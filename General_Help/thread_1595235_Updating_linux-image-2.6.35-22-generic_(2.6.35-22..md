---
title: "Updating linux-image-2.6.35-22-generic (2.6.35-22.34)"
date: 2010-10-13
forum: General Help
---

### Post by otoris on 2010-10-13
I've looked everywhere for help with this error in the console whenever I upgrade packages. This doesn't affect anything I do in Ubuntu, but it is just a little annoying. 

Here is what I get when I execute sudo apt-get upgrade
```
Setting up linux-image-2.6.35-22-generic (2.6.35-22.34) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Failed to symbolic-link boot/initrd.img-2.6.35-22-generic to initrd.img: File exists
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I think there was a simple command I could run to fix this, but I have a terrible memory. Any hints?

Thanks!

---

### Post by dino99 on 2010-10-13
try:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure linux-image-2.6.35-22-generic

---

### Post by gtuxyco on 2010-10-13
```
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       nvidia-current (260.19.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error al procesar linux-image-2.6.35-22-generic (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 2
Se encontraron errores al procesar:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Ok, this is my problem seems to be the same as yours ...
And seeing the full log you can see that the error which refers to the grub
```
/etc/default/grub: 9: splash: not found
```
The problem is that you have not installed either the patch for the pymount look good with nvidia 
Escuchar
Leer fonéticamente
You can follow the detailed how to solve the problem
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml]("LINK")
after that you can run
sudo apt-get install -f

---

### Post by forcecore on 2010-10-13
same here even reconfigure do not work and autoremove killed Ubuntu, something is really wrong with update currently.

---

### Post by gyussz on 2010-10-13
Ran into the same error code today, and System -> Administration -> Computer Janitor solved the problem for me. Give it a try :)

---

### Post by otoris on 2010-10-13
Alright. Tried all the command dino99 suggested, same error. Gave the Computer Janitor a try already, but tried again to be extra sure. It just has a lot of libre office debs that it can't remove because another package manager is in use... (When it isn't in use...) Gtuxyco, I followed that guide and tried apt-get install -f, same message...

So far no answer. :( Thanks for the suggestions though.

---

### Post by songochain on 2010-10-19
Hi, same problem here:

[quote]

&#9608;&#9608; link @ ~
&#9608;&#9608; 23:21:09 $ sudo apt-get -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de esta operación.
Configurando linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Failed to symbolic-link boot/initrd.img-2.6.35-22-generic to initrd.img: El archivo ya existe
dpkg: error al procesar linux-image-2.6.35-22-generic (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 17
Se encontraron errores al procesar:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/quote ]

BR.

---

### Post by kingv on 2010-10-20
Same here!


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.34 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by kingv on 2010-10-20
[http://ubuntuforums.org/showthread.php?p=10001273#post10001273](http://ubuntuforums.org/showthread.php?p=10001273#post10001273)

---

### Post by songochain on 2010-10-20
> **kingv said:**
> [http://ubuntuforums.org/showthread.php?p=10001273#post10001273](http://ubuntuforums.org/showthread.php?p=10001273#post10001273)
Thank you but that didn't fix the problem :confused:

---

### Post by otoris on 2010-10-25
```
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Failed to symbolic-link boot/initrd.img-2.6.35-22-generic to initrd.img: File exists
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Still getting the above error. Tried the link posted above... Didn't work for me either. Any new suggestions?

---

### Post by otoris on 2010-10-29
Ugh, I've tried everything I can think of and everything I've found, maybe reinstalling is the fix.

---

### Post by CoolJohnB on 2010-10-29
Try Ubuntu Teak a nice little utility that can really help with this.

---

