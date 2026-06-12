---
title: "Dualbooting Vista and Ubuntu for College"
date: 2010-06-08
forum: General Help
---

### Post by sports fan Matt on 2010-06-08
I may need (for college) to dual boot Vista & Ubuntu.  I am trying to get around it but in the event I do need to, how big of a hard drive space do ya'll use for it?  I am also looking to see how easy it is to reconfigure (since I have lucid 1st, and I have heard it is easier with ubuntu) 1st then vista second, is this true?

---

### Post by oldfred on 2010-06-08
Many say it is easier to add windows first, but the reason is that windows will install its boot loader to the MBR and you have to reinstall grub or grub2. Since it only takes a few minutes to boot the Ubuntu liveCD and reinstall grub it is no big deal.

You do have to have a primary partition to install windows to.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by sports fan Matt on 2010-06-08
The good thing is while I do not have everything backed up to a removable device, I do have everything stored in Firefox with Xmarks.  

Thinking for the communications school I'm attending, they may need vista at some point:)

---

### Post by sports fan Matt on 2010-06-08
I am going to dual boot, because I figure at some point (even though I am not 100 % sure), it's probable that I would need the partition :).

---

### Post by sports fan Matt on 2010-06-10
Since I have Vista 1st, how easy is it to dual boot ?

---

### Post by Ozitraveller on 2010-06-10
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

I hope these help. Suggest you try the live-cd first to see whether you have any hardware issues. 

Really it's no big deal..

---

### Post by sports fan Matt on 2010-06-10
I can shrink if need be up to 204068 which would be the entire partition. But since I mainly want Ubuntu (want to leave enough room for a manageable vista install, what is suggested?)

---

### Post by Ozitraveller on 2010-06-10
I have a 320 gb drive and I have 50gb for ubuntu which is more than enough. 

I have these partitions for ubuntu within my 50gb  /boot, /root, /home, /swap.

---

### Post by sports fan Matt on 2010-06-10
ok, So if I have 500 gb, what would work..75?, 100?

---

### Post by Ozitraveller on 2010-06-10
Yes either of those easily, and remember ubuntu can read/write to ntfs partition. I think, a full ubuntu install is around 6gb, 10 at most.

---

### Post by sports fan Matt on 2010-06-10
As of now, I have 253 gb for Ubuntu. One more question if anyone can answer.  I have a series of Windows fonts on my vista partition and was wondering if there was a way to transfer the fonts to my ubuntu partition?.

I'll check back in the morning since it is 2 am here.

---

### Post by oldfred on 2010-06-10
I always install this:
sudo apt-get install msttcorefonts

Do not know about directly adding fonts.

I still use XP for one application. I originally set up a shared NTFS partition so I would be able to easily share data without having to write into the windows system partition.  This made it easier to convert to Ubuntu as firefox, thunderbird and photos were all the same in both. Now I have most data in Ubuntu but liked the idea of a separate /data partition so I could share data in other systems. My root with many programs is about 6GB, my /home is 1GB and all my data is either in the NTFS shared or the /data partitions.

---

