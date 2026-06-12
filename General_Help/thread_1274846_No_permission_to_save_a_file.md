---
title: "No permission to save a file"
date: 2009-09-25
forum: General Help
---

### Post by kr6218 on 2009-09-25
I just recently put Ubuntu onto my computer as the only OS. The only problem I am having is that sound will not play out of my speakers. I found out that I can do the following to fix the problem:

Edit the file :
 /etc/modprobe.d/alsa-base
 To include this line at the end :
 options snd-hda-intel model=vaio


(As taken from: [http://michael.flanagan.ie/blog/index.php/19/headphone-fix-ubuntu-sony-vaio/](http://michael.flanagan.ie/blog/index.php/19/headphone-fix-ubuntu-sony-vaio/)

I had no problem accessing the file and typing in that line, however, when I try to save it I get the following error:

Could not save the file /etc/modprobe.d/alsa-base.conf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

How can I "get permission" to save this file? I would love to be able to use my headphones on my computer. Thanks to all who can help!

---

### Post by mcduck on 2009-09-25
You need to edit the file with root permissions, normal user's only have write access to their own home directories.

Open a terminal and run "gksudo gedit /etc/modprobe.d/alsa-base" to open the file for editing in gedit as root.

You should probably read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by nikhilk on 2009-09-25
> **kr6218 said:**
> I had no problem accessing the file and typing in that line, however, when I try to save it I get the following error:

Could not save the file /etc/modprobe.d/alsa-base.conf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

You probably need to edit that file as root. Open the file using
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
make the edit and then save it.

---

### Post by kr6218 on 2009-09-25
Thanks so much for the help. Once I tried it using that type of access it worked like a champ :)

---

### Post by Geweten on 2010-01-08
Hello still anyone there ?

If so, these permissions are really anoying...

Sadly enough I gave my user all permissions and he still cannot change files... ?!

At the moment I each time launch a "root-browser" code:

gksudo nautilus

Is there a way around ?

---

