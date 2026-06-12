---
title: "unable to boot - hibernation failed"
date: 2010-02-16
forum: General Help
---

### Post by kwildman on 2010-02-16
I apologize in advance.. I searched and there is way too much information on this board and wasnt sure what was applicable to my case.   I suspect that I prematurely closed the lid on my netbook last night when shutting down...my wife heard beeping noises early this morning but wasnt sure where they came from.   I think it was the netbook forcing shutdown from hibernation due to low batteries.

Computer wouldnt boot this morning and I get the following error:

[INDENT]one or more of the mounts listed in /etc/fstab cannont be mounted:
/home: waiting for UUID=3a45bd-6c46-48d4-bcd5-61b9218e3849
press esc to enter recovery shell

[/INDENT]entering the recovery shell 

[INDENT]General error mounting filesystems.
a maintenance shell will be started
Control D will terminate this shell and retry.

[/INDENT]The info reported is:

[INDENT]mountall start/starting
swapon /dev/disk/by-uuid/9dabd882-a1d1-460c-85f6-0b9d4f9cb564: swapon failed:  Device or resource busy
Mountall: swapon /dev/disk/by-uuid/9dabd882-a1d1-460c-85f6-0b9d4f9cb564 [886] terminated with status 255
mountall: problem with activating swap:  /dev/disk/by-uuid/9dabd882-a1d1-460c-85f6-0b9d4f9cb564

One or more of the mounts listed in /etc/stab cannot yet be mounted 
(ESC for recovery shell)
/home: waiting for UUID=3a45bd4b-6c46-48d4-bcd5-61b9218e3849

mountall: cancelled

[/INDENT]Any help would be greatly appreciated.   I do have a cloned image file of my computer but I would prefer to learn how to do this right.

thanks

Kevin

---

### Post by whiskers75 on 2010-03-05
Have you tried-when in the maintenance shell-typing "fsck"?
This will check your filesystem for errors and tell you if you want to fix them.

---

### Post by efflandt on 2010-03-05
There is no shutdown from hibernation.  If you hibernate, the system saves RAM to swap and powers down completely.

I suspect that your system was set to suspend when the lid is closed (a low power mode with just RAM powered).  There is another setting for what to do on low battery (hibernate or shutdown).

So you may have either confused it by closing it too soon, or there was insufficient battery power left to finish doing whatever it was attempting to do on low battery.

---

