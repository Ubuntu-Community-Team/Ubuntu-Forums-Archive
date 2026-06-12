---
title: "X Server Won't Start on Restart"
date: 2006-05-08
forum: General Help
---

### Post by DarkNemesis618 on 2006-05-08
I just installed the nvidia 8756 drivers for Ubuntu 5.10 x86_64.  The drivers installed fine.  But now whenever I restart my computer, X Server fails to start and I have to reinstall the drivers for it to work.  It's a pain in the @$$ and I was just wondering if anyone has any ideas.  Attached is my current (working at the moment) xorg.conf and the error log.  Thanks. ](*,)

Oh, it should be noted I have the nvidia GeForce 7900GT and as I understand, the 8756 drivers are the only ones at the moment that support my 7900 GPU.

---

### Post by tennvols_69 on 2006-05-09
by any chance did you download the updates listed in update manager for kernal 2.6.12-10-386? if so thats your problem. ive been figting with nvidia drivers 8756 and the updates for a bit now. finially decided that it was the updates. what i did was install ubuntu  do the updates for the default kernal.this will load the new kernal. reboot then do the driver install and not do the updates. as the updates in update manager for the 2.6.12-10-386 kernal causes problems with the nvidia drivers.  i plan on going one at  a time and installing to find out which update exactly is causeing the issue. hopes this helps you out as ive battled with it for 4 days before i finially found what was casuing the issue.

---

### Post by KillrBuckeye on 2006-05-11
DarkNemesis:  Did you ever find a solution to your problem?  I also have a 7900GT and I'm having the same problem!  I can start X after installing the nVidia drivers (using the nVidia installer package), but it won't start after a reboot.  I have to reinstall the drivers to get it working again.  tennvols_69:  I haven't done any updates.

---

### Post by BigWillyT on 2006-11-15
Okay guys, I have the answer to your problem.  I too have experienced the same thing with every version of 'buntu and I finally found the answer.  Look [here](http://www.ubuntuforums.org/showthread.php?t=290790&highlight=nvidia+driver+reinstall) for the answer. ;)

---

