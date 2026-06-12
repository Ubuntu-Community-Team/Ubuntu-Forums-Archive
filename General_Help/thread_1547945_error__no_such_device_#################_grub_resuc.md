---
title: "error : no such device ################# grub resuce&gt;"
date: 2010-08-07
forum: General Help
---

### Post by morteza100 on 2010-08-07
Well i installed ubuntu 10.04 and it said i needed to install new  drivers so i did, then i restarted and a black screen came up saying  terminating programmes, it was like that for 20 minutes, so i just shut  off my pc.
 
now when i turn on my pc it comes up with 
 
" error : no such device ################# grub resuce> "
 
now i can not load into windows neither linux. i dont mind loosing stuff  i have on linux, but i can not risk loosing my stuff on windows. 
 
i really need your help.

Thanks 
Morteza100

---

### Post by Rubi1200 on 2010-08-07
Hi and welcome to the forums :)
 
Do you still have the CD you used to install Ubuntu?
 
If yes, boot the computer with it and choose to try Ubuntu in live mode. Do not choose the option to install.
 
Then, click on the link at the bottom of my post and follow the instructions there.
 
Post the results back here and we will see what can be done to help you resolve this.
 
Also, please paste the results and wrap them with the # tag.
 
Thanks.

---

### Post by xXxBlender3DxXx on 2010-08-07
I suggest following Rubi1200's instructions.

I had a similar problem. GRUB did not install properly (GRUB is the bootloader that ships with Ubuntu).

I booted my LiveUSB, opened up Terminal, and typed:
```
sudo apt-get install grub2
```

Then:
```
sudo grub-install /dev/sda
```
This could be different for you, so don't run this exactly.

That fixed my GRUB problem.

Good luck with yours.

---

### Post by Rubi1200 on 2010-08-07
> **xXxBlender3DxXx said:**
> I had the same problem. GRUB did not install properly (GRUB is the bootloader that ships with Ubuntu).
 
If you have a LiveCD, you're all set.
 
Boot into a LiveCD or LiveUSB, open up Terminal, and type in:
```
sudo apt-get install grub2
```
 
Now, run:
```
sudo fdisk -l
```
 
It should display a bunch of stuff, so look for a thing that says "EXT4" (or EXT3 or EXT2). Note the number on that row (like /dev/sda1), since that is you partition number.
 
Now, run:
```
sudo grub-install /dev/sda
```, but replace /dev/sda with your drive code (without the number at the end).
 
It should install and say stuff like "Found Ubuntu, Found Windows", etc.
 
If that doesn't work, just reinstall Ubuntu.
 
I agree that this is _usually_ the method to solve problems like this. But, in this case we do not know if the OP has a Wubi install or a regular install, how the partitions are set up etc.
 
Better to be cautious and post a couple of extra times to make sure before we offer advice.
 
:)

---

### Post by morteza100 on 2010-08-07
i just tried both my old ubuntu disk and the new Lucid one, both take years to even load up. 

so i will try the usb way :) 


Give me time ;)

oh and i did wubi install (Y)

---

### Post by xXxBlender3DxXx on 2010-08-07
Hmm, if you really NEED to do a USB install, just use [UNetbootin]("http://unetbootin.sourceforge.net/") and load the Ubuntu ISO.

Okay, so Wubi it is.

I haven't had this happen (yet :P), so I would guess you need a Windows bootable install disk because the MBR was damaged.

Can you tell us what version of Windows it was? The XP bootloader and the Vista/7 bootloader are slightly different creatures...

---

### Post by morteza100 on 2010-08-07
Windows xp

I really want to keep all my windows stuff...

---

### Post by Rubi1200 on 2010-08-07
> **morteza100 said:**
> Windows xp
 
I really want to keep all my windows stuff...
Do you have the Windows XP installation CD?
 
And, I am pretty certain we can help you sort this out and that you will have access to your files etc. again.
 
Hang in there!

---

### Post by morteza100 on 2010-08-07
Yeah I do have the disk still :) 

The ubuntu CD isn't loading so can I just ditch ubuntu and work on accessing windows again....



Am hanging

---

### Post by Rubi1200 on 2010-08-07
Ok, the fix can be found here:
 
[http://ubuntuforums.org/showthread.php?t=1014708&highlight=howto+bootloader](http://ubuntuforums.org/showthread.php?t=1014708&highlight=howto+bootloader)
 
Scroll down until you get to the Windows XP section.
 
Follow the instructions there and everything should be back to normal.
 
Let us know if you need more help and if everything goes well.
 
Good luck!

---

### Post by morteza100 on 2010-08-07
i just want to say thanks to both of you. (tying from Windows)

the thread worked a treat. :)



thanks so much :D

---

### Post by Rubi1200 on 2010-08-08
I was traveling the last 24 hours, so I wasn't able to respond.

Glad it worked out for you! Yay!

Please mark this thread Solved using the thread tools near the top of the page.

If you like Ubuntu and want to consider dual-booting take a look here:

[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

Feel free to ask questions and drop by even if you don't have a specific question (you can learn a lot just by reading posts from other users).

Good luck!

:)

---

