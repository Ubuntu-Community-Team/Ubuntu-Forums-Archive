---
title: "Fixing suspend/hibernate in Natty?"
date: 2011-04-29
forum: General Help
---

### Post by Bartleby Jones on 2011-04-29
I've looked around for fixing suspend/hibernate on my Asus G60, and all of the topics here are for older versions of Ubuntu and point to files that don't exist/use old commands/etc.. Any ideas?

I've solved my backlight problem, video driver problem, and pretty much everything else. This is the last thing that needs doing.

---

### Post by Sonsum on 2011-05-16
> **Bartleby Jones said:**
> I've looked around for fixing suspend/hibernate on my Asus G60, and all of the topics here are for older versions of Ubuntu and point to files that don't exist/use old commands/etc.. Any ideas?

I've solved my backlight problem, video driver problem, and pretty much everything else. This is the last thing that needs doing.

What issue are you having, it'll help us immensely in helping you :)

For example, what sort of stuff do you see?

---

### Post by thevillagegeek on 2011-06-04
I am having a similar problem with Ubuntu 11.04 on an HP 620 notebook dual booted with Windows 7 (Let's not go there, unless it's related). 
Entering hibernation appears to work, in that the system takes longer to shut down, as if it is writing to disk. On my attempt to resume, however, it goes to the Grub menu as in normal bootup. 

I have not noticed problems with Suspend, but I'll check again after I post this.

Occurrence: both tests today were on AC power with 3 USB devices connected via a hub and ethernet cable connected.

Hard drive and partitions
SATA Host Adapter: Intel ICH9M/M-E SATA AHCI Controller, 6 ports
Volumes
System 315 MB HPFS/NTFS bootable /dev/sda1 not mounted
157 GB NTFS /dev/sda2 not mounted (my Windows partition)
Extended partition 145 GB /dev/sda4 (container for logical partitions)
142 GB ext4 /dev/sda5 Ext4 (version 1.0) (mounted, my Linux partition)
Unknown 3.1 GB /dev/sda6 Linux swap (0x82) (3,145,728,000 bytes)
HP_RECOVERY 16 GB NTFS /dev/sda3 (not mounted)

System RAM from "free": Total 3023416, Swap 3071996

There is plenty of hard disk space available. I suppose I could try increasing my swap space a bit, but I'm not sure that would make a difference. 

Suggestions?

Thanks!

---

### Post by Novacaptain on 2011-06-05
"On my attempt to resume, however, it goes to the Grub menu as in normal bootup." 

You do realize that this IS the expected behavior, right?

You can hibernate windows and it will do the same thing. The important thing is what happens when you choose the boot option that you hibernated from.  Does it lock up, begin a new session or resume your previous session?

You can play a game in windows, hibernate, go into ubuntu, do some work there, hibernate, go back into windows, continue playing the game etc...

---

### Post by MrJones on 2011-06-07
I'm having the same problem. If you want to make sure it's not a write-error, you can try the following:

```
sudo apt-get install uswsusp
```That's installing the program. And then:
```
sudo s2disk
```You'll see the computer give output from the write process.

---

### Post by ThatCoolGuy220 on 2011-06-07
Also you can try installing this packages:

- lm-sensors.
- cpufreq. 
- fancontrol.

It fixed mine

---

