---
title: "problems using the terminal"
date: 2009-08-22
forum: General Help
---

### Post by rastro123 on 2009-08-22
Hi, I wonder if anyone could be so kind as to tell me what I'm doing wrong in the terminal. I'm trying to install some wireless drivers, but I'm having big trouble doing it. Everytime I tell the terminal to change directory, it says that it does not exist. - I can go to Escritorio, for example and then try cd src and it tell me it doesnt exist. I try to untar the file- it doesnt exist. I put some examples of my terminal here. Any help pls?
boo@boo-laptop:~$ cd Escritorio
boo@boo-laptop:~/Escritorio$ ls
4gb-memory-overclocking,2024_files
4gb-memory-overclocking,2024.html
answer for reed 9~
backtrack4-guide-tutorial.pdf
carpeta sin título
carpeta sin título 2
carpeta sin título 3
cmdline.html
command to start wireless in bt4
components4pc
dif_linux_distros_at_same_time.html
Display list of modules or device drivers in the Linux Kernel
download_website
Ep.%2016%20-%20Wireless%20Hacking%20-%20Cracking%20WPA.flv
Ep.%2020%20-%20Ettercap.flv
Ep.%2024%20-%20Bypass%20Hotspot%27s%20Access%20Controls-1.flv
Find out Ethernet card driver name
for_the_shop
fotos_memory_card1
Hacking Wireless with Ubuntu.flv
HCL:Wireless.html
How to get Atheros AR5007EG or AR242x wireless cards (may be other models) working in Ubuntu 8_10 (Intrepid Ibex)**Ubuntu Geek_archivos
 How to load a kernel module automatically at boot time
IEFD%20Ep.%202%20-%20Wireless%20Hacking%20-%20Cracking%20WEP.flv
Installation instructions for the rt73 Module
intel front panel conectivity design.pdf
linux_commands
linux_wireless_card_things
man wget~
my_wireless_driver_info
my_wireless_driver_info~
Quad4's
RaLink RT73 USB Enhanced Driver info
rt73-k2wrlz-2.0.1
rt73-k2wrlz-2.0.1.tar.bz2
rt73-k2wrlz-3.0.2.tar.bz2
rt73-k2wrlz-3.0.3.tar.bz2
rt73-k2wrlz-3.0.3.tar.bz2 
some_wireless commands
some_wireless_commands
stop process in terminal.html
to google
to google~
torrents
Typical software administration commands
Ubuntu:Jaunty_files
Ubuntu:Jaunty.html
ubuntupocketguide-v1-1.pdf
Ubuntu-Tweak - Tips Tricks - Ubuntu 9.04 with Compiz.flv
ultimate_graphic_guide
wep_no_client_pics
boo@boo-laptop:~/Escritorio$ cd Documentos
bash: cd: Documentos: No existe el fichero ó directorio
boo@boo-laptop:~/Escritorio$ cd Música
bash: cd: Música: No existe el fichero ó directorio
boo@boo-laptop:~/Escritorio$ cd src
bash: cd: src: No existe el fichero ó directorio
boo@boo-laptop:~/Escritorio$

---

### Post by michy99 on 2009-08-22
You are trying to cd to directories that are not in the directory that you are currently in. You cd to Escritorio, so now you are in ~/Escritorio. You want to cd to Documentos, but it is not in Escritorio, it is in ~ (your home directory, also known as /home/boo). To change to Documentos, enter```
cd ~/Documentos
```or```
cd /home/boo/Documentos
```or```
cd ../Documentos
```In the last example, .. equals the parent directory of the current directory.

---

### Post by tgeer43 on 2009-08-22
It looks to me like you are trying to cd into directories contained in your home folder but you are currently in the Escritorio directory.

You'll need to either cd back to your home directory first:
```
cd ~/
```Or specify the full path in your cd command:
```
cd ~/Documentos
```tgeer

---

### Post by rastro123 on 2009-08-22
many thanks

---

