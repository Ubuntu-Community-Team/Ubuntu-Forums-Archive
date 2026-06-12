---
title: "Boxee hacked for 11.04"
date: 2011-05-01
forum: General Help
---

### Post by ki4jgt on 2011-05-01
Have 11.04 Boxee needs

> Dependency is not satisfiable: libxmlrpc-c3

in Ubuntu 11.04 libxmlrpc-c3 was changed to libxmlrpc-c3-0

I did the following to boxee.deb:

[LIST=1]
[*]dpkg-deb -x boxee.deb tmpdir
[*]dpkg-deb --control boxee.deb tmpdir/DEBIAN
[*]nano tmpdir/DEBIAN/control
[*]I removed libxmlrpc-c3 and changed it to libxmlrpc-c3-0
[*]dpkg -b tmpdir boxee-hacked.deb
[/LIST]

After this, Ubuntu said I had a package which didn't meet quality standards. I clicked install anyway, but it didn't install. Anyone know how to do this successfully?

---

### Post by marhis on 2011-05-02
> **ki4jgt said:**
> 
After this, Ubuntu said I had a package which didn't meet quality standards. I clicked install anyway, but it didn't install. Anyone know how to do this successfully?

All the packages who doesn't meet quality standards (for me it was chrome.deb when I tried to install it on natty alpha) can be installed with gdebi (you can get it with "sudo apt-get install gdebi") which used to be default debian packade installer untill 10.04
It works a lot faster then Software Center for package installation!

p.s. I installed boxee without problems.

---

### Post by ki4jgt on 2011-05-03
> **marhis said:**
> All the packages who doesn't meet quality standards (for me it was chrome.deb when I tried to install it on natty alpha) can be installed with gdebi (you can get it with "sudo apt-get install gdebi") which used to be default debian packade installer untill 10.04
It works a lot faster then Software Center for package installation!

p.s. I installed boxee without problems.

Did you do it on a fresh install of Ubuntu of was it just upgraded?

---

### Post by marhis on 2011-05-04
> **ki4jgt said:**
> Did you do it on a fresh install of Ubuntu of was it just upgraded?

It was done on freshly installed 11.04 (as I have /Home on separate partition I always make fresh installation but almost all configuration files and settings stays like previously)

---

### Post by thedrklion on 2011-05-04
New to Linux, can someone please further outline the steps needed to mod the boxee.deb?
I have never used dpkg-deb to build a package,,,nor do i know how to remove  libxmlrpc-c3 and changed it to libxmlrpc-c3-0

I am basically asking to dumb down the following:

[LIST=1]
[*]dpkg-deb -x boxee.deb tmpdir
[*]dpkg-deb --control boxee.deb tmpdir/DEBIAN
[*]nano tmpdir/DEBIAN/control
[*]I removed libxmlrpc-c3 and changed it to libxmlrpc-c3-0
[*]dpkg -b tmpdir boxee-hacked.deb
[/LIST]

I have gdebi installed, however.
Else, i will have to downgrade to ubuntu 10.10 netbook.

---

### Post by ki4jgt on 2011-05-04
> **thedrklion said:**
> New to Linux, can someone please further outline the steps needed to mod the boxee.deb?
I have never used dpkg-deb to build a package,,,nor do i know how to remove  libxmlrpc-c3 and changed it to libxmlrpc-c3-0

I am basically asking to dumb down the following:

[LIST=1]
[*]dpkg-deb -x boxee.deb tmpdir
[*]dpkg-deb --control boxee.deb tmpdir/DEBIAN
[*]nano tmpdir/DEBIAN/control
[*]I removed libxmlrpc-c3 and changed it to libxmlrpc-c3-0
[*]dpkg -b tmpdir boxee-hacked.deb
[/LIST]

I have gdebi installed, however.
Else, i will have to downgrade to ubuntu 10.10 netbook.

Open gnome-terminal and type these commands in

when you get to nano (It's a text editor and the file is one which was stored in the .deb) with the file tmpdir/DEBIAN/control you simply scroll down to dependencies section. Move the cursor to your right until you find libxmlrpc-c3 and tack a -0 on the end. Then you hit CTRL + X to exit. It will ask you if you want to save - choose yes and then it will ask you where you want to save it, leave it the way it is and hit ENTER. Then continue with dpkg -b.

***NOTE: I am not responsible for the mis/use of this information. This is merely information and does not imply I have or have not modified Boxee's software. I found this information in the Ubuntu forums and do not have a working copy of Boxee on my Linux based computer anywhere.

---

### Post by thedrklion on 2011-05-04
Upon attempting to execute the first command in terminal i get the following error
" dpkg-deb: error: failed to read archive `boxee.deb': No such file or directory "

I placed the boxee deb into the tmp folder then renamed the deb "boxee.deb", yet the error persists.

Any help would be much appreciated. Thanks.

On another note, upon viewing the deb with App Manager i noticed that i could not make changes to the control file_ and save them_ while the deb is NOT extracted but upon extracting files i noticed changes would save. Sadly, I can not install an extracted deb file (without a whole hell of alot of hassle, right?).  So, is there a GUI tool to build / compile a deb using the extracted files of a deb? A compiler of sorts. So I can extract, the edit control file, recompile it so i can then install it with the changes I make? 

P.S Would the extracted files for a deb be considered the source of the deb?

Thanks again.

---

### Post by thedrklion on 2011-05-05
Issue resolved, the boxee.deb needed to be placed into home/USERNAME
Thank you everyone. Boxee up and running.

---

### Post by Munk3y on 2011-05-06
Hey, now that you have Boxee up and running on it, does it actually work? As in plays all regular video/audio and doesn't crash after 30 seconds, etc? I'm just curious because my HTPC is still on 10.10 and there's several reasons I'd like to upgrade to 11.04 now. I've been searching around and see nothing but complaints about problems regarding Boxee, so I've been holding off. Info would be appreciated, thanks!

---

### Post by Apewall on 2011-05-07
> **Munk3y said:**
> Hey, now that you have Boxee up and running on it, does it actually work? As in plays all regular video/audio and doesn't crash after 30 seconds, etc? I'm just curious because my HTPC is still on 10.10 and there's several reasons I'd like to upgrade to 11.04 now. I've been searching around and see nothing but complaints about problems regarding Boxee, so I've been holding off. Info would be appreciated, thanks!

A few things.  But nothing absolutely terrible.

- Unity/compiz seems to cause playback issues with Boxee
- Lost Navigation/startup sounds in 64bit(have not tested for 32)
- Problems with the scraper not adding information to to the library


I like how boxee looks and feels, and prefer the way it handles its library greatly over xbmc.  They said they would be making a natty release both on the boxee official twitter and the blog, but no more information has been given and that was near two weeks ago.

---

### Post by Munk3y on 2011-05-08
Well, I installed Ubuntu 11.04 fresh. I followed the instructions in this thread to get Boxee installed. I also logged into "Classic (No Effects)" at the GDM. Boxee is working great on it with zero problems for me. Video playback was slightly choppy (Not quite, hard to describe) until I turned on Sync to VBlank in the nVidia Settings Manager.

---

### Post by turtleracer on 2011-05-09
deleted

---

### Post by tetobear on 2011-05-14
Hello thank you for the tip...
I have problems to repack the .deb...
i am stuck!

teto@tetolaptop:/media/Data/Downloads/Boxee$ dpkg -b tmpdir boxee-hacked.deb
dpkg-deb: error: control directory has bad permissions 750 (must be >=0755 and <=0775)
I tried to use chmod... (sudo chmod -cR tmpdir)but not luck...
still that error on repacking...

---

### Post by tetobear on 2011-05-14
never mind
got it
had to do it on /home folder...
dont know why... but i got it

---

### Post by cmallam on 2011-07-11
(kubuntu)

from boxee.log

FATAL: CApplication::Create: Unable to init rendering system

---

