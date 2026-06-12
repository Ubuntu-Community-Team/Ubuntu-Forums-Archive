---
title: "Need some assistance please"
date: 2006-05-23
forum: General Help
---

### Post by sabredog on 2006-05-23
Tried to install a .deb file tonight and this error cropped up. Can someone help with this? I need to install a dependency but have yet to find it.

```
madmike@ubuntu:~$ sudo dpkg -i /home/madmike/mailwasher_1.1.2_i386_kubuntu.deb
Password:
Selecting previously deselected package mailwasher.
(Reading database ... 133735 files and directories currently installed.)
Unpacking mailwasher (from .../mailwasher_1.1.2_i386_kubuntu.deb) ...
dpkg: dependency problems prevent configuration of mailwasher:
 mailwasher depends on libqt3c102-mt (>= 3:3.3.3); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing mailwasher (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mailwasher
madmike@ubuntu:~$ sudo dpkg -i /home/madmike/mailwasher_1.1.2_i386_kubuntu.deb
dpkg: status database area is locked by another process
madmike@ubuntu:~$

```

cheers and thanks

---

### Post by frodon on 2006-05-23
You have to install the libqt3c102-mt library, it's a needed dependency. Once it's done retry.

---

### Post by sabredog on 2006-05-23
Hmm, I just found that library in Synaptic and it has been installed. Is it becuase the software I am trying to install needs Kubuntu. I have installed the Kubuntu KDE desktop via apt get and am trying to install Mailwasher under the Gnome desktop. I would have thought the dependency links were the same for both DT's?

---

### Post by frodon on 2006-05-23
They are, and you don't need to install KDE, you only needs some qt libraries to run KDE applications under GNOME.
I guess that libqt3c102-mt is not installed after a default KDE install.

---

### Post by sabredog on 2006-05-23
Hmmm

That particular library is not installed after all and I cannot seem to find it via synaptic.

Can anyone help me find and install this please?

cheers and thanks.

---

### Post by frodon on 2006-05-23
You can dowload the .deb here, but i might have some dependencies you don't have on your computer : [http://packages.debian.org/stable/libs/libqt3c102-mt](http://packages.debian.org/stable/libs/libqt3c102-mt)
It's why it's always a little more difficult to install softwares outside the repositories.

---

### Post by az on 2006-05-23
Just run

sudo apt-get -f install

and that will get any dependencies, if they are available.  Dpkg doesn't do that for you, which is why the "a" in apt stands for "advanced".

---

### Post by sabredog on 2006-05-23
[QUOTE=frodon]You can dowload the .deb here, but i might have some dependencies you don't have on your computer : [http://packages.debian.org/stable/libs/libqt3c102-mt](http://packages.debian.org/stable/libs/libqt3c102-mt)
It's why it's always a little more difficult to install softwares outside the repositories.[/QUOTE]

I DL'ed the deb and came up with an error about conflicting with an installed library.

Got me beat this one, normally I get a resolution after a bit of work.

---

### Post by sabredog on 2006-05-23
[QUOTE=azz]Just run

sudo apt-get -f install

and that will get any dependencies, if they are available.  Dpkg doesn't do that for you, which is why the "a" in apt stands for "advanced".[/QUOTE]

Thanks for that!

No joy either but I will keep trying :)

---

### Post by az on 2006-05-23
[QUOTE=sabredog]Thanks for that!

No joy either but I will keep trying :)[/QUOTE]
Do you get the same error?

---

### Post by sabredog on 2006-05-23
[QUOTE=azz]Do you get the same error?[/QUOTE]

Azz

Similar, but I intend to try again when I get home from work.

This is a good lesson for me, once I overcome the problem I should have a better knowledge of how dependencies work.

Cheers and thanks

---

### Post by sabredog on 2006-05-24
a no dependency error using the commandline syntax given to me, Azz...

---

### Post by az on 2006-05-24
Your package is built for debian and not Ubuntu.  Compile it from source.  You can change the name of the libqt3-mt dependencies in the debian control file.

---

### Post by sabredog on 2006-05-24
[QUOTE=azz]Your package is built for debian and not Ubuntu.  Compile it from source.  You can change the name of the libqt3-mt dependencies in the debian control file.[/QUOTE]

Firetrust has informed me that their Linux version is having issues with Kubuntu/Ubuntu. To help out they are emailing me a new beta that is supposed to fix the issue.

Which is good news as I really do not want to get involved with compiling code just yet!

Cheers and thanks

---

