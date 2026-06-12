---
title: "Boot.ini fail"
date: 2011-01-03
forum: General Help
---

### Post by MarkVS on 2011-01-03
Ok, so I have a computer with one hard drive with both Win XP and Ubuntu 10.10 on it. I am using Grub in the MBR to boot the two. Until today, no worries, both would boot fine. Then out of curiosity I booted the Memtest86+ that is on the Grub menu. It ran for a long time, about 20 min, then I grew bored and shut it down. But when I restarted and booted Win XP, I got this error:

"Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file."

Ok, seems like an easy fix. I boot just fine into Ubuntu (I'm on it now) and looked it up. On many sites it specified that the problem was not with hal.dll but in fact with boot.ini.

Back track in time to when I installed Ubuntu. I was completely ignorant of Linux, and thought that I would use the Windows boot loader (boot.ini) to boot Linux. Obviously, most people use Grub instead and I learned that after I failed at my first Ubuntu installation. Although I did mess with boot.ini a little (dangerous, I know) I restored it to its original state when I was done. And it worked since I was able to boot Win XP for weeks after that.

So now this problem out of the blue. I was not messing with it, and ran nothing that would have messed with it (other than Memtest86+???). So in Ubuntu, I open the Win XP partition and look for the boot.ini to read it. And lo and behold: no boot.ini. Yes, I showed hidden files and still no boot.ini. Crap.

So obviously, the thing to do is load the Win XP disk and create a new one. Except, our computer was not shipped with a Win XP disk, just a recovery disk to set it back to factory standard (which I don't want). So I opened that to look for a boot.ini, and nope, not there. Only thing left to do was to get one offline. So I Googled it, found one, copied it, changed a few things, and saved it:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

This is how I remember saving it when I last looked at it, the numbers are all the same. The only thing I can think of is that somehow Ubuntu changed the partition numbers. Win XP **IS** on sda2, but it was booting before, so I don't know why it wouldn't work now.

I do know this:
Grub works (I can boot Ubuntu)
hal.dll works (I replaced it with the original one from the recovery CD)
boot.ini is for some reason not working with Win XP.

Any help fixing this would be appreciated. I know that this is not a Windows forum, but since I am using Ubuntu (and I think Ubuntu is the problem somehow) I think I would get more help here. Thanks.

---

### Post by cheapie on 2011-01-03
Have you tried multi(0)disk(0)rdisk(0)partition(2)?

---

### Post by elliotn on 2011-01-03
just restore the windows bootloader with the Windows cd then restore grub, problem solved.

---

### Post by MarkVS on 2011-01-03
Ok so I tried the partition 2, and Win XP started (the splash screen with the blue bar) but froze. I think that was because I replaced the hal.dll with the old one, so I am going to replace that now.

---

### Post by MarkVS on 2011-01-03
It worked!
I replaced the hal.dll with the original and booted on partition 2 and I am back in Windows! (Not that I like Windows at all, but it can be useful) Thanks for the help! Still not sure what deleted it and why the partitions were changed, but oh well.

---

