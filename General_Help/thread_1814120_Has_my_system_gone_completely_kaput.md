---
title: "Has my system gone completely kaput?"
date: 2011-07-28
forum: General Help
---

### Post by Shay Guy on 2011-07-28
Here's the story:

The screen of my years-old HP laptop (running Natty) freezes and eventually turns black. Ctrl-Alt-F# works to switch to the terminals. My fan is even louder than usual. I spend some time fooling around with [FONT="Courier New"]ps[/FONT] and [FONT="Courier New"]kill[/FONT] and shut down some of the most resource-consuming processes, which quiets the fan a bit, but tty7 still shows a black screen except for my mouse pointer.

I finally decide to shut it down altogether, but then I think to myself, "Self, you've used the power switch to shut down before in this situation, but shouldn't there be a more proper way to do it in the terminal?" So I try [FONT="Courier New"]shutdown[/FONT], I have trouble with it, it proceeds to get hopelessly tangled up, and it looks like it's frozen up in mid-restart when I throw up my hands and decide to go for the old power-switch-for-five-seconds method after all.

Now when I start the computer and select Ubuntu from GRUB, I get this:
```
Starting up ...
mount: mounting /dev/disk/by-uuis/xxxxxxxx-xxxx-4e35-bd5e-xxxxxxxxxxxx on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filestsyem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.17.1 (Ubuntu 1:1.27.2-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

Note: the xes are other hex digits that I wasn't willing to transcribe, and the underscore is of course a blinking cursor. One of the available commands is [FONT="Courier New"]exit[/FONT], but that causes kernel panic.

Is this a hardware problem? Software problem? Is my Ubuntu dead entirely? Should I select one of the other Ubuntu options from GRUB? I've still got Windows Vista dual-booted; should/can I do something with that?

---

### Post by fdrake on 2011-07-28
can you run a filesystem check?

```
fsck
```

---

### Post by Shay Guy on 2011-07-29
Let's try it!

```
/bin/sh: fsck: not found
```

...That's pretty damn bad, isn't it?

---

### Post by fdrake on 2011-07-29
can you try to boot from another grup option(select the below line), and see if that solves the problem.

---

### Post by Shay Guy on 2011-07-29
The top two options are "Ubuntu 11.04, kernel 2.6.38-10-generic" and "Ubuntu 11.04, kernel 2.6.38-10-generic (recovery mode)". Is the latter what you were suggesting?

---

### Post by fdrake on 2011-07-29
> **Shay Guy said:**
> The top two options are "Ubuntu 11.04, kernel 2.6.38-10-generic" and "Ubuntu 11.04, kernel 2.6.38-10-generic (recovery mode)". Is the latter what you were suggesting?

recovery mode is fine. as long you are able to mount your file. if you are succesfull that may solve the problem with the regular boot.

---

### Post by Shay Guy on 2011-07-29
The result: about 15 seconds' worth of data on the screen flying over my head, eventually stopping at...

```
mount: mounting /dev/disk/by-uuid/xxxxxxxx-xxxx-4e35-bd5e-xxxxxxxxxxxx on /root
failed: Invalid argument
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed
: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filestsyem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

[SIZE="4"]...[/SIZE]

---

### Post by fdrake on 2011-07-29
that does not look very comforting... I suggest you to get a live cd and save you critical data to a usb drive if you can and use it to fsck the HDD. Sorry for not being able to help you more than this. Hope someone else know a better solution.

ps.when you are at the GRUB menu try to press "SHIFT" and press root.
and from there try fsck. my last idea....

---

### Post by Shay Guy on 2011-07-29
I thought about a LiveCD. The problem with that? I don't know how to eject the CD tray in ash. BusyBox. Whatever.

That part's almost funny.

---

### Post by Shay Guy on 2011-07-29
Also:

> **fdrake said:**
> ps.when you are at the GRUB menu try to press "SHIFT" and press root.
and from there try fsck. my last idea....

What do you mean "root"? There's a command line for GRUB, but it hasn't got [FONT="Courier New"]fsck[/FONT].

---

### Post by zero244 on 2011-07-29
How old is this laptop?

I agree better try to get any files you want to save from a live cd or flash drive.
Looks to be failed or failing. Could be the hard drive or the circuitry on the motherboard.
It could be a bad cable, but I would consider that a long shot.
Good luck.

---

### Post by Shay Guy on 2011-07-29
Thank goodness -- the eject button worked just fine in GRUB, and I've gotten it running on a LiveCD. Not sure what order to do things in now, though...

> **zero244 said:**
> How old is this laptop?

At least three years old. Likely more, I can't remember exactly. I've been thinking about replacing it for some time now, maybe with an ASUS or Acer.

---

### Post by zero244 on 2011-07-29
With the live cd you can boot up Ubuntu without installing it.
Once you get to the live cd desktop mount your hard drive if needed  and see if it works.
If it does work and you have pictures, music or anything you want to keep, copy those files over to a flash drive or usb hard drive etc.

If your existing hard drive mounts ok and seems to be working then at least there is hope.

I suspect if its failing to boot......it probably wont mount from the live cd.

Keep us posted!

---

### Post by Shay Guy on 2011-07-29
> **zero244 said:**
> With the live cd you can boot up Ubuntu without installing it.

Oh, I knew that. I had Ubuntu booted up already, the problem was what next.

> **zero244 said:**
> Once you get to the live cd desktop mount your hard drive if needed  and see if it works.

Attempted mounting my Ubuntu filesystem. The results:

```
**Unable to mount ## GB Filesystem**
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

So I tried [FONT="Courier New"]dmesg | tail[/FONT] at the terminal:

```
ubuntu@ubuntu:~$ dmesg | tail
[11684.220341] Descriptor sense data with sense descriptors (in hex):
[11684.220344]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[11684.220358]         07 f1 82 1a 
[11684.220364] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[11684.220371] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 07 f1 81 e5 00 01 00 00
[11684.220384] end_request: I/O error, dev sda, sector 133267994
[11684.220409] ata3: EH complete
[11684.220412] JBD: Failed to read block at offset 19626
[11684.220419] JBD: recovery failed
[11684.220422] EXT3-fs (sda3): error loading journal
```

My Vista partition, on the other hand, mounted perfectly. So I'm guessing booting that OS would work fine.

---

### Post by mosaic2s on 2011-07-30
i have ditto error on my 4 month old dell vostro machine running ubuntu 10.04 with dual boot option.
the machine hung up since i removed the netsetter usb while it was shutting down. and then i removed the battery to make it shut down completely. 
this worked earlier. this time however, the USB ports are not working in the ubuntu OS. while other OS all ports are working fine.
has some freak voltage has damaged the ubuntu installation where it can not activate USB ports and therefore it refuses to boot?

if there is a way to bypass USB ports then it will boot.

I had a similar issue with another comp where the USB ports were failing. Finally I formatted the drive and re - installed. after a while the same error re appeared. however each time in both machines, the other OS worked fine.

so i am assuming it is an hardware error that does not allow the ubuntu booting to progress while OTHER OS boots.

---

### Post by Shay Guy on 2011-07-31
LiveCD's still working. Main filesystem still isn't mounting.

It's midnight here and my system clock says it's 5 AM. Complicating the matter, I'm pretty sure I didn't boot this up tonight until like 9 PM, so it's not like it started its clock at midnight then.

---

### Post by Shay Guy on 2011-07-31
[FONT="Courier New"]fsck[/FONT], by the way, is not doing anything from the LiveCD Terminal except printing "[FONT="Courier New"]fsck from util-linux-ng 2.17.2[/FONT]," even with the [FONT="Courier New"]-A[/FONT] option.

**EDIT:** HA! Never mind, I did some further tinkering with [FONT="Courier New"]fdisk[/FONT], ran [FONT="Courier New"]sudo fsck /dev/sda3[/FONT], and...

```
/dev/sda3: recovering journal
Clearing orphaned inode 3047433 (uid=0, gid=0, mode=0100600, size=178)
Clearing orphaned inode 3473643 (uid=0, gid=0, mode=0100644, size=243400)
/dev/sda3: clean, 641547/4571136 files, 6735431/9132952 blocks

```

AND IT MOUNTS! O frabjous day! Callooh! Callay! So long, LiveCD, and thanks for the good times! Time to log off and hit the sack. Ubuntu Forums, I thank you, and good night.

Now the only question is whether I still need a new laptop, just in case...

---

