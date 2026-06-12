---
title: "Grub &amp; HDD issue"
date: 2009-08-23
forum: General Help
---

### Post by Skippy_X on 2009-08-23
Hullo.

I've got a bit of a problem I hope someone in here can help me out on.

I work as a pc tech at a refurbishing shop. The other day we had an electrical storm that destroyed the Win2003 server upon which we kept software packages and drive images we use to perform installs. This is obviously a huge issue since w/out the server and the images it contained I'm relegated to doing reinstalls from CDs - which dramatically increases the amount of time I spend on an install.

My old server was assembled and installed by a guy from one of our other locations in another city. He didn't leave any install discs so building another windows server is out, and I don't know beans about configuring a windows server anyways.

I built a new box, put the drives from the windows server into it, installed Ubuntu 9.04 on a fresh set of drives, copied the data from the windows drives into /home/XXXXX/, installed samba and set up the shares. Then I removed the old server drives and installed two blank drives so I could have some more storage.

I've long been a Linux desktop user, but I know very little about working on networks. Generally, what hardware I was going to use was already in the computer upon which I installed Linux. I have never added a hdd to an existing system nor had to manually configure grub.


My problems:

1. The only OS present on this box is ubuntu 9.04, but grub still gives the option of booting either to Ubuntu or Win 2003. How do I eliminate that step from the startup process? I would like the system to boot straight to Ubuntu. 

The text of my /boot/grub/menu.lst is [here]("http://pastebin.com/m3bc30cd1") (links to pastebin).

2. I need to configure the fresh drives I put into the machine in place of the windows drives from the server. Right now the disk usage analyzer is only showing the two drives I installed linux onto - and those are almost full. How do I get "see" the two new drives and properly configure them so that they're usable?

---

### Post by loomsen on 2009-08-23
Hello.

Your menu.lst looks incomplete. I haven't been using debian for a while now, but I do remember the automagic for the grub menu.

Probably easiest to regenerate a menu.lst, cause, as far as I remember the double "##" in this file shall not be uncommented (cause the automagic script uses # to format everything)

That's why 
# default=vga=791
is read and executed if you run update-grub.

Generally, if you change anything in /boot/grub/menu.lst save and close the file, and then run 
update-grub
to trigger an update, otherwise your changes will be overwritten upon reboot.

So just generate a new one, 
```
aptitude reinstall grub 
```

or so should do.

2.)
fdisk -l 
will show any disks available. To format/configure a disk you may use fdisk, cfdisk, parted from command line, and, as always, it's reasonable to run
```
man <command>
i.e.:
man fdisk [man cfdisk|man parted] [COLOR="Navy"]#or any other utility[/COLOR]
```
before using <command> to physically change anything.

---

### Post by Skippy_X on 2009-08-23
Thank you very much, loomsen!

I will give it a go.

---

