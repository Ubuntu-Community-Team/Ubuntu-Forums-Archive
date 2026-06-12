---
title: "error: invalid arch independent ELF magic Precise Pangolin 12.04"
date: 2012-04-26
forum: General Help
---

### Post by MorrisseyJ on 2012-04-26
Hi, 

Just a note in case this is helpful for people just installing.

After my install i reboot off the hard drive but instead of being met with GRUB, i encounter

> error: invalid arch independent ELF magic
grub rescue >This is the same problem as i had under 11.10

I solved it here: [http://ubuntuforums.org/showthread.php?t=1870369&page=3](http://ubuntuforums.org/showthread.php?t=1870369&page=3)

For my partitions the solution remains: 

1. Boot to the live CD/USB
2. Open a terminal and enter the following: 
> sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda                      3. Reboot and you'll be greeted by a GRUB screen.

As far as i can tell this solution should work as long as you replace the partition (sdxy - sda5 in my case) with the partition in which your main install sits - GParted should tell you this or you can run > sudo fdisk -l

Hope this helps someone.

Oh, and 12.04 looks great: wonderful work developers.

---

### Post by cacycleworks on 2012-06-19
This post is on top of google search for "error: invalid arch independent ELF magic"...

Already booted to liveCD... found this post... as written above, the grub-install needs --force option to work.

```
$ sudo grub-install --force --boot-directory=/mnt /dev/sda 
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
ubuntu@ubuntu:/$
```

... will update until solved for me.

Anecdotally, I did NOT install Ubuntu my normal way because the installer said with UEFI booting, do something different blah blah blah, and so I do the first round of updates and get the above present on 1st reboot. 

I know everyone is officially super happy with Ubuntu, but with each new LTS, it seems things are less reliable and more and more unfuxoring is required on my part. Previously, I blamed it on 2 to 4 year old computers. This happened on brand new Core i7.

**Didn't work.** Now booting from USB stick; much faster than CD!

---

### Post by YannBuntu on 2012-06-19
Hi
As your disk is GPT, you need either a BIOS-boot or a EFI partition.

Please indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") if you want more details.

---

### Post by cacycleworks on 2012-06-19
Wow, so I did all this: [http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html)

The system saw my ubuntu installation and booted to it (after more ELF errors)

I did as the link said about installing boot-repair. I type it, nothing happens for a few seconds, then the prompt comes back. I also tried sudo boot-repair and gksudo boot-repair and gksu boot-repair.

---

### Post by YannBuntu on 2012-06-20
**@cacycleworks:** strange. What does "sudo boot-repair -d" return? you can also use it from Boot-Repair-Disk or Ubuntu-Secure-Remix.

---

### Post by cacycleworks on 2012-06-20
[FONT="Courier New"]$ sudo boot-repair -d

** (glade2script:11501): WARNING **: Command line `dbus-launch --autolaunch=a7bad5f6f122f15a4b6662cb00000003 --binary-syntax --close-stderr' exited with non-zero exit status 1: No protocol specified\nNo protocol specified\nAutolaunch error: X11 initialization failed.\n
No protocol specified
No protocol specified
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 49, in <module>
    from gi.repository import Gtk
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module
    dynamic_module._load()
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 224, in _load
    overrides_modules = __import__('gi.overrides', fromlist=[self._namespace])
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py", line 1533, in <module>
    raise RuntimeError("Gtk couldn't be initialized")
RuntimeError: Gtk couldn't be initialized
[/FONT]

---

### Post by YannBuntu on 2012-06-20
Thanks. I reported the bug here: [https://bugs.launchpad.net/glade2script/+bug/1015643](https://bugs.launchpad.net/glade2script/+bug/1015643)

Do you have the same problem when using Boot-Repair-Disk (without updating its packages) ?

---

### Post by cacycleworks on 2012-06-20
The first time I've tried boot repair was in this thread. It doesn't do anything for me...

---

### Post by YannBuntu on 2012-06-21
Until now, you tried Boot-Repair installed on a Ubuntu 12.04 CD, didn't you?

If yes, please could you create a CD or live-USB of [Boot-Repair-Disk]("http://ubuntuforums.org/showpost.php?p=11181195&postcount=1") (which is a Debian CD with Boot-Repair pre-installed), then boot on it, and tell me if the window below appears?
[[img]http://pix.toile-libre.org/upload/thumb/1340262772.png[/img]](http://pix.toile-libre.org/?img=1340262772.png)

If it does not appear, please open a terminal, type "boot-repair" and tell me the output.
[[img]http://pix.toile-libre.org/upload/thumb/1340262851.png[/img]](http://pix.toile-libre.org/?img=1340262851.png)

I ask this because Boot-Repair on 12.04 is a GTK3 version, while on Boot-Repair-Disk it is a GTK2 version, so i wonder if you have the same bug on the GTK2 version.

---

