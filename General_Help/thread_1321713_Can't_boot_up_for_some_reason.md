---
title: "Can't boot up for some reason"
date: 2009-11-10
forum: General Help
---

### Post by Haedrian on 2009-11-10
I have ubutunu installed 'inside windows', and have been using it for the past 2 weeks or so without any large problems.

Today I installed a few updates (from the update manager) - now I can't run it anymore - on boot it gives me this error -

[B][Linux-bz Image. setup=0x3400, size=0x3b26e0]
[Initrd, addr=0x2f0cf000, size=-x788fe6]
[ 1.068769] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
[/B] 
Then it stops trying to load, the Capslock goes on and off and it waits.

If I run it 'debug mode' I get a much larger set of information (which I'm not typing here since its too long - unless its needed).

I can still run windows XP.

Now I have backups of my documents - except one which I really need.

The file (of files) on windows seems to be saved as a .disk (which I can't open).

So the main question is:

1. Is there a way of recovering my files?
2. Is there a way to solve it?

Upon boot I can 'e' to edit the commands before booting or 'c' for a command-line

Help?

---

### Post by Haedrian on 2009-11-11
Didn't find anything in the forum rules about bumping unanswered threads so I guess...

bump.

---

### Post by ninja togo on 2009-11-11
I also need help with this I receive same error after same situation. school projects are still in there and I need them

---

### Post by garikgarik on 2009-11-11
I am experiencing exactly the same problem. Exactly the same questions!!!!

> **Haedrian said:**
> I have ubutunu installed 'inside windows', and have been using it for the past 2 weeks or so without any large problems.

Today I installed a few updates (from the update manager) - now I can't run it anymore - on boot it gives me this error -

[B][Linux-bz Image. setup=0x3400, size=0x3b26e0]
[Initrd, addr=0x2f0cf000, size=-x788fe6]
[ 1.068769] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
[/B] 
Then it stops trying to load, the Capslock goes on and off and it waits.

If I run it 'debug mode' I get a much larger set of information (which I'm not typing here since its too long - unless its needed).

I can still run windows XP.

Now I have backups of my documents - except one which I really need.

The file (of files) on windows seems to be saved as a .disk (which I can't open).

So the main question is:

1. Is there a way of recovering my files?
2. Is there a way to solve it?

Upon boot I can 'e' to edit the commands before booting or 'c' for a command-line

Help?

---

### Post by Haedrian on 2009-11-12
Is there a way to file a bug report? If this is so widespread then it is a big problem..

---

### Post by P4man on 2009-11-12
Can you guys boot an older kernel?
As for recovering the files, have a look here:
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?)

---

### Post by ALF102 on 2009-11-12
Yup, I guess the reason this all starts with a simple updates T_T

---

### Post by Haedrian on 2009-11-12
> **P4man said:**
> Can you guys boot an older kernel?


How exactly do I do that without uninstalling my current version?

Added: didn't see the link, never mind.

---

### Post by P4man on 2009-11-12
> **Haedrian said:**
> How exactly do I do that without uninstalling my current version?

Added: didn't see the link, never mind.

That link shows how you might be able to retrieve your docs, nothing else.

But to boot another kernel, just select one from the grub menu, assuming you have more than 1 kernel installed so it looks like this

[IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.chainload.grub.sm.png[/IMG]

If you only have 1 kernel version there and recovery mode than ignore my suggestion.

---

### Post by Schobs on 2009-11-12
Experiencing the exact same problem after installing the updates yesterday!!

Windows 7 still running, but I got the same error msg.

Would a bios update help maybe?

@ P4man: Yes, I only got one kernel version installed. However, the recovery mode does not work eithe. It stops after about 5 seconds of loading...

---

### Post by Haedrian on 2009-11-12
I only have one kernel installed.

I tried the guide to recover the files - its not working.

The first one doesn't open .disk files - the second one I installed - and it didn't do anything (Ie it didn't find the disk or something).

I'll try the 'booting from a live cd' option soon.

---

### Post by r0tor on 2009-11-12
same problem here after the update...

---

### Post by benjamin222 on 2009-11-13
Exact same problem here, all I did was run updates.

---

### Post by Haedrian on 2009-11-14
Allright, I used the method in that link to access the files (though using a virtual cd) and it worked - so I'm content up to that regard.

I ran a fsck on the root disk, and it came clean - but I still can't reboot.

So, what do I do now? Reinstall wubi and avoid updates? Do the developers know of this bug?

---

### Post by JBAlaska on 2009-11-14
I had a very similar problem this morning on my lappy with a wubi through winblows install. Last night I used "suspend to ram" for the first time (It worked) and this morning when I booted Linux I got the grub prompt.

I guess it might have been the update that did me.

I got my partition mounted with the LiveCD..so I can backup my /home like so:

[B]Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:
[/B]
```
sudo mkdir /win
sudo mount /dev/sda1 /win
```

**Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein**

```
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

[B]Now the content of the virtual disk will be visible under /vdisk.
[/B]

[COLOR="Blue"]Then I found this procedure to "fix" it:
[/COLOR]
[B]From the SH> prompt enter

sh:grub>insmod ntfs
sh:grub>set root=(hd0,1)
sh:grub>loopback loop0 /ubuntu/disks/root.disk
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot[/B]  [COLOR="Blue"]<---I get to here but MY boot fails with "linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro not found" [/COLOR]

**This might boot your system's though**.

**In Ubuntu open the terminal and enter:**
```
sudo update-grub2
```
**This should fix your grub files.**

[COLOR="Green"]It worked for some folks but not me, you will just have to try it and see if it works for you.[/COLOR]

[B]Since I was just "playing" with the wubi windows install, if I can't fix this I'm going to partition my laptop drive and do a "real install".

Hope this helps someone.[/B]

---

### Post by Haedrian on 2009-11-14
SH prompt? You mean the terminal?

How do I get the SH prompt?

---

### Post by JBAlaska on 2009-11-14
If you don't have the grub sh prompt you don't have the same problem as I do.

When I try to boot into Ubuntu, I get a grub error "wubildr" not found and this prompt
sh>

But to do the LiveCD part, yes you use a terminal.

---

### Post by Haedrian on 2009-11-14
Yeah I already recovered the files I needed.

I'm just wondering if there is a way of restoring it to its usual functionality without uninstalling/reinstalling.

---

### Post by benjamin222 on 2009-11-15
> **Haedrian said:**
> Yeah I already recovered the files I needed.

I'm just wondering if there is a way of restoring it to its usual functionality without uninstalling/reinstalling.

I've been searching around, still haven't found an easy fix. I did find the official bug page for it though

[https://bugs.launchpad.net/wubi/+bug/477169](https://bugs.launchpad.net/wubi/+bug/477169)

---

### Post by Dale61 on 2009-11-17
> **Haedrian said:**
> Yeah I already recovered the files I needed.

I'm just wondering if there is a way of restoring it to its usual functionality without uninstalling/reinstalling.

I'll wait for a couple of days, so this problem can be sorted, then I'll be re-installing, via WUBI, like I did early last week.

---

### Post by Haedrian on 2009-11-18
Well, I'll need a working Linux OS within a week, I take it this problem doesn't extend to partition installations right? I'll install on a partition if needs be.

---

### Post by wrgb2 on 2009-11-18
You're right, there shouldn't be any problem with an install to a dedicated partition.

---

