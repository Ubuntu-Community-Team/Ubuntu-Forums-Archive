---
title: "Uninstall help"
date: 2010-12-28
forum: General Help
---

### Post by TJarrell on 2010-12-28
Sorry in advance because I don't get much pc time anymore so searching is impossible with my limited time. My cousin has a acer netbook (don't know what model off hand) She wanted me to get rid of windows 7 that came preinstalled on it.
 
As an alt I suggested she try ubuntu. I've used it before on my desktop and loved it but my girlfriend insisted I remove it before getting familer with it. On my desktop I was able to remove unbuntu with no problems what so ever in disk cleanup but appertly these new new netbooks don't have that feature in the condensed crap version of 7...
 
Long story short, after maybe ten seconds my cousin calls me back and she wants it removed instantly. I guess she doesn't like that it isn't windows, whatever, last favor I do for her...
 
My problem is that I have no idea how to remove the linux partition and grub loader from her pc...
 
any sugestions (I do not know how to run linux or anything without a gui)

---

### Post by Loyus on 2010-12-28
Your cousin wants you to reinstall Windows ? Or just to remove Ubuntu ?

If you reinstall Windows, it'll propose you to use and format the entire hard drive, which will remove the linux partitions as well as the grub.

Check if her netbook has a recovery partition (it would reset the computer to its original state). If not, just boot the computer from a Windows startup disk.

If you only want to remove the grub, you can follow [these instructions]("http://www.ehow.com/how_4836283_repair-mbr-windows.html").

---

### Post by TJarrell on 2010-12-28
thanks for the quick response...

She wants ubuntu removed. Her windows is fine and intact, I had installed the dual boot method. I just put it on my desktop again and love it but her impatience bothers me.

So if I understand the instructions correctly I should delete the linux partion and use the fdisk on a live usb to repair the MBR. She doesn't have a recovery cd because it is handeled with a utility partition on her laptop. I wonder if that will be a problem later on not having a cd and all.

I'll give it a try tomorrow and repost my results thanks again...

---

### Post by West201 on 2011-01-11
If you can still boot to Windows. Go to the control Panel, there is an option that lets you burn your own recovery disk..

---

### Post by West201 on 2011-01-11
I almost forget you can I also type in 
bootrec.exe/FixBoot

bootrec.exe/FixMbr 

from the recovery disk to rewrite the Mbr:)

---

