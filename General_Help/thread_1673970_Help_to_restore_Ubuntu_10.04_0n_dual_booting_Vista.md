---
title: "Help to restore Ubuntu 10.04 0n dual booting Vista pc"
date: 2011-01-23
forum: General Help
---

### Post by richardpd on 2011-01-23
Hi
Today I tried as usual to boot into Ubuntu10.04 LL from dual boot screen but for some reason it did not open normal Ubuntu start page instead a page saying boot from CD  opened. I switched off & tried again and somehow receieved an error message saying run chkdsk in Vista.
So I booted in to Vista & ran chkdsk /f but when I tried rebooting into Ubuntu I get to Grub loader page? (This process has taken 3hrs+ this am!).
 
Anyone know what has happened and whether I can get back my Ubuntu? I installed via Wubi originally and a few weeks back I tried to increase disk space for it but that did not seem to work too smoothly but it did leave me with more space in my home folder & with a backup of my folders/files. I haven't checked program files yet on Vista but I hope I still have my Ubuntu files there. 
 
Perhaps I should try a reinstall of Ubuntu10.04 using Wubi again? I will probably do that & see what happens but am grateful for advice if anyone knows & understands this problem & what I should best do about it! Perhaps it is useful to record these issues somewhere so Ubuntu developers can be aware of such issues?
 
Anyway I am grateful for any helpful replies and support-many thanks

---

### Post by ajgreeny on 2011-01-23
I know almost nothing about wubi, but would refer you to the wubi megathread showing in my signature.

It may help you out, and will certainly be more useful than me.

---

### Post by JRV on 2011-01-23
There is a bug in grub that causes problems for a Wubi installation after an update.

This thread explains it:  [http://ubuntuforums.org/showthread.php?t=1663404](http://ubuntuforums.org/showthread.php?t=1663404)

To avoid the problem in the first place, when doing an update uncheck grub-pc.

---

### Post by richardpd on 2011-01-23
Many thanks for your replies.

Well I did a reinstall using Wubi just hoping it would back my files up-but it didn't so they are all lost! 
Oh dear!
I have now to start from scratch with Ubuntu 10.04 again & one of the first things I want to do is find the best way to back this Ubuntu up! This is about the 3rd time I have had this sort of an issue & I want to make a backup from the outset now in case it happens again (which seems probable!).

Best wishes

---

### Post by Rubi1200 on 2011-01-23
If you had read and followed the instructions in the thread ajgreeny mentioned or the other information that JRV pointed to you might have saved your data.

Please refer to the Wubi Megathread. There are known issues with Wubi installs at the moment. You need to lock the grub-pc and grub-common packages to prevent this happening (see main post just after Permanent Fix on how to do this).

If you want to do a quick and dirty backup then simply copy the root.disk to another medium to use in case things go wrong again.

---

### Post by richardpd on 2011-01-27
Hi
Well things have gone wrong again! 
This morning I ran update manager-218 packages & 15mins to install but it took ages to install and halfway through it froze. I shut down and when I restart I get to the login page but the mouse & keyboard do not work & I cannot get to start Ubuntu10.04.
 
I am not sure how to recover from this! Yesterday I bought a removable HD & had copied contents of home folder (as I had started rentering my data again after the initial crash & I wanted a back up ready) to it. I tried to install sbackup but had a problem with Software Centre & terminal said error no headers which I cleared running sudo apt-get update twice. I was not able to copy File System as it did not allow copy for many files so I cancelled that and had hoped to use sbackup but didn't get a chance (before this next freeze/crash?).
 
I'm not sure how to restore Ubuntu10.04 now- I will check out the link given in this thread & see if that might help. Otherwise I maybe forced to do a reinstall again and I am not very pleased to be experiencing this! I had been running Ubuntu smoothly but seem to have crashed badly now! I want to get back to using my computer & not having problems just running it!!
 
I am grateful for any helpful advice, thanks & good wishes

---

### Post by richardpd on 2011-01-27
Hi Rubi1200
I have just looked at WUBI Megathread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
 
I will have to look it over some more to try & understand it better.
Possibly I should try & uninstall Ubuntu10.04 and reinstall 'normally' and not with WUBI?
I have tried Ubuntu with WUBI & like Ubuntu (except for the current problems I have had! so would it be better to try an install without WUBI? except that WUBI install was a simple install procedure).
 
Anyway thanks for your link & I now have to figure out what best to do get Ubuntu10.04 working again for me. 
(I forgot to say in my previous post I tried booting in linux safe mode and got to a flashing cursor but did not know what to do next - so couldn't carry on!!).
 
As always any advice gratefully received-thanks!

---

### Post by richardpd on 2011-01-28
I am now trying to install 10.10 MMeerkat from USB stick & am having problems knowing how to allocate drive space.
I am posting this from the usb MMeerkat install but want to install to HD  but the option to allocate a new partition big enough for me (around 40GB) is not easy to discern and create.....The other option would be to use my old PartitionMagic (v7) cd to reformat Vista disc prior to MM install! Simples?! NO-not simples!!). Please Ubuntu make it simples for the future?!
As ever I press on!

Best wishes all

---

