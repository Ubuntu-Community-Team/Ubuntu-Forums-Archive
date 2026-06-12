---
title: "x configure error"
date: 2006-04-10
forum: General Help
---

### Post by niteshadw on 2006-04-10
I'm trying to install programs from source, but I get an error:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!


I used to get more error saying gnome lib's are missing so I've installed them, yet I get to this error and I'm not sure which lib's are needed here. I don't know which are required and which are not - I don't really want to have my system filled with junk.

Is there also a page or something that lists what libraries, etc are required for the system to work properly - source installation to work as smooth as possible, deb packages to work...etc

Thanks

---

### Post by Sutekh on 2006-04-10
What programs are you installing?

You may need
```
sudo apt-get install kdelibs4-dev
```

---

### Post by niteshadw on 2006-04-10
[QUOTE=Sutekh]What programs are you installing?
[/QUOTE]

Superkaramba and some boot editor and some others...

---

### Post by Sutekh on 2006-04-10
What sort of boot editor?

Superkaramaba is available through the Ubuntu repositories.  If you install it using **apt-get** you won't have to go through the trials of compiling (and downloading all those libraries you may never need again)

Its in the universe repository so you'll have to enable that.

If you don't know how to, read on
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo kwrite /etc/apt/sources.list
``` - This will copy the apt-get sources repository list to a backup file and then edit it.  You don't have to use kwrite to do this.

 - When the file opens you need to look for lines containing **universe** and uncomment them, ie remove the # sign at the beginning.  So lines like these
```
# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe
```
become these
```
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe
```
 - Save the file and exit the editor

 - Finally refresh the repositories and install Superkaramba
```
sudo apt-get update
sudo apt-get install superkaramba
```

---

### Post by niteshadw on 2006-04-10
[QUOTE=Sutekh]What sort of boot editor?

Superkaramaba is available through the Ubuntu repositories.  If you install it using **apt-get** you won't have to go through the trials of compiling (and downloading all those libraries you may never need again)

Its in the universe repository so you'll have to enable that.

If you don't know how to, read on
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo kwrite /etc/apt/sources.list
``` - This will copy the apt-get sources repository list to a backup file and then edit it.  You don't have to use kwrite to do this.

 - When the file opens you need to look for lines containing **universe** and uncomment them, ie remove the # sign at the beginning.  So lines like these
```
# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe
```
become these
```
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe
```
 - Save the file and exit the editor

 - Finally refresh the repositories and install Superkaramba
```
sudo apt-get update
sudo apt-get install superkaramba
```[/QUOTE]

Thanks that's quite good, but I got it to work from source since apt-get did not really get the job done this time - but I did not try your repository list

---

