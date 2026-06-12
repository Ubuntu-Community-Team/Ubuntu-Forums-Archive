---
title: "Frustration Level Rising..."
date: 2006-03-09
forum: General Help
---

### Post by maddog39 on 2006-03-09
Hello all,

Okay, so I am gettng pretty darn frazzled right about now. I cant get my x86 installation to boot at all on any of my PCs, they all just boot windows and ignore the CD completely. I had even tried forcing it to boot from CD by disabled the HD from loading in the boot sequence but instead my comps. completely and literatly REFUSED to boot from the CD, reminded me of a 2 year old not getting their way. I also posted a topic about this and I read the topic where they solved the problem but none of my computers have floppy drives because there all either recent or new, nor do I have floppy disks anyway.

I am also having numerous problems on my macs. They are NewAge macs. I have a PowerBook G4 12" from 2003 running Mac OSX 10.4.5 and when I try to boot from the LiveCD, I do the Command-Option-Shift-Delete command on my keyboard because the C button doesnt do anything. I brings up a dark greay screen and start reading from the CD and then in the center of the screen comes a MacOS9 animated folder image that has a picture of the Finder logo and flickers between that and a question mark on the folder. Then about 1-2 minutes later it just decides to boot Mac OSX. Doesnt make sense at all. I also tried this on my sisters iMac G5 from 2004 and has Mac OSX 10.4.4 on it and it does the EXACT same thing as my PowerBook.

I am dieing to use Ubuntu but I cant if it just refuses to work for me. If someone could help me solve atleast some of these issues, that would be GREATLY appreciated.

Thanks!
-maddog39 :D

---

### Post by dmizer on 2006-03-09
once you are in windows, if you browse to the cd that you've created, does it have one single file on it, or many files?

---

### Post by Sutekh on 2006-03-09
- If you downloaded a LiveCD for your x86 PC, then it stands to reason that it won't work on your Mac (unless you downloaded a LiveCD for a Mac)

[http://http://ftp.ussg.iu.edu/linux/ubuntu-releases/5.10/]("http://ftp.ussg.iu.edu/linux/ubuntu-releases/5.10/")



 - Here are some things to check with the LiveCD you downloaded.

 - **The MD5 checksum**.  This ensures that the ISO was not corrupted during download.  This link has the MD5 sums for the LiveCDs.  You will need to check the MD5 sum of the ISO you downloaded against these values for a perfect match.

[http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/MD5SUMS]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/MD5SUMS")

 - Here is a Windows program for calculating MD5 sums.

[Win MD5 Sum]("http://http://www.nullriver.com/index/products/winmd5sum")


 - **LiveCD ISO burnt as Image.**  The other thing to check is that the LiveCD was burned correctly.  By correctly I mean as an Image, not a data disc or bootable disc.

[Ubuntu Forums - Burn an ISO disc image with Nero in Windows]("http://www.ubuntuforums.org/showthread.php?t=111589&highlight=burn+nero+image") is a simple howto if you use Nero Express, similar if you use full Nero.  

 - Close the wizard at start-up and choose 'Recorder' and then 'Burn Image', then select the ISO you downloaded.

[Ubuntu Wiki - Burning ISO HOWTO]("http://https://wiki.ubuntu.com/BurningIsoHowto") - Includes methods for Macs

---

### Post by RAOF on 2006-03-09
It sounds like a problem with how you are writing the CDs.  You've downloaded  a *breezy-install-i386.iso* file, or something similar?  Now, you should burn that **image** to a CD, **not** create a CD with that file on it.  How you do this will depend on what you use to burn CDs.

---

### Post by maddog39 on 2006-03-10
Okay, I have a two CDs with an ISO on them, one is a PPC Live CD and the other is a i386 Install CD. Neither of them are working. I have also made two different coppies of the i386 Install disk, one on my windows computer and one on my mac, figuring it would make a difference since my windows computer told me that it added data to the ISO. It didnt. The way I created the CD was putting a CD in the drive and pasting the file in. I geuss I can try it the other way around. Not sure what difference it will make but. Thanks. :D

---

### Post by az on 2006-03-10
[QUOTE=maddog39]Okay, I have a two CDs with an ISO on them, one is a PPC Live CD and the other is a i386 Install CD. Neither of them are working. I have also made two different coppies of the i386 Install disk, one on my windows computer and one on my mac, figuring it would make a difference since my windows computer told me that it added data to the ISO. It didnt. The way I created the CD was putting a CD in the drive and pasting the file in. I geuss I can try it the other way around. Not sure what difference it will make but. Thanks. :D[/QUOTE]
An iso image is a file with an entire filesystem on it.  Putting that file onto a disk will result in the disk with that one file on it.  Making a cd *out of that iso image* will put all the files in the iso filesystem on the cd and the cd will be the real install cd at that point.

It is a very common mistake.

---

### Post by maddog39 on 2006-03-10
Ahhhh... Okay, because people were telling me NOT to unpack the ISO, I figured it would make more sense to unpack it and then burn it. Wow, okay that makes ALOT more sense now. Thanks! :D

---

### Post by az on 2006-03-10
No.  You don't unpack it either.  You need to write it to the cd.  What function it is called depends on your software....

---

### Post by mikl on 2006-03-10
[QUOTE=maddog39]Ahhhh... Okay, because people were telling me NOT to unpack the ISO, I figured it would make more sense to unpack it and then burn it. Wow, okay that makes ALOT more sense now. Thanks! :D[/QUOTE]
Good you figured it out. Happy ubuntu-ing :)

---

### Post by maddog39 on 2006-03-10
Yeah I cant wait, I looked at this one because my friends reffered it to me and I also looked at other free linuxes and this is the only one that realy appealed to me. Thanks Alot for the help!!! :D

---

### Post by DavidW2 on 2006-03-10
If you have Nero on your Windows computer just double-click on the ISO file in File Explorer and it will bring up the "Create CD Image" window (or something like that) with your image as the source.  From there you just press Burn and wait for it to finish.  Then reboot and watch Ubuntu load up. :D

---

### Post by maddog39 on 2006-03-10
I dont have Nero and dunno what it is besides a CD burning program. I re-made my CDs yet none of them work still. Im very confused about this hole image thing. When I made my new CD for both my comps, on my windows computer i just unpacked the ISO with WinRAR and reburned the CD. On my mac I just opened it and the Disk Manager Utility came up and it unpacked it as a disk image on the desktop. On both I just copied and pasted all the files and folders onto my CD and burned it. Although still not working on either computer (not my windows comp(x86 Install CD version) nor my mac(PPC Live CD version). :(

---

### Post by Lord Illidan on 2006-03-10
Try this free app for your Windows : [http://www.cdburnerxp.se/](http://www.cdburnerxp.se/)

It can burn iso images, I used it myself without many problems.

---

### Post by nalmeth on 2006-03-10
go here:
[http://www.terabyteunlimited.com/utilities.html](http://www.terabyteunlimited.com/utilities.html)
and scroll down, and download Burn CDCC
Its a tiny free application that burns ISO's to disk.

---

### Post by maddog39 on 2006-03-10
Okay I am starting to burn the disk using that program(CD Burner XP), I am using its write iso to disk utility. Hopfully this will work. :)

---

### Post by stalefries on 2006-03-10
You can't unpack them and then copy the files, because (if I have it right) it is specially formatted to be bootable. That's why it's distributed as an .iso, and not a bid old zip file, or something like that. That's where you were going wrong.

---

### Post by maddog39 on 2006-03-10
Yeah, LOL :oops: Well it boots perfectly now on my windows computer, i didnt install yet because im waiting for a new HD that im getting this weekend. I am now properly writing my PPV Live Disk and play with Ubuntu on my mac until then. :D

---

### Post by maddog39 on 2006-03-10
Okay, everything seems to be working fine now as I am posting this message from a breezy installation LOLx :lol: :). Thanks for all the help guys, like I said, I really appreciate it.

Thanks Again!
-maddog39 :D

---

### Post by az on 2006-03-10
"i didnt install yet because im waiting for a new HD that im getting this weekend"

That was quick!


Let the weekend begin!

---

