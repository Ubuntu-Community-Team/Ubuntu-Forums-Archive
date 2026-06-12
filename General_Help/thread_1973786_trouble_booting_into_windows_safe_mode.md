---
title: "trouble booting into windows safe mode"
date: 2012-05-05
forum: General Help
---

### Post by GreggC on 2012-05-05
This maybe a dumb question, but I don't know how to boot into windows safe mode from Grub.
I have a triboot configuration 11.10, 10.04 and vista (all 64 bit). I had to install a new graphics card after the old one died. When I try to boot into Vista, the computer reboots. I assume Vista is trying to reboot into safe mode. Vista will not support the new graphics card w/o installing the drivers (Sapphire HD6870).

I had no problems installing the drivers in 10.04 (other than working on a fuzzy screen at first) and 11.10 booted w/o any problems.

I'm assuming Vista was booting OK, prior to installing the new graphics card, but I have not booted into Vista for a couple of months.

Thanks in advance!

---

### Post by plucky on 2012-05-05
> **GreggC said:**
> This maybe a dumb question, but I don't know how to boot into windows safe mode from Grub.
I have a triboot configuration 11.10, 10.04 and vista (all 64 bit). I had to install a new graphics card after the old one died. When I try to boot into Vista, the computer reboots. I assume Vista is trying to reboot into safe mode. Vista will not support the new graphics card w/o installing the drivers (Sapphire HD6870).

I had no problems installing the drivers in 10.04 (other than working on a fuzzy screen at first) and 11.10 booted w/o any problems.

I'm assuming Vista was booting OK, prior to installing the new graphics card, but I have not booted into Vista for a couple of months.

Thanks in advance!

Select Windows in grub and tap on F8 key will bring up the Microsoft Menu in which you can select Safe Mode.

That works for XP.

Good Luck

---

### Post by GreggC on 2012-05-05
Thanks for the quick reply. F8 did not work - I tried it several times. The box still rebooted and it was back into Grub.

---

### Post by kdane4 on 2012-05-05
Hello, 

What if you tap the F8 key multiple times as soon as you select windows? Maybe it will take you to the advanced boot options screen. Please do tap F8 ***immediately*** as soon as you select windows.

---

### Post by GreggC on 2012-05-05
I tried it several times with no luck. - I'm pretty sure I pressed F8 quick enough for it to work. I can get an experienced video gamer with faster reflexes than I have to give it try ;-) - Windows - ugh

---

### Post by kdane4 on 2012-05-05
[http://ubuntuforums.org/showthread.php?t=1676518](http://ubuntuforums.org/showthread.php?t=1676518)

Quote from ***Mark Phelps***

> As SOON as you select Windows in GRUB, start pressing F8 and keep pressing it repeatedly until either safe mode comes up, or you get a text screen from which you can select safe mode.

The other poster got it working.. Im not an expert so lets just wait for somebody who knows the answer. :)

---

### Post by jawilljr on 2012-05-05
Open msconfig and in the boot tab put a check next to "safe boot"...restart.

Of course while in safe mode uncheck "safe boot" to boot back in normal mode.

Jerry

---

### Post by kdane4 on 2012-05-05
> **jawilljr said:**
> Open msconfig and in the boot tab put a check next to "safe boot"...restart.

Of course while in safe mode uncheck "safe boot" to boot back in normal mode.

Jerry

I believe the OP cannot boot into Vista (keeps on rebooting) so changing settings in msconfig is not possible.

---

### Post by GreggC on 2012-05-05
Hi Jerry,

I installed a new graphics card and I can't get Vista to boot in normal mode - It just restarts the computer. I assume Windows is trying to reboot into safe mode until I get the drivers installed.

---

### Post by GreggC on 2012-05-05
I managed to get into Windows boot manager by tapping F7. I pressed F8 and it rebooted the box. When I tried it again, I selected the memory diagnostic and it said a recent hardware or software change prevented Vista from booting (no surprise). I was prompted to inset the windows CD and select repair.
I have a feeling this would mess up the Ubuntu side of the machine. If there is a work around I'd like to try it. - I have a feeling I'll have to repair windows and fix grub or re-install Ubuntu.

---

### Post by kdane4 on 2012-05-05
maybe it depends on the laptop? anyway glad to hear you got it working.. :)
you really need to use the repair disc so you can boot into vista. Just a reminder, once you repair, GRUB will be overwritten but it can be easily repaired with the [boot repair tool]("https://help.ubuntu.com/community/Boot-Repair") . Its the same as reinstalling GRUB with an ubuntu live CD but painless

heres the forum thread for boot repair but I suggest you read the WIKI in the link above.

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by GreggC on 2012-05-05
Thanks!!!
I'll give it go and mark the thread solved if it works.

---

### Post by GreggC on 2012-05-05
Thanks for your help!
- made a Boot-Repair CD; booted from the Vista disc & repaired installation; rebooted into Windoze and waited and waited for updates......etc, installed drivers.

To my surprise - Grub was untouched!

---

### Post by kdane4 on 2012-05-05
I guess the windows repair disc didnt require restoring the MBR, just some minor repairs. :)
Anyway, glad to hear you got it working. You can [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").. 

cheers!! :)

---

