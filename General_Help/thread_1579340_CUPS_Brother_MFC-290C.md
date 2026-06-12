---
title: "CUPS Brother MFC-290C"
date: 2010-09-21
forum: General Help
---

### Post by Thinkin on 2010-09-21
Im on 64 Bit and have compiled the mfc driver from the source files on the Brother site.  I have also completed the installation through ubuntu and with cups.

I can see the printer [which is shared off of a XP Machine], it shows idle, but nothing prints.  

Does not work when USB connected either!  What am I missing?

---

### Post by gordintoronto on 2010-09-21
Compiling from source is not useful in this case, but it could cause problems.

What version of Ubuntu do you use? 

Brother is well supported in Ubuntu; I would begin with Administration/Printing.

---

### Post by Thinkin on 2010-09-21
Thanks, I am on 10.04 64bit.  I did not see any compatible download for 64 bit on the brother site.

---

### Post by gordintoronto on 2010-09-23
I also use 64-bit, but that had no effect whatsoever on the Brother support.

Start with Administration/Printing.

---

### Post by altjx on 2010-10-12
> **gordintoronto said:**
> I also use 64-bit, but that had no effect whatsoever on the Brother support.

Start with Administration/Printing.

Need help getting this driver as well. Any updates?

---

### Post by gordintoronto on 2010-10-13
Get rid of the things you did, which are counter-productive.

Begin at Administration/Printing, select "add" and say it's a network printer. Give it a minute to appear, then select it.

Linux is not Windows, and in some cases, Windows-type thinking will be very negative to making progress. In particular, remove "download" from your vocabulary.

---

### Post by altjx on 2010-10-13
Of course dude, but the driver is what's missing here.

---

### Post by plucky on 2010-10-14
> **altjx said:**
> Of course dude, but the driver is what's missing here.

The Brother drivers are built for 32-bit systems and will work in 64-bit systems if you install the required libraries.

Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-290C) and download the .deb format files for lpr and cupswrapper drivers.Install by double clicking on them.

Also follow the install instructions on the website,especially the prerequisites for 64-bit install.

If your printer has a scanner,you will also have to download the .deb scanner files from the [Brother Website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Good Luck

---

### Post by altjx on 2010-10-14
> **plucky said:**
> The Brother drivers are built for 32-bit systems and will work in 64-bit systems if you install the required libraries.

Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-290C) and download the .deb format files for lpr and cupswrapper drivers.Install by double clicking on them.

Also follow the install instructions on the website,especially the prerequisites for 64-bit install.

If your printer has a scanner,you will also have to download the .deb scanner files from the [Brother Website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Good Luck

I do have the pre-requisites, just checked. The deb (both deb files) still say Wrong architecture 'i386'


[IMG]http://img811.imageshack.us/img811/6015/firste.png[/IMG]
[IMG]http://img524.imageshack.us/img524/2573/secondk.png[/IMG]

---

### Post by plucky on 2010-10-15
You need to use the dpkg -i --force-all command.

Follow these [Instructions](http://ubuntuforums.org/showthread.php?t=590793)

Just tried it on my Maverick 64-bit VM and it seems to work.Of course I don't have the right printer to test if it actually works.

Good luck

---

