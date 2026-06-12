---
title: "Moving my /home folder to a different drive/partition?"
date: 2010-04-26
forum: General Help
---

### Post by HHx66 on 2010-04-26
I was thinking of moving my /home folder to a different drive/partition, is there an easy way to do it without formatting and reinstalling?

---

### Post by thebigob on 2010-04-26
yes this is really simple.

firstly move you homedir to where ever you want

then create a sym link to this in the loot directory:

eg;
```

mv /home /media/disk/whatever

cd /

ln -s  /media/disk/whatever/home

```


This moves the actual folder to another disk.

This then creates a redirect so anyone accessing /home is automatically redirected to your new location.

This means that any existing links to your homedir etc wont break whilst still moving all the content to another device.

Let me know how you get on.

PLEASE NOTE BEFORE DOING ANYTHING LIKE THIS YOU SHOULD ENSURE YOU BACK UP ANY VITAL INFORMATION!

---

### Post by HHx66 on 2010-04-26
I'll make a partition image first before I try it, I'll post back the results later tonight. I can't do it at the moment as I have class soon.

---

### Post by srs5694 on 2010-04-26
If you plan to devote the entire partition to /home, I strongly recommend that it be mounted at /home via an appropriate entry in /etc/fstab, rather than creating a symbolic link. The symbolic link just complicates matters unnecessarily. Here's a sample /etc/fstab entry:

```

UUID=3a00a023-c58b-4dff-963a-365e399b5982        /home    reiserfs       defaults        0 2

```

Of course, you should change the UUID value for your system (use blkid to find it) or specify the device as a device filename (/dev/sda2, /dev/hdb7, or whatever) and change the filesystem type code (reiserfs in this example) as appropriate for your system.

There are quite a few Web-based tutorials on this topic, such as these: [one](http://linuxtipstricks.wordpress.com/2008/10/05/how-to-create-a-separate-home-partition-in-linux-ubuntu-opensuse-mandriva-gentoo-fedora-and-so-on/), [two](http://www.psychocats.net/ubuntu/separatehome), and [three.](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/) I just found these in a Google search. I've not read them in detail, so I can't say how good any of them are.

---

### Post by oldfred on 2010-04-26
I use the psychocats (link2 in srs5694) instructions to move my /home. It worked just fine.

At the end of her instructions is mention of the possibility of dmrc errors.
This has instructions in case you get an error.
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

