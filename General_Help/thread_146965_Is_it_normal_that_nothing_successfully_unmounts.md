---
title: "Is it normal that nothing successfully unmounts?"
date: 2006-03-19
forum: General Help
---

### Post by dpaint4 on 2006-03-19
Like my iPod, my GP2x, my other hard drive, my iAudio X5. I plug them in and they auto-mount and pop a happy little icon onto the desktop.

I unmount them, and the icon on the desktop dissappears, but I get an error message stating:

```
Unable to Eject Media:
eject: unable to eject, last error: Invalid argument
```

And the iPod or whatever we're talking about does not acknowledge that it's been unmounted, so basically I have to just yank the cord on it.

Why is this? Even GtkPod, which is supposed to handle mounting and unmounting, always fails on the unmount part.

Anyone else out there with this issue, or better, a sollution for it?

---

### Post by astoltz on 2006-03-19
Can't speak for the other devices, but for my ipod, I have to use the eject command: ```
eject [ipod]
```where [ipod] is the name of the mount point under /media/.

---

### Post by Ramses de Norre on 2006-03-19
I also get this error when unmounting a medium without an eject function, though they always seem to be unmounted properly.
Maybe someone has a solution to avoid this error.

---

### Post by aysiu on 2006-03-19
It's a Breezy bug for certain devices (wasn't in Hoary). It's supposedly fixed as of Dapper Flight 3.

The temporary workaround for Breezy is using the *eject* command.

Read [this thread](http://www.ubuntuforums.org/showthread.php?t=84262) for more details.

---

### Post by dpaint4 on 2006-03-19
[QUOTE=aysiu]It's a Breezy bug for certain devices (wasn't in Hoary). It's supposedly fixed as of Dapper Flight 3.

The temporary workaround for Breezy is using the *eject* command.

Read [this thread](http://www.ubuntuforums.org/showthread.php?t=84262) for more details.[/QUOTE]

Thanks. That's reassuring, so I'll look forward to Dapper. I have tried the eject command as well, and get the same error.

```
curtis@HE3S4OODE:~$ eject ipod
eject: unable to eject, last error: Invalid argument
```

I'm going to assume that after this, even though there's an error, it's safe to unplug devices, and that I can just wait for Dapper right?

EDIT:

I read the thread. When I sudo eject, I get no error message and it is removed from my desktop, but still believes that it's connected. So like the screen still has the do not disconnect warning.

---

### Post by aysiu on 2006-03-19
[QUOTE=dpaint4]
I read the thread. When I sudo eject, I get no error message and it is removed from my desktop, but still believes that it's connected. So like the screen still has the do not disconnect warning.[/QUOTE] That's weird, because I don't when I try to eject my wife's iPod.

Are you ejecting the /dev or the mount point (/media)?

---

### Post by dpaint4 on 2006-03-19
[QUOTE=aysiu]That's weird, because I don't when I try to eject my wife's iPod.

Are you ejecting the /dev or the mount point (/media)?[/QUOTE]

When I type the command, so far, it's just been:

```
sudo eject ipod
```

Should I be typing a path to it?

It's mounted at /media like my other drives.

---

### Post by aysiu on 2006-03-19
[QUOTE=dpaint4]When I type the command, so far, it's just been:

```
sudo eject ipod
```

Should I be typing a path to it?

It's mounted at /media like my other drives.[/QUOTE] Yes, you should be typing a path--something like ```
sudo eject /media/ipod
``` or ```
sudo eject /mnt/ipod
```

---

### Post by mcduck on 2006-03-19
'sudo eject ipod' always worked for me in Breezy with  ipod mini :)

Dapper seems to eject it properly from the icon menu <3

---

### Post by dpaint4 on 2006-03-19
[QUOTE=aysiu]Yes, you should be typing a path--something like ```
sudo eject /media/ipod
``` or ```
sudo eject /mnt/ipod
```[/QUOTE]

Well, that worked to the same degree that sudo eject ipod worked, in that it removed it with no errors but the ipod still thinks it's connected.

I'm going ot put my faith in the well dressed duck I guess.

So I'll end my whining if someone can verify that even though the ipod says not to, I should be able to remove it without any harm. Right? There's no way data could be travelling to or from it if the computer dosen't even see it, right?

---

### Post by jerrykenny on 2006-03-19
I dont have this, but, Is there any milage in editing the /etc/fstab file, and changing the default option

user      (for all the stuff under /media)

to  . . . . 

users


?  which is the option to allow all users to be able to "unmount" as well as "mount" the media ?

---

### Post by Edward The Bonobo on 2006-03-20
I routinely unplug my iPod while it's still showing 'Do not disconnect'.  In fact, sometimes I have to do this several times if gtkpod fails to Read or Sync.  So far it hasn't done any harm.

---

### Post by Ranime on 2006-03-20
Hi there,

I found that it isn't particulary a breezy problem. Certain hardware is just incompattible in basic design. For instance:

I have a MSI K7N2 Delta series motherboard (for socket A AMD procs) with a nForce2 chipset. Also I had a Pioneer slot-in dvd player that fowled-up. I couldn't get it unmounted either, the same happened with the ASUS dvd player I bought for it instaid. Now I got a BenQ dvd burner and it works just fine.

It is possible your hardware devices is hogging the IDE ports or interupting HALd to function propperly.

Furthermore, the two drives I removed work fine in other pc's with different configs ;)

Bad things happen, I guess...

---

### Post by fazza on 2006-03-20
hi, I've found the same problem, although only when I have to restart X server, ot boot into recovery mode. I've just been recommended [automatix]("http://www.ubuntuforums.org/showthread.php?t=138405") which apparently lets you unmount a cd drive when you press the open button on the frontof the drive, so maybe it'll be the same with the iPod.
How do you get your iPod to work on Ubuntu anyway? I can't make it work. (Sorry if that bit's in the wrong thread-  I'm not sure where to post it).
Hope that helps, fazza

---

