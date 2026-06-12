---
title: "Partioning Ubuntu and XP"
date: 2006-06-17
forum: General Help
---

### Post by F3RGY68 on 2006-06-17
I am trying to partition my hard drive so I can have Ubuntu and Windows XP.  I'm following this guide: [http://www3.telus.net/linux4u/ubuntu.html]("http://www3.telus.net/linux4u/ubuntu.html")  When I go to primary and try to resize the partition, it doesn't do anything. It has worked when I put it on something besides ntfs but it formatted Windows XP, which I just reinstalled.

---

### Post by ajgreeny on 2006-06-17
Sorry, I don't understand what you are trying to do or exactly what the problem is.  More info needed.

---

### Post by F3RGY68 on 2006-06-17
Anyone know?

---

### Post by RRS on 2006-06-17
You might find [this guide]("http://users.bigpond.net.au/hermanzone/index.htm") more helpfull. The explanations of "what and why" are a little more detailed.

If you still have trouble please be a little more specific about any error messagges, etc. 

Also are you installing Dapper or breezy and from which ISO?

---

### Post by F3RGY68 on 2006-06-17
No it didn't help.
[IMG]http://users.bigpond.net.au/hermanzone/p3d/13ntfs.png[/IMG]
When I'm at this step, I enter in the size and press enter, it doesn't do anything but go back to the main partitioning menu with no changes to the disk.

---

### Post by RRS on 2006-06-17
Could be a problem with the CD. Possibly corrupted during download or burning.

Normally if there's a problem with the hard drive preventing the operation it'll tell you.

Not sure what to suggest next, sorry.

---

### Post by F3RGY68 on 2006-06-17
[QUOTE=RRS]Could be a problem with the CD. Possibly corrupted during download or burning.

Normally if there's a problem with the hard drive preventing the operation it'll tell you.

Not sure what to suggest next, sorry.[/QUOTE]
It has worked when I changed it from ntfs to Ext3 journaling system but I don't want that to format my hard drive again.  Is there a setting that won't format the hard drive but I will be able to switch back to ntfs?

---

### Post by MarinaraOfDeath on 2006-06-17
[QUOTE=F3RGY68]I am trying to partition my hard drive so I can have Ubuntu and Windows XP.  I'm following this guide: [http://www3.telus.net/linux4u/ubuntu.html]("http://www3.telus.net/linux4u/ubuntu.html")  When I go to primary and try to resize the partition, it doesn't do anything. It has worked when I put it on something besides ntfs but it formatted Windows XP, which I just reinstalled.[/QUOTE]

Allow me to suggest that you don't use this interface to the utility for the partitioning. Instead, boot up using the Ubuntu install disk (or a [Knoppix]("http://www.knoppix.org/") DVD if you've got one -- and if you're gonna be dual-booting, you really want a copy, it's the Swiss army knife of linux live CDs and will really save your bacon at some point). Handily, the Dapper install CD *is* a live CD (or DVD, if that's what you burned), so you can boot up with that. 

Then go to the System Tools menu (I believe, it's been two weeks since I installed) and boot up [QtParted]("http://qtparted.sourceforge.net/"), a nice GUI interface to [parted]("parted"). This is a slightly newer version of the same partitioning tool in everyone's beloved Knoppix distribution (not that I'm trying to make [K]Ubuntu jealuous :D ). It takes a bit of playing with to get used to what does what, but as long as you _do not_ select the command &commit, you can play to your heart's content learning what to do.

Most importantly, parted, the partitioning tool within QtParted resizes ntfs partitions **non-destructively**. This means no reinstalling Windows unless you format the partition you installed it to! Good luck, and let us know how it goes.

---

### Post by MarinaraOfDeath on 2006-06-17
For screenshots showing what to expect in the partitioning when you install Dapper, [this site]("http://www.psychocats.net/ubuntu/installing.html") is just awesome. You'll probably also want to see the [Luna Park review/mini howto]("http://lunapark6.com/?p=1235&cp=7#comments"). And absolutely get [Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646") or [EasyUbuntu]("http://easyubuntu.freecontrib.org/") for more awesomeness after that. Linux communities rock as thoroughly as Mac groups.

---

