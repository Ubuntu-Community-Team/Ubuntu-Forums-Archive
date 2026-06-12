---
title: "Grub Rescue Shell, / Partition Deleted"
date: 2010-05-22
forum: General Help
---

### Post by formyfriend on 2010-05-22
Worst Fears Came true today :(

I formatted the /dev/sda8 where Ubuntu Linux was installed.

Now after booting it is dropping to (GRUB 2 Rescue Shell) 
grub rescue >
I tried ls 
(hd0), (hdo,1), (hd0, 2)... is coming.

My CD Drive is not working, hence I tried to boot through the USB Installer (unetbootin-windows-442). I configured the BIOS to boot from the USB, 

Now I am getting the error "Operating System Not Found". Whats the reason ??.

---

### Post by formyfriend on 2010-05-22
Any Help ?

---

### Post by ogbomo on 2010-06-17
i have unbutu and vista on my system, i went to disk management to delet some partition now i cant log  get back to my pc am getting error message Grub Loading.[SIZE=2]
error no such partition i have try all comand i find in this forum nothing since to work can some one help me please am stuck
[/SIZE]

---

### Post by mspakousky on 2011-04-23
I am having the same problem.  Deleted my Ubuntu partition and am now getting Grub Rescue.  I've tried Ubuntu-rescue-remix boot cd, parted magic, and ubuntu 10.10 cd.  In all cases it's like it doesn't even read the CD. It just reads "reboot and select proper boot device or insert boot media in selected boot device and press a key"

I'm not against doing the legwork for figuring this out, but if I can't even get it to try and read a CD, I'm not sure what my options are. I'll try a and do this via removable device tomorrow.  I recently moved and I don't have many items, like a usb flash drive or my windows 7 install disc.  I appreciate the help.  If anyone is near Eugene I will buy them a beer!

---

### Post by Hedgehog1 on 2011-04-23
I am in Portland, but it is too far to drive for a beer with all the lovely micro breweries around town.

If you are planning to reinstall Ubuntu, a fresh updated grub will be loaded with your new install.  You will need a USB install or an external CD to boot from.

If you are wanting to drop Ubuntu you will still need a CD to boot from.  Here are the other steps:

If you don't have your windows a recovery disk, you can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

***The Hedge***

:KS

---

### Post by mspakousky on 2011-04-23
Hedgehog, thanks for the quick and extensive reply.  I just moved out here but yes, the thing I think I like the most is the assortment of amazing beers.  It's insane!  Every time I go to the store I come across new IPA's and porters I've never even heard of, let alone tried.  

Anyway, I'm out of CDR/DVDR, so it'll have to wait until later today when I go and buy some more.  I don't think it will work, however, since as I said, it's not reading any boot device, even an ubuntu reinstall or boot repair dvd.  I haven't tried the jump drive yet, so that might work.  Also, now, I am beginning to think the windows 7 repair disk might work as well.  Thanks for the help.  I'll post later.

---

### Post by mspakousky on 2011-05-05
Finally got it fixed.  I can't believe how simple it was. I am SO retarded.  Since I used a mac, I thought the mac automatically burned ISO images.  It does, you just have to used disk utility.  Anyway, all good now. Thanks.

---

