---
title: "GRUB Error 15"
date: 2010-01-03
forum: General Help
---

### Post by ahmedm989 on 2010-01-03
Hello, this is my first time posting here. I upgraded my windows partition to Windows 7 and now I can't boot into ubuntu because I guess something happened to the bootloader. I tried a lot of things and read topics online but I still have not been able to get it to boot.

I tried editing in GRUB to see which hard drive mine was on, and unlike what I've seen online (hd0 or similar things), mine was called fd0. I don't know if that means anything or not.

Thanks in advance to anyone who helps.

---

### Post by Brandon Williams on 2010-01-03
When you write 'I tried editing in GRUB', I assume that means that you have a Grub command prompt, and that you've tried using it to boot into the installed system. This is a little bit harder with grub2 than it is with grub-legacy, but just a little.

I just posted a response with the information to get you started [here](http://ubuntuforums.org/showthread.php?p=8605349#post8605349).

---

### Post by Leppie on 2010-01-03
i think you checked the grub on a live media (fd0 shows when using a livecd for example).
if you have only 1 linux partition and you know which one it is, you can use the following commands to install grub2 to your mbr of your first hard drive:
```
$sudo mount /dev/sdaX /mnt ##change sdaX to your linux partition
$sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by ahmedm989 on 2010-01-04
> **Leppie said:**
> i think you checked the grub on a live media (fd0 shows when using a livecd for example).
if you have only 1 linux partition and you know which one it is, you can use the following commands to install grub2 to your mbr of your first hard drive:
```
$sudo mount /dev/sdaX /mnt ##change sdaX to your linux partition
$sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

I tried that, and it came up with an error:

> grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly


Brandon, yes that's what I meant, I tried booting into it, but wouldn't work and always came up with the same error. I will take a look at that link. Thanks.

---

### Post by ahmedm989 on 2010-01-04
I used the steps for the "simplest" solution [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"). They were the same as the steps described above, before I had used "/dev/sda6" for the second line but this time I just changed it to sda according to that page. It succeeded and I rebooted. Now I'm on a command prompt page just saying "SH:/grub:", something like that, and I can use TAB to see a list of commands. The page is title GRUB 1.97 Beta or something similar. I don't know what to do now on this page or if I should try another step maybe.

---

### Post by Leppie on 2010-01-04
The first command is to mount your linux **_partition_**, hence _**sdaX**_.
The second command is to install grub to the _**mbr**_, hence **_sda_**

---

### Post by ahmedm989 on 2010-01-04
> **Leppie said:**
> The first command is to mount your linux **_partition_**, hence _**sdaX**_.
The second command is to install grub to the _**mbr**_, hence **_sda_**

I see, I see. Makes sense. OK, and what about the step after at the command prompt? Do you have any idea? :confused:

---

### Post by ahmedm989 on 2010-01-04
I used the last method on that page (the CHROOT) and now I'm typing this message from my ubuntu system, so things work. Another problem came up, which I hope is simpler. Now from the GRUB menu at start-up there is no windows partition showing. Also does anyone know how to edit the options on that menu to say what I want it to say?

Thanks.

---

### Post by Leppie on 2010-01-04
> **ahmedm989 said:**
> OK, and what about the step after at the command prompt? Do you have any idea? :confused:
sorry, don't understand what you mean...

---

### Post by Leppie on 2010-01-04
> **ahmedm989 said:**
> I used the last method on that page (the CHROOT) and now I'm typing this message from my ubuntu system, so things work. Another problem came up, which I hope is simpler. Now from the GRUB menu at start-up there is no windows partition showing. Also does anyone know how to edit the options on that menu to say what I want it to say?

Thanks.
what are you exactly trying to achieve?

---

### Post by ahmedm989 on 2010-01-04
OK, what I meant before is now irrelevant, but what I need to do now is to see the option to boot into Windows in the GRUB menu. It only lists Linux now.

---

### Post by Leppie on 2010-01-04
regenerate the grub.cfg:
```
$sudo update-grub
```

this should trigger the 30_os-prober script which usually detects windows installations automatically.

---

### Post by ahmedm989 on 2010-01-04
I tried that just now but it didn't help.

---

### Post by Brandon Williams on 2010-01-06
Is os-prober installed on your system?
```
$ dpkg -l os-prober
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  os-prober      1.35           utility to detect other OSes on a set of dri
```

If it is not, then 'sudo aptitude install os-prober' and then 'sudo update-grub'. If os-prober _is_ installed, then it's likely that something has gone wrong with the Windows installation.

---

### Post by Leppie on 2010-01-06
> **ahmedm989 said:**
> I tried that just now but it didn't help.
what does this mean? did you get error messages? did it process normally and the entry is in grub.cfg but you still don't have the entry in the menu when booting?

---

### Post by ahmedm989 on 2010-01-07
It worked!

I repeated the steps on [this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") page (the CHROOT method) and then tried what you recommended, Brandon. I restarted but my Windows partition was still not showing up. I tried installing GRUB 2 using this command:

sudo grub-install /dev/sdX

I'm not sure if that was what did it or not, but I decided to check my menu.lst file for grub and I simply edited the last two entries which were labeled Windows Vista Loader, and changed that to Windows 7 for my new system. That seemed to have done something. I don't know if that was all there was to it, but I'm happy now with the results. I then deleted all the extra entries and now my system works fine and I have a nice grub menu, with both operating systems working perfectly.

Thanks for all your help Brandon and Leppie! :)

By the way, am I supposed to rename the thread with a SOLVED next to the name? If so, how do I do that on this forum?

---

