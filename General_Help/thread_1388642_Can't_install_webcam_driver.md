---
title: "Can't install webcam driver"
date: 2010-01-23
forum: General Help
---

### Post by Coco999 on 2010-01-23
I am migrating to Ubuntu and so far I find it superior. But there are a few things that are a little difficult to grasp. The installation of a webcam driver is intricate. I've downloaded the driver   ov511-1.65.tar.gz   which is applicable to my old and faithful Creative webcam. From [http://alpha.dyndns.org/ov511/install.html](http://alpha.dyndns.org/ov511/install.html)
I got the OV511 Installation Instructions:

But I fail at the first step, to become root. This is what I get:

```
coco@coco-desktop:~$ su
Contraseña: 
su: Fallo de autenticación
coco@coco-desktop:~$ 
```

I tried several times and wrote the password I use to start the session, the only one I have. It doesn't help that you are blind to the results of typing, but I tried again and again. I can't be that wrong always.

Also I can't decompress the driver. 

But I'm determined to achieve this, so please help me.

---

### Post by sisco311 on 2010-01-23
By default, the root account password is locked in Ubuntu. You can not use su or directly log in as root. 

Use 
```
sudo command
```
to run a command as root.

See
[uhelp]community/RootSudo[/uhelp]

EDIT:
For installation instruction for the driver see [uhelp]community/Ov51x[/uhelp]

---

### Post by gradinaruvasile on 2010-01-23
Try 

sudo su -

Are you sure your camera isnt working? Supported hardware drivers are in the kernel usually.
Test: press alt+f2, type gstreamer-properties go to the video tab and see if your camera is listed as a device. If yes, press the test button.

---

### Post by Coco999 on 2010-01-23
> Are you sure your camera isnt working? Supported hardware drivers are in the kernel usually.
Test: press alt+f2, type gstreamer-properties go to the video tab and see if your camera is listed as a device. If yes, press the test button.

Wonderful! My camera is working properly, at least I saw myself in the screen. But previously I had not been able to use it in a Skype session. I don't think there is any matching to do to work with Skype. I'll try it again. Thank you very much!

---

### Post by gradinaruvasile on 2010-01-23
> **Coco999 said:**
> Wonderful! My camera is working properly, at least I saw myself in the screen. But previously I had not been able to use it in a Skype session. I don't think there is any matching to do to work with Skype. I'll try it again. Thank you very much!

Ah, the Skype camera thing...

Launch it this way:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

First test it in a terminal, and if works modify the menu launcher too (the menu editor name is alacarte in terminal).

PS Get the skyp latest version - it has screen sharing and some more new features:

[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

The 8.10+ version suits all newer versions of Ubuntu. If you have installed Skype from the repositories, uninstall the skype and skype-common packages first.

---

### Post by Coco999 on 2010-01-23
> PS Get the skyp latest version - it has screen sharing and some more new features:

How do I know what is the version I have?

---

### Post by gradinaruvasile on 2010-01-23
Open skype, click on the lower left blue icon, and click "about Skype"

The latest version is 2.1.0.81.

---

### Post by Coco999 on 2010-01-23
The version I have is 2.1.0.47. I have downloaded 2.1.0.81-1_i386.deb.

But I don't know how to uninstall the former or install the later.

---

### Post by gradinaruvasile on 2010-01-23
To uninstall:

Open a terminal and type:

sudo apt-get purge skype skype-*

To install:

Double-click on the downloaded .deb

---

### Post by Coco999 on 2010-01-23
I did as directed and seemed to go smoothly. But I can't start a session with my brand new skype. It tells me that there may be some other instance running. I checked and to the best of my knowledge there is none.

But I found a difficulty when doing the uninstall. I could not remove the parts I underlined. I got this. Since you are in Romania you'll probably manage some Spanish.

```
coco@coco-desktop:~$ sudo apt-get purge skype skype-*
[sudo] password for coco: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Nota, seleccionando skype para la expresión regular 'skype-*'
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  _linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic_
Utilice «apt-get autoremove» para eliminarlos.
Los siguientes paquetes se ELIMINARÁN:
  skype*
0 actualizados, 0 se instalarán, 1 para eliminar y 0 no actualizados.
Se liberarán 25,7MB después de esta operación.
¿Desea continuar [S/n]? s
(Leyendo la base de datos ...  00%
181060 ficheros y directorios instalados actualmente.)
Desinstalando skype ...
Purgando ficheros de configuración de skype ...
Procesando disparadores para desktop-file-utils ...
coco@coco-desktop:~$ apt-get autoremove
E: No se pudo abrir el fichero de bloqueo '/var/lib/dpkg/lock' - open (13: Permiso denegado)
E: Imposible bloquear el directorio de administración (/var/lib/dpkg/), ¿es superusuario?
coco@coco-desktop:~$ 
```

Perhaps it is necessary to restart the computer, which I have not done yet.

---

### Post by jaezcurra on 2010-01-23
Hi (Hola), just add "sudo" at the beginning of "apt-get autoremove".

"apt-get ... " always should be preceded with "sudo".

Suerte.

---

### Post by gradinaruvasile on 2010-01-23
> **Coco999 said:**
>  Since you are in Romania you'll probably manage some Spanish.

Ummm... I dont know where you get that from.

Anyway, the problem here is that you should have issue the autoremove command with sudo. Installing/removing packages needs administrative (root) permissions. So:

```
sudo apt-get autoremove
```

Is the correct way.

Those packages anyway are not related to Skype - its the older kernel.

---

### Post by Coco999 on 2010-01-23
Para jaezcurra, muchas gracias. Funcionó bien ese borrado, pero Skype sigue sin arrancar. Suerte para tí.

To gradinaruvasile, thank you for your help. Since we both speak languages that come from Latin, maybe there is some common ground. I've not studied Brazilian and yet understand a bit.

I removed those files using sudo but Skype still refuses to start a new session. Perhaps it is necessary to restart the computer. I don't know.

---

### Post by gradinaruvasile on 2010-01-23
New session? Is by any chance running already?

Opena terminal and type:

killall -9 skype

then try running skype from the same prompt.

No restarting required. Only in few cases its *really* required to restart in Linux - such as kernel updates.

---

### Post by Coco999 on 2010-01-23
This did the trick. There was evidently something running unknown to me.

Thank you!!!

---

