---
title: "restor softwares to ubuntu"
date: 2011-12-02
forum: General Help
---

### Post by shubham1 on 2011-12-02
i have jsut wiped my ubuntu 11.104 and replace it with ubuntu 11.10 a complete remove with all partions deleted i have my softwares kept with me how to restore them also in smart way suppose a apllication is preinstalled so do not install that and also update them actually my brother has already done it so i think it can be done software center was used to do that

---

### Post by Mark Phelps on 2011-12-02
Don't know what you mean by "softwares kept with me".

If you saved off the .deb files you originally used to install the apps, then you can copy them to your current install and install them again by double-clicking them.

However ... you need to be aware that new Ubuntu versions often come with new versions of the apps in the repositories.  You should install Synaptic and check the versions of your saved apps to see if there is a newer version in 11.10 -- before reinstalling the older version.

---

### Post by shubham1 on 2011-12-02
> **Mark Phelps said:**
> Don't know what you mean by "softwares kept with me".

If you saved off the .deb files you originally used to install the apps, then you can copy them to your current install and install them again by double-clicking them.

However ... you need to be aware that new Ubuntu versions often come with new versions of the apps in the repositories.  You should install Synaptic and check the versions of your saved apps to see if there is a newer version in 11.10 -- before reinstalling the older version.
yes i know what is the meaning "software kept with me"
i have copied the deb files will copying the files
when i open any package it says in valid architcture amd 64
let me try copying also how to know which deb is of which pacakage

---

### Post by xtremesupremacy3 on 2011-12-02
Ok the errors you are encountering about the invalid architecture, is because you most likely copied amd64 versions of the deb files whilst you have a 32 bit Ubuntu installed, they are not compatible, this means you would need the 32 bit versions of the debian files.

btw, there is a better way to do this, and saves a lot of space.

first create a folder called backup (i recommend in Dropbox or Ubuntu One)

then in a terminal run the following command (im going to assume you have a backup folder inside dropbox):

```
dpkg --get-selections > ~/Dropbox/backup/mybackuplist

```

this will leave a small text file named 'mybackuplist' inside your backup folder.
Then if you need to format or whatever and want your apps back, just run this in the terminal after you installed Ubuntu again (and dropbox):

```
dpkg --set-selections < ~/Dropbox/backup/mybackuplist && gksu apt-get install dselect-upgrade
```

And that should then begin downloading and installing those applications

---

### Post by shubham1 on 2011-12-03
> **xtremesupremacy3 said:**
> Ok the errors you are encountering about the invalid architecture, is because you most likely copied amd64 versions of the deb files whilst you have a 32 bit Ubuntu installed, they are not compatible, this means you would need the 32 bit versions of the debian files.

btw, there is a better way to do this, and saves a lot of space.

first create a folder called backup (i recommend in Dropbox or Ubuntu One)

then in a terminal run the following command (im going to assume you have a backup folder inside dropbox):

```
dpkg --get-selections > ~/Dropbox/backup/mybackuplist

```

this will leave a small text file named 'mybackuplist' inside your backup folder.
Then if you need to format or whatever and want your apps back, just run this in the terminal after you installed Ubuntu again (and dropbox):

```
dpkg --set-selections < ~/Dropbox/backup/mybackuplist && gksu apt-get install dselect-upgrade
```

And that should then begin downloading and installing those applications
this will install them again or use those pacakages

---

### Post by shubham1 on 2011-12-03
> **shubham1 said:**
> this will install them again or use those pacakages
dpkg: error: operation requires read/write access to dpkg status area

---

### Post by Lars Noodén on 2011-12-03
> **shubham1 said:**
> dpkg: error: operation requires read/write access to dpkg status area

Try it again with sudo.  It needs root access:

```

**sudo** dpkg --set-selections < ~/Dropbox/backup/mybackuplist && gksu apt-get install dselect-upgrade

```

---

### Post by shubham1 on 2011-12-03
> **Lars Noodén said:**
> Try it again with sudo.  It needs root access:

```

**sudo** dpkg --set-selections < ~/Dropbox/backup/mybackuplist && gksu apt-get install dselect-upgrade

```
(gksu:6416): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:6416): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:6416): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:6416): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Reading package lists... Done
Building dependency tree       
Reading state information... Done

---

### Post by xtremesupremacy3 on 2011-12-03
Please note that the example I gave above only works if you had backed up the list BEFORE the computer had to be wiped clean.
If you create a list and then restore, it will already have all those files so nothing will happen. It's more an idea of what to do for next time you have to restore

And the errors are to be ignored, I made a slight mistake there, the gksu can be replaced by sudo.

sudo runs a command as root for that command and ask for a password on the commandline. gksu will do the same thing except for it will ask for your password in a graphical box instead. But since you are running this off the command line, that command can just be:

sudo dpkg --set-selections < ~/Dropbox/backup/mybackuplist && **sudo** apt-get install dselect-upgrade

that should also get rid of the warnings

---

### Post by shubham1 on 2011-12-04
> **xtremesupremacy3 said:**
> Please note that the example I gave above only works if you had backed up the list BEFORE the computer had to be wiped clean.
If you create a list and then restore, it will already have all those files so nothing will happen. It's more an idea of what to do for next time you have to restore

And the errors are to be ignored, I made a slight mistake there, the gksu can be replaced by sudo.

sudo runs a command as root for that command and ask for a password on the commandline. gksu will do the same thing except for it will ask for your password in a graphical box instead. But since you are running this off the command line, that command can just be:

sudo dpkg --set-selections < ~/Dropbox/backup/mybackuplist && **sudo** apt-get install dselect-upgrade

that should also get rid of the warnings
i have another idea instead of installing these again i will wait for final relese of 12.04
and install amd 64 bit archetecture then copy these softwares i have to switch to 64 bit and i hope the architecture will be same so it will work also my pc has amd processor so i should fully utilise it but earlier it did not worked but this time i will try will the softwares work

---

