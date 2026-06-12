---
title: "Grub MIA !!"
date: 2010-12-04
forum: General Help
---

### Post by DaveCason on 2010-12-04
Hi, 
 
So I've read a bit on the grub loader but I can't find my situation.
 
I loaded 9.10 on my laptop from scratch then when in and shrunk the dev/sda1 (down to a 10gig partition) that has Ubuntu on it and then put windows on the dev/sda2 (100gig) that I made for windows xp. Right now if I boot the laptop it goes right in to windows on the sda2 part.
 
/dev/sda1 ext1 10Gb
/dev/sda2 ntfs 100Gb
/dev/sda3 ext 4.5Gb 
/dev/sda5 swap 4.5Gb
 
So how can I get Ubuntu to see the install on sda1 and also add the windows partition 
on so it cab be selected as well?
 
When I boot the 9.10 install CD and run Gparted, it sees everything but when I try the
sudo grub command it says it can't find it also the path is MIA and when I try sbin/grub too.
 
Cheers'
Dave

---

### Post by drs305 on 2010-12-04
This link will fix you up:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")


when you installed Windows it wrote it's own information to the MBR. The link will show you how to get it back to Grub2, which is kind enough to give you a choice of OS's!

---

### Post by DaveCason on 2010-12-04
Thanks !
 
I ran it as far as "
sudo grub-install --root-directory=/media/sda5 /dev/sda 
and got back ....
 
Install finished.  No error reported. 
 
then a line about the map being at:  /media/sda1/boot/grub/device.map
I tired to gedit it to have a look but it appers to be blank or empty!  DOH!
 
I'm open to suggestions!  (grin)
 
Cheers'
Dave

---

### Post by wilee-nilee on 2010-12-04
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by vaniaspeedy on 2010-12-04
Is it working for you?
If not, take a look at the device.map file you found. Try adding this line to it:
```
(hd0)    /dev/sda
```

---

### Post by DaveCason on 2010-12-04
OK, so I rebooted the laptop and I am now in the orginial 9.10 that was first installed on the laptop ....
 
So now I just need to find the how-to and the config info for grub 2 to add the windows info for the 
install on sda2 so the loader lets me pick a real OS or Windows!   (grin)
 
Also is there a way to edit the grub loader so it picks windows as the first OS - and no-  its for the wife
to use ..... but I'll get her converted.
 
Cheers'
Dave

---

### Post by DaveCason on 2010-12-04
Uummm, Gee !! .... what an interesting command ..... 
 
"  Update-grub  "  Who knew?!  Thanks everyone ! 
 
I'll go play and see if I can figgure out how to change the order!
 
Cheers'
Dave

---

### Post by sikander3786 on 2010-12-04
> **DaveCason said:**
> Uummm, Gee !! .... what an interesting command ..... 
 
"  Update-grub  "  Who knew?!  Thanks everyone ! 
 
I'll go play and see if I can figgure out how to change the order!
 
Cheers'
Dave
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

