---
title: "Live CD Shutdown Script"
date: 2009-11-17
forum: General Help
---

### Post by ShareBuntu on 2009-11-17
Hello,

I'm in a sticky situation. I'm using the Live CD to move some partitions around. Unfortunately, the current operation is going to take 19 hours to complete (it's a lot of data). The problem is, I'll be out of town before it completes - and would have no way of shutting down my computer.

So, I thought you could help me punch out a one-liner that'll shutdown the computer (with the Live CD in the tray still) after, say, 24 hours? My only concern is the computer hanging on the screen where the CD is ejected and ENTER must be pressed to continue - even if the script is successful.

Help?

P+.

---

### Post by Aubergines on 2009-11-17
You might be able to setup crontab on the livecd to get it to shutdown at a specific time.

---

### Post by ShareBuntu on 2009-11-17
> **Aubergines said:**
> You might be able to setup crontab on the livecd to get it to shutdown at a specific time.

I was thinking of just opening a terminal and using the "shutdown -t" command. My main concern is the computer not shutting down and displaying the "remove CD from tray" screen. Would you be able to test it?

---

### Post by Aubergines on 2009-11-17
Actually it doesn't work, shutting down from the livecd (at least on my box) always prompts you do remove the CD and close the tray before properly shutting down.

---

### Post by ShareBuntu on 2009-11-17
> **Aubergines said:**
> Actually it doesn't work, shutting down from the livecd (at least on my box) always prompts you do remove the CD and close the tray before properly shutting down.

Thanks for the response. I'm not installing anything. I'm just using the Live CD to move a few NTFS partitions around - there's no operating system installed on the drive. So, you think the "shutdown -t" command will work and bypass the "remove disc from tray" screen?

---

### Post by Giblet5 on 2009-11-17
Bring up a terminal window.

Enter the following command:

```
sleep 75600 ; sudo poweroff
```

That will wait 22 hours (22x60x60), then power off the system.

---

### Post by ShareBuntu on 2009-11-17
> **Giblet5 said:**
> Bring up a terminal window.

Enter the following command:

```
sleep 75600 ; sudo poweroff
```

That will wait 22 hours (22x60x60), then power off the system.

Thank you! If this works I'll love you forever. If the computer stays on, sets itself on fire, and burns the building down, I'll be a little sad.

---

### Post by Giblet5 on 2009-11-17
> **ShareBuntu said:**
> Thank you! If this works I'll love you forever. If the computer stays on, sets itself on fire, and burns the building down, I'll be a little sad.

It *will* shut the system off in 22 hours - whether the partition work has completed, or not....

---

### Post by ShareBuntu on 2009-11-17
> **Giblet5 said:**
> It *will* shut the system off in 22 hours - whether the partition work has completed, or not....

How do we know it'll bypass the tray removal screen?

---

### Post by Aubergines on 2009-11-17
It's not a problem with a particular shutdown method. When you shutdown the Ubuntu Live CD environment it will always prompt you to remove the CD from the tray. This prompt is after the whole OS has shutdown but remains until you actaully press the ENTER key. So your machine wont actually eletrically power off until this happens.

If you're just reconfiguring partitions it might be worth using a different livecd distro. I tried my [CLI linux from scratch CD](http://www.linuxfromscratch.org/livecd/) and that does power off the machine without prompts.

The other method is boot the Ubuntu livecd off a USB drive thats been modified to not issue that last prompt - [http://www.pendrivelinux.com/ubuntu-remove-the-prompt-to-eject-cd/](http://www.pendrivelinux.com/ubuntu-remove-the-prompt-to-eject-cd/)

---

### Post by Giblet5 on 2009-11-17
I just tried it and the poweroff command did not follow a shutdown path that led to a prompt to remove the CD.

The reboot command does.

That said, I hope you did a complete backup of your data first. Shifting partitions around is not a trivial task and a lot can go wrong.

I also wouldn't walk away from a partition shift.

Also, it is guaranteed to shut the system off if you do it like this:

```
sleep 75600 ; sync ; sync; sudo poweroff --force
```

That's like pulling the plug out of the wall, but safe. It won't follow the shutdown path - it will power the system off Right Now (after 22 hours).


Pro tip: 'sync' will write all flagged, unwritten, buffers to disk and set the flag on any remaining unwritten buffers. So, sync;sync guarantees that ALL unwritten write buffers will have been written to the disk before the command returns.

---

### Post by Aubergines on 2009-11-17
That's really weird, poweroff still prompts me to remove the cd on my machine. With any luck it'll work for ShareBuntu :)

---

### Post by mithun.kamath on 2009-11-17
You could also try this command

sudo shutdown -h no:0f mins.

For eg if you want to if you want to shutdown after say 10mins

sudo shutdown -h 10

if you want to shutdown now

sudo shutdown -h now

Hope it helps

---

### Post by Giblet5 on 2009-11-17
> **Aubergines said:**
> That's really weird, poweroff still prompts me to remove the cd on my machine. With any luck it'll work for ShareBuntu :)

Did you try it with 'poweroff -f' or 'poweroff --force'?

Those don't follow ANY shutdown path at all. They virtually flip the switch.

---

### Post by Aubergines on 2009-11-17
> **Giblet5 said:**
> Did you try it with 'poweroff -f' or 'poweroff --force'?

Those don't follow ANY shutdown path at all. They virtually flip the switch.

Yeah actually, 'poweroff --force' works :D

---

