---
title: "Problem to install Google Picasa on Ubuntu 11.10"
date: 2011-11-16
forum: General Help
---

### Post by aafgarci on 2011-11-16
Hi there,

I am trying to install Picasa 3.0 on my desktop running Ubuntu 11.10 (64 bits). I've been using Picasa for quite a while on previous Ubuntu's versions.

I got the .deb from here: [http://picasa.google.com/linux/](http://picasa.google.com/linux/)

To install, I did
sudo dpkg -i picasa_3.0-current_amd64.deb

But there some dependencies that I don't know how to solve, since the packages are not on the repository:

ia32-libs
lib32asound2
lib32z1

It seems that is somehow related with the 64 bits version, but I have no idea how to solve this problem.

---

### Post by hoffman462 on 2011-11-22
I see this problem too; using picasa 3.0 / ubuntu 11.10
I see some posts elsewhere (google'd) to use picasa 3.8 with the windows binaries instead and they suggest installing wine.

did you find away around this?

---

### Post by alphacrucis2 on 2011-11-22
ia32-libs is in universe repo for oneiric. Do have have universe repo enabled in your software sources.

[http://packages.ubuntu.com/oneiric/ia32-libs](http://packages.ubuntu.com/oneiric/ia32-libs)

---

### Post by hoffman462 on 2011-12-12
> **alphacrucis2 said:**
> ia32-libs is in universe repo for oneiric. Do have have universe repo enabled in your software sources.

[http://packages.ubuntu.com/oneiric/ia32-libs](http://packages.ubuntu.com/oneiric/ia32-libs)

Yes, I "had" that installed - I checked to make sure.
After a while -  I just rolled my distro back to 11.04.

Sadly, I see picasa 3 is removed from googles download page.

What to do now?

---

### Post by oldtimer7777 on 2011-12-12
Try installing it from the updated PPA instead.. Here is a checklist to install what you want.  Picasa is listed about 2/3rds the way down the checklist:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

I just did it this way for a client yesturday, so I know for a fact that it is still works.

---

### Post by hoffman462 on 2011-12-14
> **oldtimer7777 said:**
> Try installing it from the updated PPA instead.. Here is a checklist to install what you want.  Picasa is listed about 2/3rds the way down the checklist:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

I just did it this way for a client yesturday, so I know for a fact that it is still works.

Thanks alot, 
this worked great on ubuntu 11.04 too

---

### Post by ac_d600 on 2011-12-15
For those who would like to try out the new version 3.9 here are instructions:

Install version 3.0 as mentioned in the above post.

From the command line:

1) **cd /opt/google/picasa/3.0/wine/drive_c/**

2) **wget [http://dl.google.com/picasa/picasa39-setup.exe](http://dl.google.com/picasa/picasa39-setup.exe)**

3) **WINEPREFIX=/opt/google/picasa/3.0/wine/ /opt/google/picasa/3.0/wine/bin/wine /opt/google/picasa/3.0/wine/drive_c/picasa39-setup.exe**

If you get any error messages along the way you may have to use **sudo**.

** This works for me, has worked since ver 3.8, this does not guarantee it will work for you **

Enjoy :P

---

