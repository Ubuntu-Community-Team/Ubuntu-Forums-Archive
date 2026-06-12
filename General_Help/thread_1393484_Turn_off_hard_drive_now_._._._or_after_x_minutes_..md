---
title: "Turn off hard drive now . . . or after x minutes . . .?"
date: 2010-01-29
forum: General Help
---

### Post by jenaniston on 2010-01-29
The following thread is in archive and no reply is possible . . .[ http://ubuntuforums.org/showthread.php?t=288035]("http://ubuntuforums.org/showthread.php?t=288035")

The suggestion of System>Preferences>Power Management is from the  Desktop and it just hibernates the whole OS . . .

The root terminal is all I really have for now - in a jerry-rig USB U9.04 full install OS being run on USB of a sick Sharp AL27 laptop.

The laptop's hard drive is burning up . . . constantly spinning, yet the entire Ubuntu OS is on the USB pendrive - just need it to cool down a bit while I run commands and  learn to change fstab options all via the running USB U9.04 OS.

So, **a command line way to turn off hard drive ?**

Thank you very much.

---

### Post by llawwehttam on 2010-01-29
There is a (spin down hard disks where possible) option in power management as I used it 5 minutes ago.

---

### Post by jenaniston on 2010-01-29
> **llawwehttam said:**
> There is a (spin down hard disks where possible) option in power management as I used it 5 minutes ago.

well . . .thanks for the reply . . .
I would need advice to run it in a command line - any ideas ?

In Jaunty desktop there is in System>Preferences>Power Management > On AC Power tab only . . .
____________________________________________________________________

**Actions **

Put computer to sleep when inactive for     ----------------------------- minutes

**Display**

Put display to sleep when inactive for     ---------------------------------minutes
____________________________________________________________________

So I don't even find - in desktop - the "spin down hard disks where possible" - at least just yet.

But that** is the command I would need** in  command line/root terminal . . .
so thanks for the lead.

I am only in a command line/root terminal of the installed USB run Ubuntu 9.04 OS that has
 the laptop hard drive spinning but no OS being run on that hard drive.
It will blank out the screen - screensaver - and I'll hit a key to get my USB OS root terminal screen back up.

But I am starting to even smell a burning/heat of a hard drive spinning for now an hour or more. 

I am thinking about fstab  . . . ?

Any help greatly appreciated.

---

### Post by llawwehttam on 2010-01-29
This was in the archives: [http://ubuntuforums.org/showthread.php?t=308962](http://ubuntuforums.org/showthread.php?t=308962)

Should work for you.

---

### Post by jenaniston on 2010-01-29
> **llawwehttam said:**
> This was in the archives: [http://ubuntuforums.org/showthread.php?t=308962](http://ubuntuforums.org/showthread.php?t=308962) . . .

A great thread link . . . titled **"Spin Down Hard Drives"**

Thanks !

some excerpts . . .             
____________________________________________

_post **#3**_ . . .
                                                                **hdparm**  (run as root) is what you're after - it can control all aspects of your  hard disk operation.

For the spindown, you want the **-S <value> /dev/hda** option

_post **#4** _. . .
Thanks a bunch. I was trying to spin down 2 other hard drives that just  store data, not the OS.

_post **#9** _. . .
note the the default /etc/hdparm.conf file 
```
/dev/hdb  {
         spindown_time=240
}
```_post **#11** _. . .
Since adding a short spin-down time in the conf file, my laptop is  _VERY_ much cooler.
____________________________________________

Thanks again.
I am still trying to sort out a bit more . . . the man page seems **hdparm** is only for IDE hard drives ?
[http://linux.die.net/man/8/hdparm](http://linux.die.net/man/8/hdparm)

While sdparm ***is ***for SCSI hard disk drives . . . **sdparm** is a very different (capability) command
[http://linux.die.net/man/8/sdparm](http://linux.die.net/man/8/sdparm)

---

