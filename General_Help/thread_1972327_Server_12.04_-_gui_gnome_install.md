---
title: "Server 12.04 - gui gnome install?"
date: 2012-05-03
forum: General Help
---

### Post by Sternfan on 2012-05-03
Hi all,
I am setting up a test box - is there any way to install gnome on server 12.04?

Thanks,
Rob

---

### Post by gordintoronto on 2012-05-03
Your best bet is to install Ubuntu Desktop, which can do everything Ubuntu Server can do. Then install AMP on top of it, if you are testing web pages.

---

### Post by Sternfan on 2012-05-03
I tried that, and got Unity.  I am trying to get gnome.

Rob

---

### Post by gordintoronto on 2012-05-03
I think you can install gnome in the software manager, then at logon click the "gear" and select gnome.

---

### Post by josir on 2012-05-15
"install Ubuntu Desktop, which can do everything Ubuntu Server can do"

That's not true: Ubuntu server kernel is compiled with different options to be a server. 

The best options is install Ubuntu Server and then install ubuntu-desktop.

---

### Post by jerome1232 on 2012-05-15
Unity is a small compiz plugin on top of gnome3, to get gnome-shell as an option run the following command

```
sudo apt-get install gnome-shell
```

At your login screen click on the Ubuntu Logo near your name, select "Gnome" as your login session.

---

### Post by Cheesemill on 2012-05-15
> **josir said:**
> "install Ubuntu Desktop, which can do everything Ubuntu Server can do"

That's not true: Ubuntu server kernel is compiled with different options to be a server. 

The best options is install Ubuntu Server and then install ubuntu-desktop.

Nope.

The server kernel and desktop kernel have been merged.
All Ubuntu versions now use the same kernel, the only difference is in the chosen architecture (amd64, i386 or i386-nonpae).

---

### Post by EarlsFurniture on 2012-06-04
> **Cheesemill said:**
> Nope.

The server kernel and desktop kernel have been merged.
All Ubuntu versions now use the same kernel, the only difference is in the chosen architecture (amd64, i386 or i386-nonpae).

 My understanding was this was only for 32 bit.  There used to be a 32bit kernel, 32bit pae kernel and a 32bit server kernel.  The pae and server kernel for 32bit have been merged.  It is my understanding that 64bit generic and 64bit server are not the same.  This is shown by trying to install linux-server and linux-image-server on a 32 bit system.  You will get generic-pae instead.  However, if you install linux-server and linux-image-server on a 64bit system, you will get it, and it is NOT "generic" but rather "server."  There doesn't seem to be much point to keeping separate server kernels if they have in fact identical. (but this isn't the case for 32bit as noted)  

update - seems I was mistaken: 

"The amd64 -generic and -server kernel flavors have been merged into a single -generic kernel flavor for Ubuntu 12.04. Given the few differences that existed between the two flavors, it only made sense to merge the two and reduce the overall maintenance burden over the life of this LTS release."

 from: [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by EarlsFurniture on 2012-06-04
> **jerome1232 said:**
> Unity is a small compiz plugin on top of gnome3, to get gnome-shell as an option run the following command

```
sudo apt-get install gnome-shell
```At your login screen click on the Ubuntu Logo near your name, select &quot;Gnome&quot; as your login session.

 If the OP or anyone else gets this to work please post how you did it.  I've tried it several times both from official repos and the gnome3-team ppa, and all I get is a classic gnome session.(with its ugly 1995 icon theme)  I can't seem to get the modern gnome3 with gnome-shell.

---

### Post by cortman on 2012-06-04
> **EarlsFurniture said:**
> If the OP or anyone else gets this to work please post how you did it.  I've tried it several times both from official repos and the gnome3-team ppa, and all I get is a classic gnome session.(with its ugly 1995 icon theme)  I can't seem to get the modern gnome3 with gnome-shell.

In that case it could be that your graphics hardware/driver isn't up to spec. Make sure when you log in that you choose "Gnome" not "Gnome Classic".

---

### Post by EarlsFurniture on 2012-06-04
> **cortman said:**
> In that case it could be that your graphics hardware/driver isn't up to spec. Make sure when you log in that you choose &quot;Gnome&quot; not &quot;Gnome Classic&quot;.

 Did that.  I'm doing this in the current vBox.  I've had issues with that before with VMWare Player not reporting true video capabilities, but vBox seems to install Unity3D just fine, so I'm stumped as to why I get this fallback or classic session only with vanilla gnome.  Also, upon install, it changed grub and now the os thinks it is debian. (or at least is now branded that way) Very odd...

---

### Post by NLem on 2012-06-05
> **Sternfan said:**
> Hi all,
I am setting up a test box - is there any way to install gnome on server 12.04?


I have been using "sudo apt-get install gnome-panel".

---

