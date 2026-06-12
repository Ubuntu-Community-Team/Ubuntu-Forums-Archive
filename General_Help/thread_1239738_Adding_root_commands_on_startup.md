---
title: "Adding root commands on startup"
date: 2009-08-13
forum: General Help
---

### Post by nanda_justgames on 2009-08-13
Hello,
I have a virtual machine using ubuntu as guest.

I need to run these commands as root:

sudo mount.vboxsf celular /home/flm/Cell
chown -R flm /home/flm/Cell
sudo mount.vboxsf doc /home/flm/Documentos
chown -R flm /home/flm/Documentos
sudo mount.vboxsf hq /home/flm/Comics
chown -R flm /home/flm/Comics
sudo mount.vboxsf img /home/flm/Imagens
chown -R flm /home/flm/Imagens
sudo mount.vboxsf doc /home/flm/Documentos
chown -R flm /home/flm/Documentos
sudo mount.vboxsf photoshop /home/flm/Photoshop
chown -R flm /home/flm/Photoshop
sudo mount.vboxsf py /home/flm/Python
chown -R flm /home/flm/Python
sudo mount.vboxsf red /home/flm/Redes
chown -R flm /home/flm/Redes
sudo mount.vboxsf universidade /home/flm/UFRGS
chown -R flm /home/flm/UFRGS
sudo mount.vboxsf wallpaper /home/flm/Walls
chown -R flm /home/flm/Walls
sudo mount.vboxsf songs /home/flm/Músicas
chown -R flm /home/flm/Músicas

These "mount"s commands allow me to shared folder between my host and my guest and I add chown cause I want my regular user to be allow change, execute any one of these folders.
These way I`ll be able to sync these folders between guest and host.

I already made a .sh doc with these comands and put on the Session startup and I already try to but these comands in bottom of the rc.local file.

But its not working, any help, suggestion?
TKS

---

### Post by michy99 on 2009-08-13
Just a couple of obsevation.

You can leave off the sudo at the beginning of the mount commands, because the script will be run as root, anyway.

You can wait until the end and just do one chown command.```
chown -R flm /home/flm
```

As to why it isn't working, does it work if you run it from a terminal? If not, what errors do you get?

---

### Post by feffer on 2009-08-13
Another way to do this is put an entry in the /etc/rc.local file

---

### Post by tgeer43 on 2009-08-13
> **feffer said:**
> Another way to do this is put an entry in the /etc/rc.local fileHe already stated that he tried that.

If you can execute the commands in a terminal without errors then you can try the following:

Create a script and name it *whatever*.sh. Make sure the first line of the file is: #!/bin/sh and make sure it is executable.
```
chmod +x whatever.sh
```Now move the new file into /etc/init.d/
```
sudo mv /path_to_file/whatever.sh /etc/init.d/
```Now update rc.d
```
sudo update-rc.d whatever.sh defaults
```This will create symbolic links in the appropriate runlevel folders causing the script to be run at startup with root privileges.
Hopefully this will get you going. As michy99 pointed out, you can lose the sudo part of the commands and combine all of the chown commands at the end with:
```
chown -R flm /home/flm
```Run that up the flagpole and see if anyone salutes it.

tgeer

---

### Post by nanda_justgames on 2009-08-13
Tks guys...
I actually forget the #!/bin/sh line lol

Tks for the chown tip too.

I had a pretty crazy idea now to transform my vm in a data server.
But I have to learn how to bridge my vm and other stuffs too...
I am searching about it...

THANKS for the fast reply!

---

