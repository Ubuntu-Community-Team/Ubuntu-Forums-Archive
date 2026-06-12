---
title: "Can't watch youtube videos"
date: 2011-05-09
forum: General Help
---

### Post by imu96 on 2011-05-09
I CAN'T WATCH YOUTUBE VIDEOS OR DO ANYTHING ELSE REGARDING FLASH! I'VE TRIED DOING WHAT OTHER THREADS SAID BUT NOTHING WORKED!!!
how do i download and enable flash??

---

### Post by ComradeSlice on 2011-05-09
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Choose the Ubuntu APT link. Should be fine.

---

### Post by imu96 on 2011-05-09
when i clicked on download it brought me back to the same page. both pages said "to view this experience i need to have javascript enabled and the latest version of adobe flash player installed"

---

### Post by clhsharky on 2011-05-09
imu96

Since 10.04 I haven't had to do anything more than install ubuntu-restricted-extras.
Thats flash,java,codex.

Not knowing what you have done, install

Flash-Aid

From Firefox addons, or from here.
[http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)



Sharky

---

### Post by triceratops on 2011-05-09
> **imu96 said:**
> when i clicked on download it brought me back to the same page. both pages said "to view this experience i need to have javascript enabled and the latest version of adobe flash player installed"

 I could never get the apt-get version to work either.  Try downloading and unpacking the *.deb file instead.  Then install the libflashplayer.so plugin manually.

After going to the Adobe website and downloading the deb package for Flash, go to superuser and root and type the following from the download directory:

```
dpkg -i install_flash_player_10_linux.deb
```When dpkg is done unpacking, go to root and cut and paste

```
cd /usr/lib/adobe-flashplugin && ls -FAtrls | grep libflashplayer.so
```Just to make sure that you have the libflashplayer.so file somewhere on your computer.  File should light up in red text.

There are a number of places that libflashplayer.so can go on the machine.  Why not copy to each plugin directory?  (if you can spare 60 mb or so)

Copy libflashplayer.so to the following directories.  I'll batch the command (using &&) to make things easier.

```
cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/mozilla/plugins/ &&
cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/firefox/plugins/ &&
cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/firefox-3.6.15/ &&
cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/xulrunner-addons/plugins/ &&
cp /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/firefox-addons/plugins/
```Is this wasteful and redundant?  Yes, but the copies can be pruned back later if necessary.  

Don't forget to exit root.

Open up youtube and see what happens.

---

### Post by imu96 on 2011-05-10
@ triceratops.... it says that the package's archetecture i386 does not match mine amd64.... is there anyway to deal with this???

hopeful....

---

### Post by rahilm on 2011-05-10
download the .tar.gz version of the flash from the adobe site.. in it.. you will find the libflash.so file..
then copy paste it to the required directories..



(this is not how it should be done!! someone should fix this!!)

---

### Post by bullfrog55 on 2011-05-11
The APT version: lucid didnt know what to do/how to open it so I tried the .deb version and it installed and worked no problem. Only had to restrart Firefox to get it going.

---

### Post by imu96 on 2011-05-12
ummm... wat is the required directory???

---

### Post by philinux on 2011-05-12
> **imu96 said:**
> ummm... wat is the required directory???

Just install this it will do all the work for you.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by imu96 on 2011-05-12
ummmm.... not trying 2 b difficult or anything.... but... what if i want to use chromium???

---

### Post by imu96 on 2011-05-12
Thank you phil linux it worked!!!! Even in chromium!!! :D

---

### Post by philinux on 2011-05-12
> **imu96 said:**
> Thank you phil linux it worked!!!! Even in chromium!!! :D

Nice one. Credit to lovinglinux. Don't forget to mark this solved using the pull down menu Thread Tools.

---

