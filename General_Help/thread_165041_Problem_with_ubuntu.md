---
title: "Problem with ubuntu"
date: 2006-04-23
forum: General Help
---

### Post by alfre_gr on 2006-04-23
I installed ubuntu on my machine, but when is loading, it hangs when "starting hotplug subsystem" and doesn't start! 

I have wireless internet, I don't know if that's the problem... Can somebody help me?? I'm a novice with linux and ubuntu... Really don't know what to do...

Thankx

---

### Post by sinkxdie on 2006-04-23
Did you ever try disabling your wireless card and then starting Ubuntu, just a suggestion. :D

---

### Post by alfre_gr on 2006-04-23
Don't know how... :(

---

### Post by sinkxdie on 2006-04-23
:D Does it have a button, my laptop(Compaq something) have a button on the top that you press and it disables it. 
Is it an internal card?

---

### Post by alfre_gr on 2006-04-23
Yes, it's internal, but it's a desktop, not a laptop...!

---

### Post by sinkxdie on 2006-04-23
Oh, haha then I don't know what to do

---

### Post by robglinka on 2006-04-23
Have you tired just removing the wireless card?

---

### Post by alfre_gr on 2006-04-23
Don't know how... I mean, I haven't open a desktop in my life yet, so I don't know which cable or bus to disconnect...

---

### Post by robglinka on 2006-04-23
It is probably a PCI card in your computer, you'd just have to turn your computer off, unplug it, and remove the card. 

But if you don't know what you're looking for, maybe you should see if you can find a friend nearby that does.

-rob

---

### Post by dmizer on 2006-04-24
when it says "starting hotplug subsystem", you might be able to get away with just hitting <ctrl>c to cancel it.

---

### Post by bobpur on 2006-04-25
I just built a new system that hangs up in the same place. Unlike yours, mine has never had an OS installed. Ubuntu and Kubuntu (v5.10) both install and both hang up on "Starting hotplug subsystem" on boot. The AMD 64 version won't install at all (and this is an AMD 64 system). Also WinXP won't install either. It gives an error message about not detecting my harddrives which are two Seagate 200 GB drives in a RAID 0+1 (striping) setup.
I mention this because maybe I need to go check my mobo drivers and update before taking another stab at installing an OS. You might want to check these too on your system.
Also, if you start Ubuntu in safe mode you get a really freaky time out message preceded by a bunch of numbers that just keep on scrolling. IF you can make sense of it, let me know.
Good luck.

---

### Post by cracker on 2006-04-26
Generally, fake hardware raids are not recommended to use with linux.

Try using a liveCD and booting the system without hotplug, and then disabling hotplug from the RC scripts, to see if it boots.

---

### Post by 1002285 on 2006-04-27
cracker,
can you say a little more about this "disabling hotplug subsystem from RC scripts". I have a 3-5 years old (I bought it used) Dell Latitude and it also hangs in "starting hotplub subsystem", but not every time. Windows XP worked fine on this computer.
But is this "hotplug system" useful anyway?
If it's not necessary, I'd like to try and disable it.

---

