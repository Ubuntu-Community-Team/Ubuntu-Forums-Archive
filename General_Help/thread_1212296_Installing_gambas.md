---
title: "Installing gambas"
date: 2009-07-13
forum: General Help
---

### Post by nsblenin on 2009-07-13
Please How can i install gambas. I tried this:



il@Nailo:~/trunk$ ls
acinclude.m4        gb.compress.zlib  gb.net        INSTALL
app                 gb.corba          gb.net.curl   install-sh
AUTHORS             gb.crypt          gb.net.smtp   ltmain.sh
ChangeLog           gb.db.firebird    gb.opengl     main
comp                gb.db.mysql       gb.pcre       Makefile.am
component.am        gb.db.odbc        gb.pdf        missing
config.guess        gb.db.postgresql  gb.qt         NEWS
config.sub          gb.db.sqlite2     gb.qt4        README
configure.ac        gb.db.sqlite3     gb.qt.kde     README.svn-commit
COPYING             gb.desktop        gb.sdl        reconf
depcomp             gb.gtk            gb.sdl.sound  reconf-all
examples            gb.gtk.svg        gb.v4l        TEMPLATE
gb.cairo            gb.image          gb.xml        TODO
gb.compress.bzlib2  gb.image.io       help
nil@Nailo:~/trunk$ 
il@Nailo:~/trunk$ 
nil@Nailo:~/trunk$ ./configure
bash: ./configure: No existe el fichero ó directorio
nil@Nailo:~/trunk$ configure
bash: configure: orden no encontrada
nil@Nailo:~/trunk$ reconf
bash: reconf: orden no encontrada
nil@Nailo:~/trunk$ reconf-all
bash: reconf-all: orden no encontrada
nil@Nailo:~/trunk$ sudo reconf
sudo: reconf: command not found
nil@Nailo:~/trunk$ install-sh
bash: install-sh: orden no encontrada
nil@Nailo:~/trunk$ decomp
bash: decomp: orden no encontrada
nil@Nailo:~/trunk$ depcomp
bash: depcomp: orden no encontrada
nil@Nailo:~/trunk$ make
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
nil@Nailo:~/trunk$ 



In INSTALL file tells to write ./configure then make then make install but this doesn't function.
What can i do?

---

### Post by GCoffee on 2009-07-13
run:

```
joebloggs@dellLap1:~$ sudo apt-get install gambas 
```

---

### Post by nsblenin on 2009-07-13
> **GCoffee said:**
> run:

```
joebloggs@dellLap1:~$ sudo apt-get install gambas 
```

nil@Nailo:~$ sudo apt-get install gambas
[sudo] password for nil: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete gambas
nil@Nailo:~$ 

It says that it couldn't find gambas packet

---

### Post by nsblenin on 2009-07-13
i installed gambas but when I try to install slcreator it says:

Error: Dependency is not satisfiable: gambas-runtime

---

### Post by Crafty Kisses on 2009-07-13
Just run:
```
sudo apt-get install gambas2
```

---

### Post by openbox1 on 2009-07-21
How about i want the older version of gambas 1.0.15. how i suppose to do that? 

> 
openbox@openbox-laptop:~$ sudo apt-get install gambas
[sudo] password for openbox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gambas
openbox@openbox-laptop:~$ 


---

