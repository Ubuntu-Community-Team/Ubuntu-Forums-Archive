---
title: "Working with .iso"
date: 2009-08-29
forum: General Help
---

### Post by rmp5s on 2009-08-29
I have another Linux distrobution (Pentoo) on my hard drive as a .iso file.  My computer (an HP Mini 1020NR netbook) doesn't have an optical drive so a .iso doesn't do me much good.  I LOVED the Ubuntu Netbook Remix and how it came as a .img file that booted from a thumb drive (I liked it so much I'm now Windows free running Ubuntu NBR, actually!)  I was wondering how to convert the .iso I have to a .img so I can boot it from my thumb drive to mess around with or if there's another way I can do this.  Any help greatly appreciated!!

---

### Post by mikewhatever on 2009-08-30
You can use unetbootin to put isos on flash memory sticks.

---

### Post by kerry_s on 2009-08-30
> **rmp5s said:**
> I have another Linux distrobution (Pentoo) on my hard drive as a .iso file.  My computer (an HP Mini 1020NR netbook) doesn't have an optical drive so a .iso doesn't do me much good.  I LOVED the Ubuntu Netbook Remix and how it came as a .img file that booted from a thumb drive (I liked it so much I'm now Windows free running Ubuntu NBR, actually!)  I was wondering how to convert the .iso I have to a .img so I can boot it from my thumb drive to mess around with or if there's another way I can do this.  Any help greatly appreciated!!

you should have usb-creator installed.
in the top point it to the iso, the bottom should be the usb flash you want to burn to.

---

### Post by rmp5s on 2009-08-30
Kerry...at first I thought you were a life saver.  I anxiously went to my "add/remove software" thing, installed the USB maker prog you mention, cranked it up and, to my dismay, I got this:

[IMG]http://www.villagephotos.com/utils/image.aspx?u=2004-5%5C721024%5CScreenshot.png.jpg[/IMG]

What does this mean?  I'm just trying to use standard, bootable ISO files...

---

### Post by kerry_s on 2009-08-30
looks like you'll have to go unetbootin then.
**sudo apt-get install --no-install-recommends unetbootin**

that will install it with out the qt crap.

i'll download that pentoo & see if the usb-creator does the same on mine, so i'll get back to you in 30 minutes.

---

### Post by rmp5s on 2009-08-30
Sounds good.  I'll try the other thing in the mean time.  Talk to you shortly.

---

### Post by kerry_s on 2009-08-30
> **rmp5s said:**
> Sounds good.  I'll try the other thing in the mean time.  Talk to you shortly.

just a couple more minutes.

---

### Post by kerry_s on 2009-08-30
alright i get the same message as you. unetbootin should work.

---

### Post by earthpigg on 2009-08-30
unetbootin is vendor neutral.

Ubuntu's usb-creator package (aka system -> admin -> USB Startup Disk Crator) is ubuntu and ubuntu-based only ---- you, or anyone else, is welcome to modify it to suit **_your_** needs, of course, but **_Ubuntu_** created it to suit **_Ubuntu's_** needs (encouraging people to explore/try different falvors of **_Ubuntu_**, such as the one in my sig).

soooo yea, unetbootin is the way to go for you.

---

### Post by rmp5s on 2009-08-30
Well...I ran unetbootin and all seemed to work fine.  Restarted the mini, booted from the USB and all I got was a black screen with "Boot error" on it.  I'm lost...

You a fellow Marine, Pigg?

---

### Post by kerry_s on 2009-08-30
> **earthpigg said:**
> unetbootin is vendor neutral.

Ubuntu's usb-creator package (aka system -> admin -> USB Startup Disk Crator) is ubuntu and ubuntu-based only ---- you, or anyone else, is welcome to modify it to suit **_your_** needs, of course, but **_Ubuntu_** created it to suit **_Ubuntu's_** needs (encouraging people to explore/try different falvors of **_Ubuntu_**, such as the one in my sig).

soooo yea, unetbootin is the way to go for you.


:lolflag: that makes since, the last time i used it was to try that "masonux" & then to put jaunty gnome back.

---

### Post by earthpigg on 2009-08-30
> **rmp5s said:**
> Well...I ran unetbootin and all seemed to work fine.  Restarted the mini, booted from the USB and all I got was a black screen with "Boot error" on it.  I'm lost...

You a fellow Marine, Pigg?

ya, fallujah '04. grunt.


as for the boot error, i'd try downloading over again. a single 1 or zero in the wrong place during the download _**or**_ the write to thumb drive -- since this is an operating system and not a movie or song or simple userland program -- can FUBAR everything.

if that didn't do it, i'd try a different distro and/or different computer just to narrow down the possible issues.


> that makes since, the last time i used it was to try that "masonux" & then to put jaunty gnome back.

glad you where able to have fun & try something new.

for the record, however, you could have just ran this to get the default ubuntu jaunty gnome desktop back:

> sudo apt-get install ubuntu-desktop

---

### Post by jrox717 on 2009-08-31
>  all I got was a black screen with "Boot error" on it. 

Could you have selected as the USB drive "sdb" instead of "sdb1" (or whatever your drive is labelled-- you need to install to the partition)

---

### Post by P4man on 2009-08-31
try wiping your usb stick clean before running unetbootin:

if =/dev/zero of=/dev/yourusbstuck

(that will wipe *everything* from the stick, so beware).

---

### Post by kerry_s on 2009-08-31
> for the record, however, you could have just ran this to get the default ubuntu jaunty gnome desktop back:

i just prefer a clean install, didn't want to have to clean up. i also did a debian install to check if they fixed it yet. using ubuntu is just a temp thing for me, i'm a debian testing user, it's just right now testing is all messed up. :lolflag:

---

### Post by rmp5s on 2009-08-31
> **earthpigg said:**
> ya, fallujah '04. grunt.

Oorah.  I'm in 29 Stumps, CA.  0651, Data Systems.  Trying to broaden my horizons with Linux.

I'll try wiping the drive, re-downloading the .iso and giving it another shot.  I'll post results.

---

### Post by earthpigg on 2009-08-31
> **rmp5s said:**
> Oorah.  I'm in 29 Stumps, CA.  0651, Data Systems.  Trying to broaden my horizons with Linux.

I'll try wiping the drive, re-downloading the .iso and giving it another shot.  I'll post results.

tell your buddies you run a distro put together by a former grunt sergeant, they will either be appalled or love it... either way, lol

---

### Post by rmp5s on 2009-08-31
> **earthpigg said:**
> tell your buddies you run a distro put together by a former grunt sergeant, they will either be appalled or love it... either way, lol

What?!  A sergeant put the Netbook Remix together or Ubuntu in general?  I didn't know this...very interesting.  Knew I liked it for some reason...lol

---

