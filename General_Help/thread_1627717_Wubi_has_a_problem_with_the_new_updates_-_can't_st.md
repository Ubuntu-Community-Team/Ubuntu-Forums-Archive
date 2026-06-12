---
title: "Wubi has a problem with the new updates - can't start grub"
date: 2010-11-21
forum: General Help
---

### Post by bsm2th on 2010-11-21
I have used this system for about a year, and am having problems only after the last update. Grub won't start with the message "can't find loadfont', and halts at that message. A post on a forum said that the problem was with the command name. In ubuntu it is 'font'. The problem comes when trying to change this. My system uses wubi, so..

           mkdir /win
           mount -tntfs /dev/sdb2 /win 
worked fine, and showed the windows files

           mkdir /linux
           mount /win/ubuntu/disks/root.dsk /linux
gave this error
NTFS signature is missing
Failed to sync device /dev/loop0: Input/output error
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS
Maybe the wrong device is used?

            mount -tloop /win/ubuntu/disks/root.dsk /linux
gave this
mount: mounting /dev/loop0 on /linux failed: No such device
I checked and there is a loop0 in /dev
Please help. I need this computer running Linux for a user list at the local foodbank. 

Thanks

Bob <bsm2th@gmail.com>

---

### Post by WorMzy on 2010-11-21
If you need linux, then why not install it normally: to a partition, instead of as an easily broken wubi installation? Unless there is a good reason not to, I recommend you do that ASAP. Wubi isn't meant to be used as a permanent OS, just as a way of trying out Ubuntu. But whatever, it's your PC, not mine. If you want to use Wubi, so be it.

You may, before mounting it, want to check the root disk for errors. So run (after mounting the windows partition)

```
sudo fsck /win/ubuntu/disks/root.disk
```

If that gives you any errors, ignore the rest of this post, and post them here.

Now, about mounting the root disk, in your original post, you said you tried:

> mount -tloop /win/ubuntu/disks/root.dsk /linux

That should be

```
sudo mount -o loop /win/ubuntu/disks/root.disk /linux
```

Note the space between the "-o" and "loop". loop is not an filesystem type, so don't use the -t flag.

I don't know where you'd go from there, as I don't use Wubi, or grub2. Hopefully the guide you mentioned can explain what you need to do, or, failing that, someone else on the forums can shed some light on a solution.

---

### Post by bcbc on 2010-11-21
Here's the post regarding getting around the loadfont and other grub errors affecting wubi. It's related to the 10.10 upgrade, but I've seen the loadfont errors with 10.04 grub updates as well. [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

Likely if you didn't upgrade then you'll have to manually edit the grub.cfg

---

