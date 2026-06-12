---
title: "Please help!! Ubuntu won't boot! (I'm scared..)"
date: 2011-06-01
forum: General Help
---

### Post by Goosemonkey on 2011-06-01
I am so scared right now.. I just started up my computer, and it wouldn't get past the Ubuntu logo... I've tried everything, and I'm not very good with ubuntu, so can anyone help me?

I have a dual boot configuration, with ubuntu 11.04 and vista.. And now VISTA doesn't boot off of the loader :( !

I have an unusable computer, and have no idea of how to fix it.. 

I literally made an account on here just to ask this. Someone PLEASE help me! I'm so upset.. I think there might be a problem with the swap, so if anyone can help, I will be forever grateful :)

---

### Post by Goosemonkey on 2011-06-01
Bump.. Please??

---

### Post by jerrrys on 2011-06-01
has it worked at all since you installed?

---

### Post by Rasa1111 on 2011-06-01
the bad news is you've deleted all your data.

the good news is im only kidding. lol :P
sorry, im in a stupid mood.. O_o

Someone who can help you fix it will be by Im sure,
but bumping your own threads within a few minutes of each post is generally frowned upon. 

Patience young grasshopper...
a solution will come... lol :)

Good luck.

---

### Post by Goosemonkey on 2011-06-01
> **jerrrys said:**
> has it worked at all since you installed?

Yes, it was working for a few days.. And I didn't even so anything before it stopped working. And sorry about the soon bump, I'm just really scared.

---

### Post by baarn on 2011-06-01
what was your last change to your computer between ubuntu working and ubuntu no longer working? (any updates/upgrades)
its really hard to guess what the problem might be from your info.

could be nearly anything... because vista wont boot either i would say there is some grub2 error.
i am not very firm in using grub2 only use grub on my experimental-box so i dont know how to tell it to go verbose while booting (which might show the error)

---

### Post by jerrrys on 2011-06-01
best way out is to forget about about ubuntu for the moment and use your vista restore disk.

---

### Post by zealibib slaughter on 2011-06-01
see if you can boot into recovery mode by pressing esc when grub loads.  If you can then drop to root shell and see if any errors are posted.

---

### Post by Goosemonkey on 2011-06-01
> **jerrrys said:**
> best way out is to forget about about ubuntu for the moment and use your vista restore disk.

The problem is that the Vista restore is in a separate partition, and I can't access any commands like the F-keys - it just goes straight to grub.

---

### Post by idoitprone on 2011-06-01
or we can tell the op to do the a list of commands to mark off a list of things that i may do.dododododo

get live cd

```
sudo fdisk -l

```
try this boot script

```
http://sourceforge.net/projects/bootinfoscript/

```
maybe ```
sudo blkid
```

can u access your files through a live cd?

---

### Post by jerrrys on 2011-06-01
ok, thats good.  you have a grub boot screen right?

---

### Post by Goosemonkey on 2011-06-01
> **zealibib slaughter said:**
> see if you can boot into recovery mode by pressing esc when grub loads.  If you can then drop to root shell and see if any errors are posted.

Right after I entered recovery mode, for a split second it said something like VGA-792 is deprecated.. Does that help?

---

### Post by Goosemonkey on 2011-06-01
> **jerrrys said:**
> ok, thats good.  you have a grub boot screen right?

Yes.

---

### Post by zealibib slaughter on 2011-06-01
> **Goosemonkey said:**
> Right after I entered recovery mode, for a split second it said something like VGA-792 is deprecated.. Does that help?
 
maybe here is a bug report tied to this [https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/495436](https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/495436)
but it doesn't say that it will prevent bootup.  Try to start an x session while in recovery mode and see if any errors come up.  Should be able to type startx and go from there.

---

### Post by glene77is on 2011-06-01
> **baarn said:**
> what was your last change to your computer between ubuntu working and ubuntu no longer working? (any updates/upgrades)
its really hard to guess what the problem might be from your info.

could be nearly anything... because vista wont boot either i would say there is some grub2 error.
i am not very firm in using grub2 only use grub on my experimental-box so i dont know how to tell it to go verbose while booting (which might show the error)
-----------------------------------------------------------------------------------------------------------------------

Baarn,
Just saw the suggestion to use the Vista Restore Disk.     
Always a good choice, although it sounds drastic.

------------------------------------------------------------------------------------------------------------------------
If you have a grub screen,
... enter 'c' 
... enter my code for Ubuntu 10.10 Bare Bones Bootup as copied from my grub.cfg :
# menuentry "---< -U- >--- Ubuntu 10.10 (hd0,5) Bare-Bones-Bootup .........."
# {
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
# }
endcode.
Change my partition from "5" to yours, assuming that the Ubuntu 11.04 was completed, of course.
------------------------------------------------------------------------------------------------------------------------


My early experience with Ubuntu 11.04 was not good, no booting.
So, I simply returned to the Ubuntu 10.10 which was proven stable.   

On the forums, it was revealed that if U 10.04 was upgrated to U 10.10, 
and then updated again to U 11.04 that booting could be problematic !
So, 
My decision was 
(1) to revert to U 10.10 
(2) wait a six months for U 11.04 to settle down. 
I suggest, 
Obtain Live-CD of Parted-Magic and Puppy Linux 5.25 from OSDisc.com.
Both are designed to work 'forever' from Live-CD, very handy.  

########################################################################################
Here is the general procedure I have used several times in Recovery involving M$ XP. 
(1) Used Parted-Magic Live-CD to copy out 'created data'  to a USB flash thumb-drive,
(2) then used the M$ Restore Disk to start over.
(3) Used Parted-Magic Live-CD to shrink the M$ partition down (maybe to 10 GB) ,
(4) Used Parted-Magic Live-CD to create a Linux Swap of 1 GB at the far right of the HD.
(5) Used Parted-Magic Live-CD to create an Extended partition in the middle.
(6) Used Parted-Magic Live-CD to create 
...a) one M$ XP ntfs partition for original 'created data'.
...b) several 10 GB partitions for several Linux OS install.
(7) Used the Ubuntu 10.10 Live-CD 
... a) to install  the  Ubuntu OS  
... b) to install Grub2 files and fix MBR.
(8) Lastly, used Parted-Magic Live-CD to copy the 'created data' from USB back into the HD. 
###########################################################################################

HTH

---

### Post by Goosemonkey on 2011-06-01
> **glene77is said:**
> -----------------------------------------------------------------------------------------------------------------------

Baarn,
Just saw the suggestion to use the Vista Restore Disk.     
Always a good choice, although it sounds drastic.

------------------------------------------------------------------------------------------------------------------------
If you have a grub screen,
... enter 'c' 
... enter my code for Ubuntu 10.10 Bare Bones Bootup as copied from my grub.cfg :
# menuentry "---< -U- >--- Ubuntu 10.10 (hd0,5) Bare-Bones-Bootup .........."
# {
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
# }
endcode.
Change my partition from "5" to yours, assuming that the Ubuntu 11.04 was completed, of course.
------------------------------------------------------------------------------------------------------------------------


My early experience with Ubuntu 11.04 was not good, no booting.
So, I simply returned to the Ubuntu 10.10 which was proven stable.   

On the forums, it was revealed that if U 10.04 was upgrated to U 10.10, 
and then updated again to U 11.04 that booting could be problematic !
So, 
My decision was 
(1) to revert to U 10.10 
(2) wait a six months for U 11.04 to settle down. 
I suggest, 
Obtain Live-CD of Parted-Magic and Puppy Linux 5.25 from OSDisc.com.
Both are designed to work 'forever' from Live-CD, very handy.  

########################################################################################
Here is the general procedure I have used several times in Recovery involving M$ XP. 
(1) Used Parted-Magic Live-CD to copy out 'created data'  to a USB flash thumb-drive,
(2) then used the M$ Restore Disk to start over.
(3) Used Parted-Magic Live-CD to shrink the M$ partition down (maybe to 10 GB) ,
(4) Used Parted-Magic Live-CD to create a Linux Swap of 1 GB at the far right of the HD.
(5) Used Parted-Magic Live-CD to create an Extended partition in the middle.
(6) Used Parted-Magic Live-CD to create 
...a) one M$ XP ntfs partition for original 'created data'.
...b) several 10 GB partitions for several Linux OS install.
(7) Used the Ubuntu 10.10 Live-CD 
... a) to install  the  Ubuntu OS  
... b) to install Grub2 files and fix MBR.
(8) Lastly, used Parted-Magic Live-CD to copy the 'created data' from USB back into the HD. 
###########################################################################################

HTH

What? I really don't know too much about linux.

---

### Post by Goosemonkey on 2011-06-01
Bump.. I tried deleting the swap partition from the live cd and it still doesn't work.

---

### Post by zealibib slaughter on 2011-06-01
i dont think its swap related but maybe grub since windows doesnt boot.  have you tried to reinstall grub from the recovery menu? if not i would try that first. Also if you can reach a terminal by ctrl alt f1 when ubuntu boots then maybe there will be an error that can shed some light on things.

---

### Post by Rasa1111 on 2011-06-01
with all this toying around...
it may be wise to insert a LiveCD and backup whatever files you might need first. 
from both OS's. 
If someone tells you to do something, and it goes wrong or you misinterpret something.
 .. all your data is just a few clicks away from being toast. 
Specially if you don't know what you're doing.

good luck

---

### Post by zealibib slaughter on 2011-06-01
> **Rasa1111 said:**
> with all this toying around...
it may be wise to insert a LiveCD and backup whatever files you might need first. 
from both OS's. 
If someone tells you to do something, and it goes wrong or you misinterpret something.
 .. all your data is just a few clicks away from being toast. 
Specially if you don't know what you're doing.

good luck

i couldnt agree more.  Back up first then we will try to fix things.

---

### Post by Dustin2128 on 2011-06-01
hm, just a thought, get on the livecd and go to your ubuntu partition, then go to /boot/grub/grub.cfg and post the contents of that file. Something that got me when I was installing arch was that grub.cfg generated with the wrong hard drive name, hence I couldn't boot.

---

### Post by cachiporokas on 2011-06-02
I'm having the same problem, everything was fine until last Monday when the update manager pop up with new updates, after updating the system i continued with my work and shutdown, but now when i start the computer it stucks in the purple screen with the ubuntu logo. I think it has something to do with the graphic card and xserver because the only way to acces my account is in recovery mode under the failsafex option, also, two of the latest updates have to do with xserver.
Any idea what's happening?

---

### Post by mastablasta on 2011-06-02
the only way to see what happens at boot and why it doesn't boot is to use the bootinfoscript and then post the results .txt here in the code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
this will tell us what is happening at boot and hopfully why it's not booting. 
 
Though i suspect it has something to do with Wubi. Did you install Ubuntu from Windows Vista using wubi installer? if not then again the bootinfoscript should say what is wrong at boot.

---

