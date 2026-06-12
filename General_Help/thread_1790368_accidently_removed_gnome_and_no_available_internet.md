---
title: "accidently removed gnome and no available internet connection"
date: 2011-06-24
forum: General Help
---

### Post by 200k on 2011-06-24
Hello all, I am quite new to linux, I have been using it the last few months. I just recently switched over to debian squeeze.

Today I was removing some applications/libraries in synaptics and accidentally removed gnome-core.

I am on a wpa2 hidden wireless network, and getting that up and running  through the terminal in recovery mode has been killer, I've searched  about half a dozen threads and nothing is seeming to work.

My wired like is pretty far away and I really do not want to keep moving my desktop all over the house.

When in the terminal i type apt-get install gnome-core it tells me I  need to download 11 new packages, of course it fails because theres no  connection. 

Is there any way I could use a command to compile a list packages I need  to reinstall gnome-core, manually retrieve them from the  ftp.us.debian.org, save them to eternal media and install them with dpkg  -i *.deb?

Thanks in advance!

---

### Post by kyphi on 2011-06-24
I am a bit unclear as to which distro you are using but would suggest that you get the files you need from your Live CD.

Go to System, Administration, Software Sources and place a tick into the box next to the entry under "Installable from CD-ROM/DVD".  To avoid confusion you can temporarily untick the boxes for "Downloadable from the Internet".

---

### Post by 200k on 2011-06-24
I am running Debian 6.0.1a squeeze x64 and I accidently removed gnome, so I have no desktop manager. I need 11 packages from the debian repo, (which I dont know which ones they are) but do know they are linked to gnome-core.

I need an offline option of getting and installing these packages, is there any way to do this?

I found this [http://packages.debian.org/squeeze/gnome-core](http://packages.debian.org/squeeze/gnome-core) but dont know where to go from there. Any ideas?

---

### Post by kyphi on 2011-06-25
If you do not have a Live Squeeze CD to hand, then you will have to download the files you need from the internet.

Squeeze has two inbuilt desktop managers.  When the Login screen appears, press Enter.  Before you type in your password, at the bottom of the screen you will be able to choose TWM which is an old windows manager but reputedly highly configurable.  It appears on the desktop on a left mouse click.

Have you considered asking this question in the Debian Help Forum?

---

