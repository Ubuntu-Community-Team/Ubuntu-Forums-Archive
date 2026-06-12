---
title: "Disable filesystem check after system crash"
date: 2011-08-22
forum: General Help
---

### Post by Herschdorfer on 2011-08-22
Hello together,
how can I disable the automatic file system check after power outages or system crashes?  The check sometimes prompts for a key (ignore, repair… etc.) but the panels do not have a keyboard.

Some ideas?

---

### Post by Script Warlock on 2011-08-22
i dont think its a good idea, you can delay but not disable. besides it can check every 50boots? does it run every boot?

---

### Post by Herschdorfer on 2011-08-22
Ok here is the scenario: 30, mostly, elder people have become a display for their homes. These people unplug the devices when they are running or hold the power button until the device dies. After such a miss-use of the devices, the file system check causes to run. Sometimes the system prompts for an input, but they do not have keyboard.
So if this is a good idea or not, it have to be disabled. Otherwise we can drive every 2 weeks around the block and fix the prompting displays…
Another idea is that the errors will always automatically be ignored/fixed… but how can I do this?

---

### Post by JKyleOKC on 2011-08-22
> **Herschdorfer said:**
> Otherwise we can drive every 2 weeks around the block and fix the prompting displays.If they persist in doing this, you'll also be re-installing the system on some of them pretty soon. The reason for NOT just pulling the plug is that critical system data may not yet have been written out to disk.

You could create a "dummy" file-check routine that does nothing at all; that would do away with the system prompt -- but would probably hasten the time that a complete re-install becomes necessary. You'd need to dig into the boot process to find out exactly how the "check" routine gets called, but it would be possible to do.

With no keyboards, how do these folk communicate with the systems? Or do they do so at all? If it's by touch screen or mouse clicks, perhaps a "shutdown" button would help, as would simply disconnecting the power button and hard-wiring the power cord so that it couldn't be pulled from the wall...

---

### Post by Script Warlock on 2011-08-22
this is worrisome but for Herschdorfer information heres how..

gksudo gedit /etc/fstab 

UUID=5df6ef11-148e-4ec8-a8f0-4c36b37464b8 /               ext4    errors=remount-ro 0       1

notice the last number change that to 0 and drive won't be checked

---

### Post by Herschdorfer on 2011-08-22
> **Script Warlock said:**
> this is worrisome but for Herschdorfer information heres how..

gksudo gedit /etc/fstab 

UUID=5df6ef11-148e-4ec8-a8f0-4c36b37464b8 /               ext4    errors=remount-ro 0       1

notice the last number change that to 0 and drive won't be checked

I’ve tried this but without success. 

Yes the we have touch screens and yes we have a shutdown button… but the user is dump… :) and we need the power switch because the displays have not reset button.

i need a beer...

i've also tried to deactivate the scan with ```
tune2fs –i 0 /sda1
``` also whit no success…

---

### Post by Herschdorfer on 2011-08-22
> **JKyleOKC said:**
> 
You could create a "dummy" file-check routine that does nothing at all; that would do away with the system prompt -- but would probably hasten the time that a complete re-install becomes necessary. You'd need to dig into the boot process to find out exactly how the "check" routine gets called, but it would be possible to do.

ok... how can i do this? :)

---

### Post by JKyleOKC on 2011-08-22
Let me start by saying that doing this may result in total destruction of the system; it will definitely remove one of the primary protective layers from it. I think that if you implement it, you will soon discover just how bad an idea it is. Nevertheless, here's one way to do it:

The program that performs the check is named "fsck" (**F**ile **S**ystem **C**hec**K**) and is located in the /sbin directory; it's executable only by the root user. Actually, I find 10 versions of "fsck" in my /sbin directory; the initial program determines exactly what flavor of file system is involved, then launches the appropriate one of the others to do the actual check.

You can move all 10 of them to a different directory to get them out of the executable path, and replace all of them with a simple script:```
#!/bin/bash
exit 0
```This script will do absolutely nothing, so when the boot process attempts to perform the check, nothing will happen but no error message will result.

Just to be on the safe side, I would make 10 copies of the script, each named exactly the same as one of the 10 original programs. Each should be owned by root, and have "execute" permission exactly the same as the original files. This may be overkill, but I have no way to know whether the boot process calls the generic "fsck" program or calls a more specific version directly.

Again, the result of doing this may well cause the system to become totally unbootable after an improper power-down and reboot, so it would be well to test this carefully on a system that can be sacrificed. It's also quite likely to require a total reformat and reinstallation of the users' systems fairly often -- in other words, the cure may be much worse than the disease!

---

### Post by Herschdorfer on 2011-08-24
Thx for the help... 

maybe I found a more elegant solution…
I used:
FSCKFIX=yes
In 
/etc/default/rcS
For answer “yes” every time fsck prompts for input. 
Seems to work...

---

### Post by JKyleOKC on 2011-08-24
A **much** better solution, since it does run the file-check and the system will do the best it can to repair the damage!

---

