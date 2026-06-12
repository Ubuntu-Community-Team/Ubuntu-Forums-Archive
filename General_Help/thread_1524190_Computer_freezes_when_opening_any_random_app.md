---
title: "Computer freezes when opening any random app"
date: 2010-07-04
forum: General Help
---

### Post by Aralhach on 2010-07-04
Hey folks!! I installed Ubuntu Lucid on my computer a few weeks ago (fresh install, formatted).  I'm very happy with the speed, etc.  But recently I've been having some problems.

This is about the 4th time it happens.  When I randomly open a program, sometimes the whole computer will just freeze.  I can't change to a terminal window with Ctrl-Alt-F1,2,3,4 or anything.  I can only press the Reset button on the computer case.  This is frustrating because I already lost ALL my firefox settings and addons and I don't want anything like this to keep on happening.  Any ideas? :)

I'd really appreciate it.

EDIT: [SOLVED]
Well.... a couple days ago I managed to fix the problem.

The problem was: *drumroll* the POWER SOURCE.

Apparently the voltage was having little drops and this caused all the hardware to freeze. This caused the system operation to be WORSE after I bought the new graphics card (since it was bigger and needed more power). I bought a new powersource and installed it and it seems everything is alright now. I didn't post before because I wanted to make sure this time. I hope anyone with this problem in the future can fix it more easily than I did.

Thanks a lot everybody for your ideas!
Aralhach

---

### Post by Tech2077 on 2010-07-04
Check the iso you used, the first time I installed ubuntu something like this happened, it was a problem with the cd, so check your disk, burn another, maybe on a dvd to make sure the size is correct, if it still has problems, check the md5 sum of your iso.

---

### Post by lovinglinux on 2010-07-05
Not a solution for your problem, but I would recommend using [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109/) extension to keep regular backups of your Firefox profile. Profiles can become corrupted for several reasons, so having backups will save you a lot of trouble.

---

### Post by Aralhach on 2010-07-06
Well, I checked the ISO, and the MD5 hash is just fine.

And I don't think the installation itself caused the problem since I just started having these last week.  I think some update may have broken my system somehow.  It happens when I open LOTS of programs at the same time....

Is there a log somewhere I can look at and see what's going wrong?

And lovinglinux.... Thanks a lot for the suggestion! I appreciate it and will start using FEBE today.. XD

Thank you all! (and if anyone has ANY ideas, I'd appreciate them a lot)

---

### Post by BikeHelmet on 2010-07-06
The first thing I'd do is check for hardware instability.

Memtest... maybe check your HDD with a bootable diagnostic CD from the manufacturer... and whatever checks CPU stability?

I had two computers with freezing issues, but one was a bad stick of RAM, and the other was an HDD slowly accumulating bad sectors.

---

### Post by sudokodo on 2010-07-06
Ibet you are using USB mouse and/or keyboard ... test problem using PS/2 mouse and keyboard ... USB sometimes can't wake up after sleep modes ... PS/2 hardware doesn't have sleep modes

sudokodo

---

### Post by Aralhach on 2010-07-08
@BikeHelmet:
I ran the memtest and my RAM came through fine.  The HD bad sector theory seems to make sense, but do you know about a good program that could check my HD for me?

@Sudokodo:
Thank you very much for your idea, and I'll keep it in mind for the future.  Unfortunately, my mouse and keyboard are both PS/2.

Thanks a lot! :)

---

### Post by 3rdalbum on 2010-07-08
> **Aralhach said:**
> @BikeHelmet:
I ran the memtest and my RAM came through fine.

Run it overnight and see if it finds any errors by the morning. This definitely sounds like a RAM problem to me. If Memtest doesn't find anything, then try installing the Phoronix Test Suite and run the memory benchmarks - if they cause a freeze then your memory is at fault.

---

### Post by Aralhach on 2010-07-08
I suspect it's not a RAM problem.  I booted into Windows, to play Hitman, and I loaded the game and it quickly locked up.  I took out one RAM module, and the same thing happened.  I took the other one out (I only have 2) and the same thing happened (there's only 2 sockets).  So yeah..... this probably IS the RAM module...

I did the memtest and there were no errors in 1 pass.  Is one pass enough? I thought that one pass would effectively test all registers and everything should be fine... or are we talking about bad HD sectors?  How could I check for this?

I really appreciate the help! :'(

---

### Post by Furry_Fighter_20x66 on 2010-07-09
Your ram check should run at least more then one pass. Like stated above, you should run the memtest all night and check it in the morning, or whatever works for you.
It is very important these days with computers that your ram in the system is good. There is a lot of disk caching to ram with modern Linux distros and if you have flaky ram it will likely start to flip bits leading to file errors.

There is one more possibility that I can think of. Disable ACPI during boot and see if it stabilizes your system. I had Compaq tower here that would baffle me with frequent freezing and lockups for no reason until I did this. It would be a year later I found out the reason. Foxconn was contracted to supply the motherboards and this was one of the affected boards. (You can read about all that here: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249)). Once I disabled it during boot, the system ran flawlessly evermore. 

By disabling ACPI you will lose your ability to suspend and hibernate as a result though. I am also not sure how to pass boot commands onto the kernel since the latest version of Ubuntu unless you add them to grub or something. Perhaps someone can help you figure that one out.

---

### Post by Aralhach on 2010-07-11
I ran the memtest86 for 5 hours, with 3 or 4 passes, and there were no errors.  I took one RAM module out, and it still froze.  I took out the other one, and the same thing happened.  I'm quite sure now that the RAM is not the problem.

I also ran a CHKDSK in Windows XP (the other OS I have installed) for all partitions (except the Linux one obviously).  I think it found some errors as it corrected entries in some file.  I happily thought that my problem had been solved but no.  I ran CHKDSK 2 more times and it found nothing. 

Your ACPI idea sounds interesting.  I don't really use Suspend OR Hibernate, so I wouldn't mind... but I don't get what you said about how to pass boot commands to the kernel.  Why would I need to do that?

Again, I appreciate all your help very much! :)

PS: On a wild thought, could it be my graphics card? I ran a GPU testbench with PC Wizard and everything went smoothly... I don't know.

---

### Post by Furry_Fighter_20x66 on 2010-07-12
Hi Aralhach:

The easiest way to temporarily disable the ACPI from running is to do it at boot time before the kernel can enable the module that communicates with the motherboard.

To do this we have to access a secret menu at boot time, much like the F8 key in Windows. For your sake I would advice you to write these instructions down.

First, reboot the computer. As the computer starts back up and finishes the BIOS check screen, press and hold the SHIFT key. I don't think it makes a difference but I used the left shift key. If you get a menu right away, then great it worked. Proceed to the next step. If Ubuntu starts to boot then press the CTRL-ALT-DELETE sequence before it gets too far into the boot sequence.

On this menu is a list of kernels we can work with. For this, all we need to do is use the one already selected. Press the 'e' key.

A new menu appears allowing us to modify the boot commands. In here I will need you to scroll down to the line that reads something like...
> linux /boot/vmlinuz-blahblabblah root=UUIDmoreblahs ro quiet splash
Note there may be a few other things in there too. No worries. Go to the end of that line and add the following 'acpi=off'. So now it will read something like...
> ... quiet splash acpi=off
note the very important space between splash and acpi=off. This must be included.

Now press the CTRL-X key combination to boot with this change. Now this change will only last this one time. Once you reboot it will be gone. But now you can work with the computer and see if it starts to respond better without crashing. If you find this solves things then write back and I will help you to set it so the change is permanent.

---

### Post by Aralhach on 2010-07-19
Hi... sorry for taking so long to reply, but I got quite busy and now have a little time to work on this thing.  I think I discovered the problem.

Bad GPU card.  I noticed it tended to freeze when I opened lots of programs, or moved windows around, or when I started a game (I couldn't play any games).  Anyway, I booted into Windows and ran this FurMark thing that's like a benchmark utility and I put stability test.  After some time, it froze.  I just went down this morning and got a new GPU.  I booted up a game and it worked perfectly (and faster too, I think I got a better card :P).  Anyway, I installed the new drivers in Windows, and updated the DirectX stuff, and booted into Ubuntu, no problem.  I ran a "sudo aptitude update" just for kicks and full of joy, turned the computer off.

Now, when I restart, and select Ubuntu, the splash screen appears, but when the screen goes black before the user select screen appears, it just stays black and I can't do anything.  Any ideas? I can boot into Windows fine, but not Ubuntu.

I appreciate all your help! :)

@Furry_Fighter_20x66: Thank you VERY MUCH for all your help, and I will keep your ideas in mind if I ever run into this problem in the future.  Thanks a lot! :D

EDIT:  I don't know what happened.. I can log in now without problems.... But my freezing problem has returned after several hours of correct operation.... I'll try to change the PCI-E port....

---

### Post by Aralhach on 2010-07-25
Well.... a couple days ago I managed to fix the problem.

The problem was: *drumroll* the POWER SOURCE.

Apparently the voltage was having little drops and this caused all the hardware to freeze.  This caused the system operation to be WORSE after I bought the new graphics card (since it was bigger and needed more power).  I bought a new powersource and installed it and it seems everything is alright now.  I didn't post before because I wanted to make sure this time.  I'll now tag this as SOLVED and edit the main post, so anyone with this problem in the future can fix it more easily than I did.

Thanks a lot everybody for your ideas!
Aralhach

---

