---
title: "Directories in /Boot disappear on reboot"
date: 2010-05-30
forum: General Help
---

### Post by mceniry on 2010-05-30
Hi,
  When I installed 9.10 I decided to allocate a /Boot partition. After noticing that
I was wasting a lot a space in /Boot I decided to move some directories over
to that partition from /Home. Every once and a while those directories disappear
on reboot. If I then re-reboot they come back (most of the time). Am I doing
something I shouldn't? Is there a way to set the directories to show permanently?
Here's my fstab entry for that partition:

# /dev/sda2
UUID=xxxxxxxxxxxxxxxxxxxx /boot           ext2    relatime        0       2

---

### Post by Bachstelze on 2010-05-30
First, Unix filesystems are case-sentitive. It's /boot and /home, not /Boot and /Home.

And I'd say that yes, you are doing something you shouldn't: moving files where they shouldn't be. /boot is supposed to contain only the files needed to boot the system (kernel images, boot loader, etc.), while /home contains the users' personal files.

That being said, it shouldn't make the files you put in /boot disappear, even if they have nothing to do there. Are you really sure they aren't there? What does a [font=monospace]ls /boot[/font] gives?

---

### Post by Jeroensum on 2010-05-30
Could you post the contents of your /etc/fstab ?
This could help us troubleshoot potential mistakes in it :)

---

