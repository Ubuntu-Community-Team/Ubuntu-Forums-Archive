---
title: "iPod Touch 4G?"
date: 2010-11-12
forum: General Help
---

### Post by Ntwiles on 2010-11-12
Hey guys, I've been trying desperately to try to sync my iPod to play songs from it and to add songs to it. I've tried Rhythmbox, Amarok, and iTunes through Wine, but none of them will even acknowledge that a device has been connected. When I connect my iPod while in Rhythmbox, a device called "Unknown Device" pops up for just a second, then disappears. This computer is running only Ubuntu now so I'm pretty desperate to find a way to be able to sync my iPod. Any help would be greatly appreciated.

Edit: The iPod does show up in the Places menu. When I try to open it I get the following error:

```
Error: DBus error org.freedesktop.DBus.Error.UnknownMethod: 
Method "QueryInfo" with signature "aysus" on interface "org.gtk.vfs.Mount" doesn't exist
```

Please select another viewer and try again.

---

### Post by gupti on 2010-11-12
I'm not sure this might help, but I found another thread:
[http://ubuntuforums.org/showthread.php?t=1576249](http://ubuntuforums.org/showthread.php?t=1576249)

---

### Post by laurenbanjo on 2010-11-12
Did you try installing the gtkpod iPod Manager from the ubuntu software center?

---

### Post by Ntwiles on 2010-11-12
Browsing that thread and the ones it links to I've found multiple solutions but I haven't been able to follow through any of them. I've installed ifuse and gtkpod and I'm trying to create a mount point in /media/ipod. I can't find any information online about how to do that though. It seems like I need to edit fstab to create the mount point? I've put this line at the bottom of the file:

/media/ipod vfat nosuid, noauto, nodev, rw,umask=077,gid=1000, user, defaults, noatime, iocharset=utf8 0 0 

But it doesn't seem to do anything. I have no idea what it means, I just pasted it and modified it to match the directory of where I want to put my mount point.

My ipod is jailbroken, are there any resources available for jailbroken ipods to make this easier?

---

### Post by laurenbanjo on 2010-11-12
Can you borrow anyone else's iPod and try it? Maybe it doesn't recognize jail broken ones.

---

### Post by Ntwiles on 2010-11-12
> **laurenbanjo said:**
> Did you try installing the gtkpod iPod Manager from the ubuntu software center?

Yeah I have that as well. It allows me to specify the mount point I've chosen but it tells me there's no file directory detected in it. I'm assuming because it's not detecting the ipod at all.

I'm now using

/dev/sda1 /media/ipod defaults 0 0

in fstab which I believe is closer to what I needed. But when I give the command 'ifuse /media/ipod' I get the error "no device found"

Edit: Sadly I don't know anyone else with an ipod touch. I can restore it to unjailbreak it from my laptop but I would prefer to only do that if I have good reason to believe that's the issue.

---

### Post by laurenbanjo on 2010-11-12
Wait, so if you have another computer, why dont you just add the music there? You shouldn't sync 'cause I'm assuming your laptop must not be able to hold much music or else you'd have it on there, but you could use a flash drive and add the few songs you need to add every once in a while.

---

### Post by Ntwiles on 2010-11-12
By 'my laptop' I mean my mother's lol. I have access to it fairly often but not enough to use it to sync all the music I get onto my ipod.

Edit: I just restarted because why not and upon rebooting I got an error to the effect of "Could not mount /media/ipod". I was given the option to try to fix the issue through command line or to skip the step.

---

### Post by chanfle on 2010-12-01
Hello all,
I have a issue with my ipod touch 4g, when I connect on Ubuntu 10.10 the OS it detect perfectly (only see the photo folder)
but on Rhythmbox appear but disaapear quicly and I can't transfer my music on my ipod..
Any help for fix this issue?

---

