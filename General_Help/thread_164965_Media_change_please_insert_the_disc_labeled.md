---
title: "Media change: please insert the disc labeled"
date: 2006-04-23
forum: General Help
---

### Post by arsenic23 on 2006-04-23
I just tried to 
[INDENT]sudo apt-get install build-essential[/INDENT]
and was met with
[INDENT]Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter[/INDENT]

I don't have the CD anywhere near me.  I don't even have a burner with me.  I'm out in the feild and need this installed.  Can anyone help me, or should I just get in the car and drive home to get the CD?

---

### Post by cosmoshell on 2006-04-23
<snip>

---

### Post by Computeruser on 2006-04-23
Is it practical (speed of connection) to download it, and point to the download? If so, faster and cheaper than driving home and back (in most cases). I load VMware guests from .iso and it works fine.

---

### Post by sinkxdie on 2006-04-23
Go get that CD...Im with you?
Do you wanna help me with my scanner problem? :D

---

### Post by robglinka on 2006-04-23
Hey, try this:
  Go into your /etc/apt/ directory and edit your sources.list file.

  In there, it tells apt-get where to look for updates. Comment out all the "deb cdrom:" lines. apt-get should not look for files in your cdrom anymore.

-Rob

---

### Post by sinkxdie on 2006-04-23
But if you don't get the files from the CD, how woudl it install properly?
Download the .iso and change the sources.list CD-Rom Drive directory to the .iso directory mounted onto a virtual drive.
Just a suggestion

---

### Post by bobofett on 2007-05-10
Just wanted to add my two cents here.  I just installed 7.04 (kubuntu), and the first thing I tried to apt-get was the nvidia driver, and I got exactly the same message.  The solution robglinka provided did just the trick.

Seem Fiesty (at least the alternative version) installs a sources.list that has two cdrom lines (one commented out already) pointing to the installation CD.  Unfortunately the line in sources points to /cdrom, which for some reason or another is not linked correctly to /media/cdrom0 so the apt script will never find anything anyway...even if the most upto date nvidia drivers were even there.  So commenting out the cdrom line makes apt go to the net repositories to get it.

Worked for me anyway.

---

### Post by Nythain on 2007-05-10
yeah, that about sums it up...

---

### Post by Drone4four on 2008-01-18
This is a useful post.

---

### Post by izomorphius on 2008-01-30
Thanks for this post - it just sorted out a problem I was fighting with for about 3 hours...](*,)

---

### Post by mcwnz on 2008-04-21
Thanks.   commenting out the cdrom line in the sources.list file definitely: does the trick!  Useful post. :)

---

