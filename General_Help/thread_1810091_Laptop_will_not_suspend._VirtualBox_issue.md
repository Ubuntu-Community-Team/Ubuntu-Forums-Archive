---
title: "Laptop will not suspend. VirtualBox issue?"
date: 2011-07-22
forum: General Help
---

### Post by darthpenguin on 2011-07-22
Hi Guys,

I upgraded my Thinkpad T400 from 10.10 to 11.04. Everything worked flawlessly including suspend (I think, I usually opt for shutting down instead of suspend). Anyway I tried to suspend the machine the other day (just closed the lid) and the suspend indicator light (quarter-moon-shape-icon) on my laptop just kept flashing. When I opened the laptop to inspect the problem the screen was black (but not off) and my only option to get things going again was to remove the battery (holding power button was not invoking a cold shutdown). I figured it was a kernal issue so I rebooted into the 2.6.38-8-generic-pae kernal instead of the 2.6.38-10-generic and suspend worked again. Then, today, it wouldn't suspend; same behavior as before. I ran uname -r to make sure I was in the old kernal [38-8]. I was.

I though about what could be causing the issue and I think it might be VirtualBox. The problem started after I upgraded to VirtualBox 4.1.0 (I wanted the 'clone' feature). Of course, VBox said I had to run this command '/etc/init.d/vboxdrv setup' (thank the maker for bash_history) before I could boot up my VMs. Oddly enough, I had to run that same command again after switching to the old kernal which is when the suspend issue started again.

Clearly, running '/etc/init.d/vboxdrv setup' edits the kernal (or kernal modules or something) allowing VBox to run VMs; but could it also be screwing up suspend support? Or am I way off base? Has anyone else had a similar problem? How can I fix it?

---

### Post by darthpenguin on 2011-07-22
Okay, kinda answered my own question. If I run this command

```
sudo /etc/init.d/vboxdrv stop
```

then suspend the machine all is well b(^_^)d

So why is the vboxdrv inhibiting laptop suspension? How can I fix it? Disabling the vboxdrv service is a workaround at best.

---

### Post by davescafe on 2011-07-22
I was having the same problem. Thank you posting how to stop the service. That solution works for me.

For the record, I have just installed Ubuntu 11.4 on an HP Compaq 8510w laptop. I installed VirtualBox 4.1 with extension pack that I downloaded from virtualbox.org (not from Ubuntu repositories).

There is a defect ticket opened on this at VirtualBox (#9260): [http://www.virtualbox.org/ticket/9260]("http://www.virtualbox.org/ticket/9260")

---

### Post by Dave_L on 2011-07-22
Previously reported here: [http://ubuntuforums.org/showthread.php?t=1809463](http://ubuntuforums.org/showthread.php?t=1809463)

---

### Post by darthpenguin on 2011-07-22
Thanks Dave_L

As you suggested in the other thread; I reverted back to VirtualBox 4.0. Hopefully the guys over at Virtual box fix this bug. I really want the cloning feature. I'll install VBox 4.1 on y desktop though. It's acting as a server so I never suspend it.

---

### Post by TechBeastie on 2011-07-31
I had the same problem, and can confirm that uninstalling VirtualBox 4.1 immediately restored suspend/hibernate functionality.  While investigating this problem, I also ran into the following two links, both of which look very promising

[ This one ]("http://www.virtualbox.org/ticket/9260") is a VirtualBox problem ticket discussion, in which some enterprising soul offers the following workaround:
"Adding the following line in /etc/pm/config.d/unload_modules fixes the problem for me:
```

SUSPEND_MODULES="$SUSPEND_MODULES vboxdrv vboxnetflt vboxnetadp vboxpci

```
"
I haven't tried the fix yet, but it looks right on-target.  

And [these folks]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/814323") just released a patch for this very problem.  I haven't tried it yet either, but when/if I do I'll report back.

Hope something in all that proves helpful!

---

### Post by Contrast on 2011-08-14
Just chiming in to say the workaround posted by TechBeastie worked right away (i.e., no reboot necessary) for me. Although, the line is missing a quote; it should read:
```
SUSPEND_MODULES="$SUSPEND_MODULES vboxdrv vboxnetflt vboxnetadp vboxpci"
```
Thanks for finding this fix for us, TechBeastie. :)

---

