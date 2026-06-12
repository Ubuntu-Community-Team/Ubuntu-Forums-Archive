---
title: "Can't boot UNR 10.10 on Toshiba NB305"
date: 2011-02-15
forum: General Help
---

### Post by dasBob on 2011-02-15
Please help. I'm new to Ubuntu. I resurrected an old laptop with 10.10 and REALLY like it so I thought I try a dual boot system with Win7 on my Toshiba NB305 (2Gb ram, 250Mb HD). 

I almost gave up after waiting at least 5 minutes to boot and an additional 10 minutes to get it to load a trial run rather than install. After trying a few more times, I downloaded a couple of hours worth of updates and things looked good! It booted off the USB in just under 2 minutes and only took about 5 minutes to load the trial version. The Fn brightness and volume keys even worked. I figured it would boot fast from the HD.

S0 I decided to install it...

The computer will not boot. I get an error to the effect: ALERT! /dev/disk/by-uuid/xxxxx-xxxx-xxx-xxx does not exist.

I found instructions somewhere on this forum written by an ubuntu developer that worked up to a point.

I ran blkid and found that ubuntu is on sda3, ext4 and that my uuid that ubuntu can't find is 4179236e-2395-46e2-ba6d-b34a1531d929

I ran:
 sudo mkdir /mnt/target
sudo mount -t ext4/dev/sda3 /mnt/target

so far so good.

Then the instruction was to modify the "# kopt=root" line in /mnt/target/boot/grub/menu.lst

I assumed I was supposed to enter:

sudo gedit /mnt/target/boot/grub/menu.lst

I guess not, because the computer can't find that directory or file

Am I using instructions for an old version?

What should I do for unr 10.10?

Thanks in advance for any help!

---

### Post by Hakunka-Matata on 2011-02-15
Yes, the insructions were for an earlier release.  The bootloader has changed, menu.lst no longer exists.  rather than try to give you specific commands, maybe you'd like to look at the Grub2 description in the following link.  [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by dasBob on 2011-02-15
Thank you, Hakunka-Matata! This information looks like it should have just what I need. I'll read it this weekend when I get home from the 72 hour stint at work I'm off to now!

Thanks again.

---

### Post by dasBob on 2011-02-18
Well, I read through the document and tried the fixes but without success. The only thing that happened is that now I'm booting faster from the USB and going directly into UNR without having to wait forever for the trial version to load.

I'm not a programmer by trade and haven't even done much programming since writing programs in Fortran on punch cards in the late '60s!

I'm not afraid to muck around with this and have a general understanding of what I'm trying to do but I'm getting stuck in the details.

If someone would please spell out the specific steps I need to follow I will be extremely grateful.

Thank you in advance.

---

### Post by Hakunka-Matata on 2011-02-18
You might want to start a new thread in "absolute beginner talk" Forum subcategory.  I say this because usually when someone has a grub problem one of several members show up right away that really know their stuff.  They are not showing up here though. I would also suggest you name it something like "dual boot Ubuntu 10.10 - Windows 7 grub problems"

[http://ubuntuforums.org/forumdisplay.php?f=326]("http://ubuntuforums.org/forumdisplay.php?f=326") That's the link to open a thread in Absolute Beginner Talk.  I suspect you will quickly find several very knowledgeable helpers. 

[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")  That's the link you should look at, it might be enough for you to solve your problem, it's by on of those users who is very good with Grub.  

If you choose to start a new thread, I'll find you there, and you should mark this thread Solved to close it if you start a new thread.  **_Thread Tools_** Upper right hand side page

Good luck

---

### Post by Hakunka-Matata on 2011-02-18
Several people who really know their stuff are 'drs305', 'oldfred', 'willee nillee'  and i'm guessing they don't watch in general help as much as in 'installation problems' or 'absolute beginner talk'

---

### Post by Hakunka-Matata on 2011-02-18
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

You will most likely be asked to download and run the 'bootinfoscript' script (Linux speak, batch file) and supply the results when and if you get help from them.  I'd suggest you run it anyway, and look at the results, they might help you understand what is not working in your setup.

---

### Post by dasBob on 2011-02-19
Thanks a lot, H-M. I'll try your suggestions. Very appreciative regards.

---

### Post by dasBob on 2011-02-20
In case anyone has been following this thread, I have solved my problem and hope my solution will be of help to others.

After yet another removal/installation I tried booting while holding down the <SHIFT> key, being under the impression that would get me into a grub menu where I could try the editing required I thought was required. Lo and behold, it booted directly into Ubuntu, albeit rather slowly. I figured that was OK and  I could live with holding down the <SHIFT> key while booting.

Feeling confident, i thought I'd try to solve the Toshiba NB305 sleep issue (yes, this relates to the original boot issue). I found a suggestion to modify

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off" and updated grub and rebooted.

Well, before I could even get my finger to the <SHIFT> key, the boot was well under way. It now boots in about 20-25 seconds and shuts down in 1-2 seconds!

As far as I am concerned, this particular problem is solved. Thanks again for the help and encouragement. What a great forum! :P

---

