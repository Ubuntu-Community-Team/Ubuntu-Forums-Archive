---
title: "Choosing OS in startup"
date: 2009-08-07
forum: General Help
---

### Post by AFUNA on 2009-08-07
I had ubuntu and winXP at the same time
winXP (on the C partition)
and ubuntu on its own partition
but when I formatted C to install a new windows, the interface where I can use to login into ubuntu or windows is disappeared
So how can I bring this interface back if I cant login Ubuntu @ the first place.
ps: am sure I didnt format my ubuntu partition ..
Thanks in advance ..

---

### Post by Mighty_Joe on 2009-08-07
[RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by michy99 on 2009-08-07
Read this page:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

EDIT: Beat to the punch!

---

### Post by burmanabhay88 on 2009-08-07
There's a software called "Auto Super Grub Disk". Install it in windows. It's got a GUI, and it's easy to use. Will suffice your needs.
[http://simplyeko.com/linux/the-simple-way-to-restore-grub-or-boot-menu-in-ubuntu-linux/]("http://simplyeko.com/linux/the-simple-way-to-restore-grub-or-boot-menu-in-ubuntu-linux/")

---

### Post by AFUNA on 2009-08-08
First of all thanks guys for ur quick reply
> **Mighty_Joe said:**
> [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
> **michy99 said:**
> Read this page:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

EDIT: Beat to the punch!
I dunno I couldnt do it (newbie :oops:) and it screw my boot and I had to fix my boot to access my windows
> **burmanabhay88 said:**
> There's a software called "Auto Super Grub Disk". Install it in windows. It's got a GUI, and it's easy to use. Will suffice your needs.
[http://simplyeko.com/linux/the-simple-way-to-restore-grub-or-boot-menu-in-ubuntu-linux/]("http://simplyeko.com/linux/the-simple-way-to-restore-grub-or-boot-menu-in-ubuntu-linux/")
Unfortunately this didnt work even it seems that it is the easiest way ..

---

### Post by ouker on 2009-08-08
Your mbr of your disk changed after you install a new windows system, So you can boot from LiveCD to install the grub again, how to repair the grub you can search it from internet!

---

### Post by hubertofliege on 2009-08-08
I don't know if this is too off topic.

When I turn on my computer, I'm offered the choice of operating systems, but sometimes when I update, it adds a new version of Ubuntu to the list.  It started something like this:

"
-----------------------------------------------------------------------------------
[FONT=Courier New][B]Ubuntu something something ###.13
Ubuntu something something ###.13 recovery mode
mem test 
Other systems:
Windows selector
[/B][/FONT] -----------------------------------------------------------------------------------
"

Now it looks more like this:


"
-----------------------------------------------------------------------------------
[FONT=Courier New][B]Ubuntu something something ###.16
Ubuntu something something ###.16 recovery mode
[/B][/FONT][FONT=Courier New][B]Ubuntu something something ###.15
Ubuntu something something ###.15 recovery mode
[/B][/FONT][FONT=Courier New][B]Ubuntu something something ###.14
Ubuntu something something ###.14 recovery mode
[/B][/FONT][FONT=Courier New][B]Ubuntu something something ###.13
Ubuntu something something ###.13 recovery mode[/B][/FONT]
[FONT=Courier New][B] mem test 
Other systems:
Windows selector[/B][/FONT]
-----------------------------------------------------------------------------------
"


Not a huge deal, just something I'd like to deal with eventually.

---

### Post by AFUNA on 2009-08-12
Oki I tried again
but seems very complicated ..
when I try to reinstall the grub it keeps saying
```
The file /media/root/boot/grub/stage2 not read correctly.
```
even am booting the correct partition
I found 2 partitions but am guessing that it isnt the Linux swap / Solaris so it is the second one cos it is the biggest one (space)
and it contains my documents which I saved on it when I was using it.
Am sure that I got something wrong in my steps I even couldnt unmount partitions to do the steps again so I made some screenshots
Check these 2 screenshots
First one shows the steps I made however I faced the error message

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124681&stc=1&d=1250133588[/IMG]

Second one shows my partitions 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124682&stc=1&d=1250133588[/IMG]

ps: am trying to fix the boot from Live CD ubuntu 8.04

---

### Post by AFUNA on 2009-08-14
any reply
guys windows sux
help me please.

---

### Post by soapBAR2 on 2009-08-14
I see what you've done. You've mounted the same partition twice - once in /media/root, and once in /media/root/boot. In the tutorial, the boot is on it's own partition (not necessary for non-raid devices, but often a good idea), whereas your install has boot on the same partition as the rest of your stuff.

Do what you did again, but leave out

> sudo mount /dev/sda5 /media/root/boot

---

### Post by AFUNA on 2009-08-14
I did it but I face an error message.
I made a screenshot with the error message for you guys

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124921&stc=1&d=1250298970[/IMG]

---

### Post by AFUNA on 2009-08-17
Any Help ??
Please !!

---

### Post by Epidural on 2009-08-17
> **hubertofliege said:**
> When I turn on my computer, I'm offered the choice of operating systems, but sometimes when I update, it adds a new version of Ubuntu to the list.

Huberto, it's not entirely recommended to delete the older kernel boot options as if an error occurs in your current kernel, you're somewhat screwed, but if you really want to it's a simple fix. Edit your grub file and delete the older kernel boot entries.

```
sudo gedit /boot/grub/menu.lst
```

Be careful when doing this! This is also where to permanently change other boot options, such as menu timeout and OS Choices, so I hope it keeps a small amount of relevance to the original thread.

---

### Post by oldfred on 2009-08-17
Rather than using a supergrub in windows get the supergrub download as CD or floppy disk.
Instructions on use are here:
[http://www.supergrubdisk.org/w/index.php5?title=Main_Page](http://www.supergrubdisk.org/w/index.php5?title=Main_Page)

---

### Post by AFUNA on 2009-08-21
what is the bug at xfs_freeze which unabled me to fix my grup and how to solve the problem !?
Please help !!

---

