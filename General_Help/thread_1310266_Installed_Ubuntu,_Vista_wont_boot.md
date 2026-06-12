---
title: "Installed Ubuntu, Vista wont boot"
date: 2009-11-01
forum: General Help
---

### Post by taylor1234 on 2009-11-01
I have windows vista and I installed Ubuntu. Now when I boot up it loads the grub which has these choices to boot from:
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic(Recovery mode)
Memory test(memtest86+)
Memory test(memtest86+,serial console 115200)
Windows Vista (loader)(on/dev/sda1)
Windows Vista (loader)(on/dev/sda2)

When I try to boot Vista it says microsoft corporation at the bottom of the screen then the screen flashes and the grub loads again.

Please help me.

---

### Post by taylor1234 on 2009-11-01
Can I uninstall ubuntu and see if windows will still run or is there anyway i can get it to work?

---

### Post by sliketymo on 2009-11-01
> **taylor1234 said:**
> I have windows vista and I installed Ubuntu. Now when I boot up it loads the grub which has these choices to boot from:
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic(Recovery mode)
Memory test(memtest86+)
Memory test(memtest86+,serial console 115200)
Windows Vista (loader)(on/dev/sda1)
Windows Vista (loader)(on/dev/sda2)

When I try to boot Vista it says microsoft corporation at the bottom of the screen then the screen flashes and the grub loads again.

Please help me.

9.1 is now using Grub 2.Here is some good info.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by RJ12 on 2009-11-01
If you uninstall Ubuntu you will delete grub and make it worse and will have to restore your MBR (Its a program that tells the computer where to start booting from). So far this is all I know but I guess this can be served as a bump also.

Oh did you resize Vista's Partiton without using the Vista Disc Editor and did you defrag before you installed also


*Hopes the problem dosent get worse*

---

### Post by taylor1234 on 2009-11-01
I defraged a day before I resized the partition.

---

### Post by taylor1234 on 2009-11-01
[B]What about this i found in another thread, link: [http://ubuntuforums.org/showthread.php?t=373074&page=5](http://ubuntuforums.org/showthread.php?t=373074&page=5)


e: Vista doesn't boot after Ubuntu install[/B] 			 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **skydog2004** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=4041982#post4041982") 				
 				[I]I found a solution that worked great for me. I just installed gutsy on a new vaio vgn-nr160e laptop, and when I tried to reboot into vista it hung up at crcdisk.sys. (safe boot mode). 
 
After a bit of cursing at the boys in redmond, a bit of googling, more cursing...

I rebooted back into linux and downloaded ntfsprogs and ran ntfsfix on vista partition. It resets journal and forces a file system check next time windows boots. 
no problems since. 
I can hibernate in both OS's and life is good...[/I]
 			 		 	 	 
skydog2004 - You have made my life complete.

sudo apt-get install ntfsprogs
sudo umount /dev/sda2 (or whatever your vista drive is - if your not sure use gparted to bring up a graphical image of your drive partitions and then close)
sudo ntfsfix /dev/sda2

reboot selecting the recovery partition at the Grub stage (mine was the first windows option on the list)
Allow windows to attempt to fix itself
After a few minutes the program will ask you to reboot (or will do so automatically)
Reboot Vista (using the normal windows option)

And there you go. Proof for all your friends that it is possible to dual boot. Now you can leave the Vista partition alone and get on with your linux life!

---

### Post by taylor1234 on 2009-11-01
[http://desktoplinux.com/articles/AT2094892904.html](http://desktoplinux.com/articles/AT2094892904.html)

I found this but I don't know what exactly to type in the terminal. About half way down down the page it tells you to use the sudo command but i dont know what to type.

---

