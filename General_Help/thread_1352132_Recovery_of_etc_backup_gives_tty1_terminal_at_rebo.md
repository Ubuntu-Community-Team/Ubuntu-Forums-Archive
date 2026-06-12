---
title: "Recovery of /etc backup gives tty1 terminal at reboot"
date: 2009-12-11
forum: General Help
---

### Post by OldGrantonian on 2009-12-11
I have dual-boot WinXP and Karmic.

When I reboot from a GUI session, I'm presented with the tty1 login console. "startx" does not work.

My Ubuntu experience is only one month old. So I've only a few of my own files. These are backed up to external HDD.

As part of my "disaster recovery" planning, I've done several re-installs of Ubuntu, followed by several restores of external HDD backups.

Here is a typical re-install sequence:

•  Re-install. Reboot. All OK.
• Install updates. Reboot. All OK.
• Use grsync to restore /etc from HDD backup.
• Reboot. This is when I get the tty1 login screen.

Why is the /etc restore causing the tty1 screen to launch, rather than the GUI?

---

### Post by viralmeme on 2009-12-11
> **OldGrantonian said:**
> I.. Why is the /etc restore causing the tty1 screen to launch, rather than the GUI?

Why the need to restore /etc if you've done a reinstall. /etc usually contain configuration settings. What exactly is on /etc that you need ?

---

### Post by OldGrantonian on 2009-12-11
> **ymitchell said:**
> Why the need to restore /etc if you've done a reinstall. /etc usually contain configuration settings. What exactly is on /etc that you need ?

I'm simply practising for a "disaster recovery" while I still have only a few files to back up :)

A google article said that I should back up the following directories:

/etc
/home
/usr/local
/var

So, after a re-install, I'm restoring these directories one at a time, followed by a reboot after each restore, so that I can isolate any problems.

BTW: I'm no techie, but I assume that each time I install an application from Synaptic Package Manager, then stuff will be added to /etc and other directories.

For example, I've added "Wine" since my first install of Ubuntu. So I'm assuming that by restoring the above directories, I won't need to re-install Wine. Maybe you don't agree with that? If so, please say so. This seems to me like a friendly forum :)

In a year's time, when disaster occurs, I don't want to have to re-install Wine, plus all the other applics that I've installed. If you know of a better solution, I would be most grateful for your input :)

---

### Post by viralmeme on 2009-12-15
Are you trying to restore from a running system, if so that maybe your problem. Boot from a CD and then run your restore ..

---

### Post by muteXe on 2009-12-15
just thought i'd mention this here, mine 8.04 randomly boots up into tty1 as well. I'd say about 30% of the time.  Very weird.

---

### Post by OldGrantonian on 2009-12-15
Thanks for the responses.  I've solved the problem :)

BTW: It's better for my recovery to fail now, when I have only a few files to back up. If I wait for one year, and then find an error, I'm going to be annoyed :)

Here's the problem. I'm trying out grsync (front-end for rsync). I'm sure I'll try other backup tools later.

With rsync, you need to back up sym links as sym links if you want to "archive", which is what I want to do.

I had no idea what sym links are. Now I know :)

When I preserve sym links in rsync, I can restore /etc without problems :)

---

