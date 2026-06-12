---
title: "Laptop won't boot after fresh install of 11.04 with LVM"
date: 2011-07-11
forum: General Help
---

### Post by grw on 2011-07-11
Hi,

I have a brand new laptop, a Thinkpad E420 - Core i5 processor, 500GB harddrive, 4GB RAM
My problem: my computer won't boot. GRUB starts fine, but after that, the boot process hangs. I get a black screen.

When I try to start Ubuntu in recovery mode, the computer often hangs at this line:
[INDENT]eth0: no IPv6 routers present[/INDENT]
Or at this line:
[INDENT]type=1400 ..... apparmor="STATUS" operation="profile_load" name="usr/sbin/cupsd" pid=781 comm="apparmor_parser"[/INDENT]

I actually have a dual boot machine (well, I would have a dual boot if the thing would boot). I first installed fedora 15. I then installed Ubuntu 11.04 (using the alternate install CD). I followed these instructions for installing with Logical Volume Management (LVM): [http://www.linuxbsdos.com/2011/06/20...ioning-scheme/](http://www.linuxbsdos.com/2011/06/20...ioning-scheme/)

The computer started up fine in both distros a couple of times. (I fiddled, added a logical volume (partition), edited fstab....) But now I can't boot at all. Or rarely.

Fedora tends to hang after just after starting the plymouth daemon. The final line I get is this:
[INDENT]input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input6[/INDENT]
This seems to be described in this bug report: [https://bugzilla.redhat.com/show_bug.cgi?id=697932](https://bugzilla.redhat.com/show_bug.cgi?id=697932)

On one occasion, I got into recovery mode in Fedora and got something along these lines:
[INDENT]VFS: Can't find ext4 filesystem
... Bad magic number in super-block while trying to open /dev/mapper/fedora-home
... The super-block could not be read or does not describe the correct ext2 filesystem[/INDENT]

It's all very frustrating. I have a useless laptop.

I have already started a thread about this in a different forum: [http://ubuntuforums.org/showthread.php?t=1788772](http://ubuntuforums.org/showthread.php?t=1788772)
The advice I have received is that it's unlikely I have a BIOS or GRUB problem.

What am I to do to get my laptop going? Can anyone help diagnose the problem?

Gwyn
Edit/Delete Message

---

### Post by psusi on 2011-07-11
Press 'e' at the grub menu to edit the entry.  There should be a line near the top that says something about gfx payload.  Delete that line, then press ctrl-x to boot.  See if that helps.

You might also try changing the splash and quiet options on the linux line to nosplash and noquiet repsectively, and adding the nomodeset option.

---

### Post by grw on 2011-07-12
Deleting the gfx payload line allowed me to boot once. After that, I tried about 5 times and failed each time.

Adding nomodeset also led to a successful boot but with the old gnome desktop and not Unity. I ran update manager and rebooted. No problems. We will see....

---

### Post by grw on 2011-07-12
And now I can't boot at all.

I edited fstab so I could mount my fedora partition. After that, the computer won't start up.

I started up with a Knoppix live cd, changed fstab back the way it was, and the computer still won't boot.

---

### Post by psusi on 2011-07-12
The editing done in grub is not permanent, you will need to repeat it each time.  To make the changes permanent, you will need to edit /boot/default/grub.

Keep playing around the different combinations and try to see which ones work.  Try just the noquiet nosplash options and that should at least give a little more detail about what is going wrong before it gets stuck.

Do you have the proprietary video driver installed?

---

### Post by danodev on 2011-07-12
I have the same issue, I can boot successfully if I type in the nomodeset option, but then I don't get the new interface.  I'm not sure if I have a proprietary video driver in use or not.  I'm on a Lenovo T500 laptop.  Any more ideas?  What does it mean if the nomodeset option works?

thanks!
dan

---

### Post by psusi on 2011-07-12
> **danodev said:**
> I have the same issue, I can boot successfully if I type in the nomodeset option, but then I don't get the new interface.  I'm not sure if I have a proprietary video driver in use or not.  I'm on a Lenovo T500 laptop.  Any more ideas?  What does it mean if the nomodeset option works?

thanks!
dan

Does deleting the gfx_payload line instead of nomodeset work?

---

### Post by danodev on 2011-07-13
It does not work when I remove the gfx_payload line.

---

### Post by grw on 2011-07-13
I have no proprietry drivers installed.
I have integrated graphics and a separate switchable graphics card. VGA compatible controller: ATI ... Whistler [AMD radeon HD 6600M Series]

Been playing around.
Deleting the gfx payload line gets me nowhere. But replacing "quiet nosplash vt. handoff=7" with "nomodeset" does get me into gnome (not unity). I can't seem to get Unity desktop with nomodeset.

So with my computer running, update manager suggested some kernel updates. After install, the computer started correctly into the Unity desktop without nomodeset. (Is this all a kernel problem? The kernel was not updated to the latest version 2.6.39 - I have seen mention of booting problems being solved with the 2.6.39 kernel. I tried to install this kernel yesterday when I managed to get things running for a short time, but the kernel had been removed from kernel-ppa). 

In answer to danodev's question about nomodeset, see this post: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thank you for your help, psusi. I just hope once I fiddle and try to mount Fedora partitions and get my wireless working and so on that I don't have any further booting problems...

gwyn

---

### Post by danodev on 2011-07-13
I just updated to kernel 2.6.38-10-generic-pae from 2.6.38-8-generic-pae and still have the same issue.

---

### Post by psusi on 2011-07-13
nomodeset prevents the kernel from switching your display to high resolution, which prevents the open source video drivers from working.  The fallback VGA only driver can't support Unity.

So it seems to be a kernel problem.

---

### Post by grw on 2011-07-14
danodev, here are three different sets of instructions for upgrading to the 2.6.39 kernel. Might help.

[http://askubuntu.com/questions/51486/how-to-upgrade-to-a-2-6-39-kernel](http://askubuntu.com/questions/51486/how-to-upgrade-to-a-2-6-39-kernel)

---

### Post by danodev on 2011-07-14
I installed 2.6.39.3-candela and that worked for one boot, then I kept getting some strange kernel errors. Guess I'll just stick with the old kernel and wait...

Thanks for the help, suggestions!

---

