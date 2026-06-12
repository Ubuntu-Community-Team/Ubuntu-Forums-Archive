---
title: "Computer Recovery usb drive recommendations?"
date: 2011-01-24
forum: General Help
---

### Post by dhysk on 2011-01-24
I have an old 160 GB HD I want to use as a bootable drive for the purpose of fixing computers and recovering lost files.

I'm no computer wiz but I have fixed a few peoples PC's at chruch so I have become the defacto computer fixer uper.  Many of you can probably associate with this.  As soon as you help one person in a group with a computer suddenly EVRYONE needs help.  But I enjoy it so anyway.. back to the topic.

Tools I normally use.

Clonzilla:  I like to Image a drive before I mess with it that way I can always go back to the original state encase I do something risky and make things worse.  Hasn't happened yet but the day I don't do an image will be the day I kill somebody's file system and have to do a recovery.....

XP CD: Use it only for fixmbr and fixboot.  

I haven't ran into much file recovery yet but I've used a few linux file carvers before so something with this ability is a must.

Things I need..

*Bit for Bit forensic style imaging- don't want to loose 'blank' sectors encase I need to do some file carving.

*Used space imaging - so I could if I had to image someones drive and put it on a smaller one if need be.  This would probably have to be done with something with decent error handling like ddrecover or dd_recover.  I cant remember which I used but it was great getting an OS off of a bad drive.  But I put it on a larger one, so is there a way to image a drive and put it on a smaller one given the USED space from the original doesn't exceed the size of the new drive?

*Windows fixmbr- does linux have a tool to fix windows MBR?

*Windows fixboot - this is less likely to have a linux version but maybe you guys know of something?

*File recovery tools - File carving obviously, but I'd also like something that can find recently deleted files from the master file list without going threw the carving process.

*file system tools - gparted along with some tools to repair corrupted file systems, mostly windows but who knows when I'll need to fix ext3-4 systems for my machines.

*Virus scanners capable of scanning for viruses on a mounted windows drive.

*regedit tools - just encase I want to really dork someones machine up ;), j/k I'm laking in this area but again I can learn and I always have an image to go back to.

*any other tools I may need you guys can think of that may be of use for these type of things.


I've looked at SystemResueCD, Trinity Rescue Kit, and at this moment the best looking one is ubuntu rescue remix.  I am willing to install additional tools if need be.  It also needs to be able to run on a larg array of computer hardware, as well as very, very old computers...  (I know I want my cake and eat it too ;).. but so far with my limited linux experience thats exactly what I get... eventually.)

Again this will be put on a 160 GB drive to accommodate HD images so it still needs to be 'relatively' small and will be made into an external USB bootble drive.

Short version I want a one stop shop bootable drive to do most common computer repair jobs.

---

### Post by dhysk on 2011-01-24
Bump.  wrong section maybe?

---

### Post by dhysk on 2011-01-31
Figured I'd give one more bump a try to see if I could even get any partial answeres before I give up and just pick a distro and start installing random tools ;).

Big ones are

Imaging ware you could put the image onto a smaller drive/partitio than it was originaly on.

Good linux fixmbr utilities (windows MBR)
linux fixboot utility? (this one is a streach I'm sure)

---

### Post by ronnielsen1 on 2011-01-31
I like Hirens boot cd but I've never thought about installing it to a hard drive. It's pretty powerful

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

---

### Post by Ocxic on 2011-01-31
> **ronnielsen1 said:**
> I like Hirens boot cd but I've never thought about installing it to a hard drive. It's pretty powerful

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Do you know how to download it???, I can't find a link for the life of me.

---

### Post by dhysk on 2011-01-31
very end of the list. Hmm never mined not a link.. hmm good point.

---

### Post by ronnielsen1 on 2011-01-31
[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)

Scroll down to the bottom of the above link. Forgot that little detail. It seems to be a hidden file on the net. Took me forever to find it the first time

---

