---
title: "Installing Debian on Nexus One, script says cp, grep, mkdir unknown"
date: 2010-02-19
forum: General Help
---

### Post by hobo14 on 2010-02-19
This is a bit of a strange one, I'm not really sure where to post it...

I'm installing Debian on my N1 as per this OP: 
[http://forum.xda-developers.com/showthread.php?t=631389&highlight=debootstrap]("http://forum.xda-developers.com/showthread.php?t=631389&highlight=debootstrap")

My phone is unlocked, rooted, and has busybox installed. cp, grep and mkdir all work fine in a terminal on the phone, and in an adb shell on a computer linked to the phone.  
Not sure about grep and mkdir, but I know cp is not part of the Android linux distro, it's from busybox.

When I get to about step 6 of the guide this happens:
```
**#** chroot /data/local/mnt/ /debootstrap/debootstrap --second-stage

[FONT="Lucidia Console"]chroot /data/local/mnt/ /debootstrap/debootstrap --second-stage
/debootstrap/debootstrap: **332: cat: not found**[/FONT]
```

I checked line 332 of the debootstrap script, and sure enough it's the end of an if block that contains a cat statement, so I replaced the cat statement with an appropriate string constant, which fixed the cat problem at 332 but then I got similar messages re grep and mkdir at lines 376 and 386, which I can't replace because I don't know what string to replace them with.

Why, oh why would a script running in an OS that happily accepts cp, grep and mkdir statements say that it can't find those commands?

Help! Totally lost, I can't even begin to guess why this is happening...

---

### Post by prshah on 2010-02-19
> **hobo14 said:**
> 
```
**#** chroot /data/local/mnt/ /debootstrap/debootstrap --second-stage

[FONT="Lucidia Console"]chroot /data/local/mnt/ /debootstrap/debootstrap --second-stage
/debootstrap/debootstrap: **332: cat: not found**[/FONT]
```<...>guess why this is happening...

Just a guess; but maybe you need to include /bin in your path (after the chroot is performed?); eg```
export PATH=/bin:$PATH
``` Or use the full path to the command eg "/bin/cat" instead of just "cat".

---

### Post by hobo14 on 2010-02-20
Thanks parshah, just needed to chroot, edit the path, then run the script.

---

