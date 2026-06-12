---
title: "Mounting Problems"
date: 2009-08-23
forum: General Help
---

### Post by enterman on 2009-08-23
Hi, I'm having issues mounting 2 of my NTFS HDD's. Basically on one of them I get a "You do not have permission to mount this HDD" while on the other I get this: [http://img229.imageshack.us/img229/2820/screenshotshp.jpg/]("http://img229.imageshack.us/img229/2820/screenshotshp.jpg/"). I've been messing with both of them for a while to no end. I was getting that same error with the first drive that I'm getting on the 2nd one now. Here is my fstab: [http://pastebin.com/m10a72732](http://pastebin.com/m10a72732) and here is the result of sudo fdisk -l: [http://pastebin.com/m32e483c4](http://pastebin.com/m32e483c4) The first HDD is 500GB's and the 2nd is 250GB's. My fstab is going to look a bit dirty from me trying to fix this :P Thanks for any help you can provide.

---

### Post by enterman on 2009-08-25
Anyone?

---

### Post by trikster_x on 2009-08-25
What methods have you used to attempt to mount the drives?

---

### Post by P4man on 2009-08-25
Your fstab shows two entries for /media/sdb1. That cant be right. And the first of those also misses a "/" at the beginning for the device. Not sure about the mountlines if those are correct.

---

### Post by P4man on 2009-08-25
on closer look, your fstab is pretty messed up lol.

Try this:


#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                          0  0  
# /dev/sda1
UUID=bc31b347-cc63-4b0d-ac7e-4aabad565132  /              ext3         relatime,errors=remount-ro                        0  1  
# /dev/sda5
UUID=4f6399da-4e5e-4a1f-a699-f98b8f478f0f  /home          ext3         relatime                                          0  2  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                             0  0  
/dev/sdc1                                  /media/1.5TB   ext3         defaults,errors=remount-ro,users,user_xattr,user  0  0  
/swapfile1                                 swap           swap         defaults                                          0  0  

/dev/sdd1 /media/sdd1    ntfs-3g defaults, 0 0
/dev/sde1 /media/sde1    ntfs-3g defaults, 0 0      
/dev/sdb1 /media/sdb1    ntfs-3g defaults, 0 0

---

### Post by enterman on 2009-08-29
> **P4man said:**
> on closer look, your fstab is pretty messed up lol.

Try this:


#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                          0  0  
# /dev/sda1
UUID=bc31b347-cc63-4b0d-ac7e-4aabad565132  /              ext3         relatime,errors=remount-ro                        0  1  
# /dev/sda5
UUID=4f6399da-4e5e-4a1f-a699-f98b8f478f0f  /home          ext3         relatime                                          0  2  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                             0  0  
/dev/sdc1                                  /media/1.5TB   ext3         defaults,errors=remount-ro,users,user_xattr,user  0  0  
/swapfile1                                 swap           swap         defaults                                          0  0  

/dev/sdd1 /media/sdd1    ntfs-3g defaults, 0 0
/dev/sde1 /media/sde1    ntfs-3g defaults, 0 0      
/dev/sdb1 /media/sdb1    ntfs-3g defaults, 0 0
ya...I knew my fstab was pretty bad XD. After doing this my 1.5TB, 500GB (sdb) and 250GB (sdd) auto-mounted with the system. It also says I do not have permission to un-mount them. The 1.5TB is the only drive I need auto-mounting. Any ideas?

---

### Post by scouser73 on 2009-08-29
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by enterman on 2009-08-29
> **scouser73 said:**
> Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")
I know how to mount/unmount drives XD but I'd rather be able to simply be able to mount them from places with a click and unmount them by right clicking the drives and clicking unmount. I used to be able to do that and cannot explain why I can't now.

---

### Post by enterman on 2009-09-05
Sorry for the bump but I'd really like to get this solved.

---

### Post by P4man on 2009-09-05
If you dont want automounting, just remove those drives from your fstab?
Perhaps also remove the mountpoints in /media/

---

### Post by jeffdunn on 2009-09-05
I've been having similar strange problems with mounting devices that were formerly plug and play and are now, mysteriously, giving permission problems. For example I have a hand held wav/mp3 recorder that connects like a drive to my computer by USB. When I first bought it, it would simply mount and I could manipulate the files. Now, suddenly, in the last week, although I can mount the device and drag files from it to my desktop, I don't have permission to rename files or delete them, which is a problem, because the only way to clear memory is by connecting it to the computer. As soon as it fills the SD card, I'll have to through it away and get a new one unless I can find a way to clear it. Well, not really throw it away 'cos, if I go to a web cafe and connect it to a windows machine, there's no problem (not that I'm a windows fan). I've also had problems with my second hard disk (formerly working fine), suddenly also giving permission problems. I sudo stuff once in a blue moon so I don't think it's any fault of mine. I should also mention that since this began, my mouse has gone haywire, and a couple of times, firefox has opened about 20 sessions of itself with me even touching the computer. I just sttod there eating a sandwich and watching in amazement.
I'm not a tech so I don't understand this stuff, but it seems that my version of Ubuntu 9.04 is acting a bit strangely of late. My firewall and antivirus arn't detecting anything either.
Just thought I'd add this to the conversation.

---

