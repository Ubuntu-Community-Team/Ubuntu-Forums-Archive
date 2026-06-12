---
title: "streams of errors when booting up ubuntu 10.10"
date: 2012-02-17
forum: General Help
---

### Post by dragonfly41 on 2012-02-17
I've got a problem in my ubuntu 10.10 configuration which is in
/dev/sda7 -- root partition
/dev/sda8 -- home partition
I have Vista in other partition which can boot up o.k.

Ubuntu today showed lots and lots of of errors in black screen when booting and these were in chunks with a typical line in each chunk like this..

```

EXT4-fs error (device sda7): __ext4_get_inode_loc: (comm udisks-part-id) unable to read inode block 3670056

```

I narrowed this down by searching for this string .. [COLOR=Red]__ext4_get_inode_loc[/COLOR]

[http://ubuntuforums.org/search.php?searchid=85418821](http://ubuntuforums.org/search.php?searchid=85418821)

and this thread came close to the errors I'm seeing

[http://ubuntuforums.org/showthread.php?t=1851108&highlight=__ext4_get_inode_loc](http://ubuntuforums.org/showthread.php?t=1851108&highlight=__ext4_get_inode_loc)

....

Now I'm trying to launch Live CD and in fact this post is being sent by Live CD right now ..

but for some reason I can't click on **Try Ubuntu** in the Live CD install window to get to the full desktop to then inspect the sda7 partition.

This Live CD has worked many times before and today .. it's just stuck right now.   Just a roting icon seen as though attenpting to load but no disk activity seen,   esc does nothing.

Is there any way of forcing the **Try Ubuntu** onclick event from a stuck installer?  

All I have is firefox working and I only managed that by a fluke by clicking on the link [B]release notes

[/B]e.g. as well as browsing I can read files using firefox .. file:///etc/fstab

And then when I do get to gparted running .. I guess I could switch to booting up with PartedMagic instead of Live CD .. if I check the /dev/sda7 partition using GParted (with partition unmounted) is there a risk of losing data since I haven't backed up recent changes to ubuntu root partition?  Famous last words.

I guess that I need to run this command on the /dev/sda7 partition ...

```
  e2fsck -f -y -v   /dev/sda7
```

I suspect that my disk might be on the blink since I've seen bad sector messages in Vista ntfs partitions (even though Vista works .. so far).

---

### Post by dragonfly41 on 2012-02-17
Hello Houston.

I'm back into Live CD but I still can't get the **Try Ubuntu** to work to launch desktop.  Very strange.

Meanwhile instead of using ubuntu Live CD I booted up PartedMagic Live CD and got into Partition Editor.

I selected the suspect partition (/dev/sda7 -- root partition) and applied Partition > Check .. fingers crossed ..

The message came up .. operation completed .. I guess after running e2fsck .command ...

then I shut down and rebooted into ubuntu 10.10 kernel

error messages started to come up .. as it had before this exercise ..

```
init: plymouth main process (984) terminated with status 127
```but this time instead of a continuous stream of errors the bootup soon switched into tty1 console mode with error message at logon

```
/bin/login error while loading shared libraries libpam.so.0 no such file or directory
```I could not logon as user ..

This looks like a reinstall of ubuntu is needed ..  but although ubuntu is in separate root and home partitions when I've done this repair before (not reformatting) there is always something in root partition which is forgotten and lost or reset to defaults (e.g. Thunderbird last time).

I would prefer ubuntu to prompt when files are being deleted when I have to repair root / home partitions.

---

