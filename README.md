![alt text](https://github.com/rsantomauro/obligatorio_2021_08/blob/main/Portada_README_Git.jpg)
# Obligatorio Taller de servidores Linux 2021 🎓

## Comenzando 🚀

### Introducción 📖
 
Primeramente, para cumplir con la finalidad del objetivo planteado, se implementan tres máquinas virtuales en VirtualBox con ciertas particularidades en las configuraciones de red, que serán detalladas posteriormente. 
Con el objetivo de realizar una instalación de diferentes componentes se decide utilizar Ansible como aprovisionamiento del software necesario para la instalación del stack LAMP. Se debe tener en cuenta que las dos familias de distribuciones solicitadas son RedHat y Debian, donde estos serán creados con esquema de particionamientos de LVM. 
La base de este proyecto surge de un repositorio público en GitHub brindado por los docentes de la materia donde en el sugieren una implementación del playbooks de Ansible para CentOS 7, donde se debe realizar un fork del mismo y realizar los cambios pertinentes para que su ejecución sea correcta sobre CentOS 8 y Debian. 
Para realizar el mantenimiento del código ansible se utilizó la herramienta de Microsoft Visual Studio Code con las siguientes extensiones: remote-ssh, ansible de Tomasz Maciazek, ansible lenguaje de RedHat.

### Pre-requisitos 📋

- Servidor CentOS 8 con usuario ansible sin contraseña y con permisos de superusuario.
- Servidor Ubuntu 20.04 LTS con usuario ansible sin contraseña y con permisos de superusuario.
- Servidor encargado de ejecutar los playbooks.

### Herramientas 🛠️

- Virtual Box
- Visual Studio Code
- GitHub
- Ansible
- CentOS 8
- Ubuntu
- Apache
- MySQL
- MariaDB
- Python

## Configuraciones de Playbooks

- En todos los casos se adaptó la instalación para que sea compatible con distribuciones Ubuntu 20.04 LTS.

### Roles
- common
- db
- web

#### Common
- [x] Se actualiza tanto en CentOS como en Ubuntu el paquete ntp por chrony ya que el mismo [quedó obsoleto](https://linuxhint.com/configure-ntp-centos-8/).
- [x] Se corrigen las dependencias.
- [x] Se asignan permisos para contemplar el [Issue 71200](https://github.com/ansible/ansible/issues/71200)
- [x] Se asigna la variable con el host de proyecto [ntp.org](https://www.pool.ntp.org/zone/uy) de Uruguay.
- [x] Se corrige el [código obsoleto](https://www.programmersought.com/article/4888525503/) pasando la iteración a variables.

#### DB
- [x] Se corrigen las dependencias.
- [X] Se actualizan las librerías.
- [x] Se asignan permisos para contemplar el [Issue 71200](https://github.com/ansible/ansible/issues/71200)
- [x] Se debe especificar el usuario y grupo del archivo de configuración.
- [x] Se corrige el [código obsoleto](https://www.programmersought.com/article/4888525503/) pasando la iteración a variables.
- [x] Se actualiza el estado de installed a present ya que el mismo no existe.
- [x] Se corrige la configuración de SELinux.
- [x] Se implementa ufw para distribuciones Debian.
- [x] Se realizan conexiones a mariadb mediante el socket.

#### WEB
- [x] Se utilizan los paquetes correspondientes de cada distribución.
- [x] Se instalan los paquetes de git para Debian.
- [x] Se implementa ufw para distribuciones Debian.
- [x] Se asignan permisos para contemplar el [Issue 71200](https://github.com/ansible/ansible/issues/71200)
- [x] Se corrige el [código obsoleto](https://www.programmersought.com/article/4888525503/) pasando la iteración a variables.


## Ejecutando las pruebas ⚙️

```
ansible-playbook -i inventario site.yml
```

![image](https://user-images.githubusercontent.com/88011897/128646689-cd8605fd-de36-4bee-b9e7-f61f8e6e14f5.png)

Validamos que podamos entrar a la url 

![image](https://user-images.githubusercontent.com/88011897/128646692-ff8b1302-6607-4686-af6a-1afdd9d62649.png)

## Licencia 📄

Este proyecto está bajo la Licencia GPLv3 - mira el archivo [LICENSE.md](https://github.com/rsantomauro/obligatorio_2021_08/blob/main/lamp/LICENSE.md) para detalles

## Referencias Bibliograficas 📚

- https://guides.github.com/features/mastering-markdown/
- https://gist.github.com/Villanuevand/6386899f70346d4580c723232524d35a
- Ejemplo de ansible.cfg https://github.com/ansible/ansible/blob/devel/examples/ansible.cfg
- Ejemplo de playbooks https://docs.ansible.com/ansible/latest/user_guide/playbooks_conditionals.html
- Ejemplo de ansible facts https://docs.ansible.com/ansible/latest/user_guide/playbooks_vars_facts.html


## Autores ✒️

- **Rodrigo Santomuro** - *Trabajo y documentacion* - [@rsantomauro](https://github.com/rsantomauro)
- **Melissa Rossi** - *Trabajo y documentación* - [@sudakiita](https://github.com/sudakiita)
- **Virginia Grajales** - *Trabajo y documentación* - [@vikygj](https://github.com/vikygj)