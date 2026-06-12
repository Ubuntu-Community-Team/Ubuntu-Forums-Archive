---
title: "Replace Linux Mint with Ubuntu?"
date: 2011-12-01
forum: General Help
---

### Post by Benhermies on 2011-12-01
Ok here's the situation.  I tried out the new version of Ubuntu on a Live USB and I REALLY like it!  I think the new Unity interface rocks!  On my computer I currently dual-boot between Windows 7 and Linux Mint 9.  I would like to just replace Linux Mint with Ubuntu and still be able to access Windows, and make it as painless as possible.  Is that possible without having to re-install Windows?  Please help!

---

### Post by DapperMe17 on 2011-12-01
Yes, it's easy. 

Load the Live CD or DVD, and during the installation process, install Ubuntu on the partition that currently holds Linux Mint.

---

### Post by Benhermies on 2011-12-01
If I just install it over top will it just over-write all the files or do a fresh install?  I'd prefer the fresh install.  I don't have any vital data on my Linux partition.

---

### Post by Linuxratty on 2011-12-01
> **Benhermies said:**
> If I just install it over top will it just over-write all the files or do a fresh install?  I'd prefer the fresh install.  I don't have any vital data on my Linux partition.

 Just install it over Mint,it should go fine.

---

### Post by DapperMe17 on 2011-12-01
Yes, it will overwrite all. You can also choose to reformat that partition in the installer, as an overwrite, prior to installing.

---

### Post by grahammechanical on 2011-12-01
So, you REALLY like Unity? Or are you joking us? We are not used to compliments like that.

Just mark the Linux Mint partition to be formatted and the files will not survive the install. And if you leave the Windows partitions alone everything will be fine. Just like when you set up the dual boot with Windows and Linux Mint.

---

### Post by vasa1 on 2011-12-02
> **DapperMe17 said:**
> Yes, it will overwrite all. You can also choose to reformat that partition in the installer, as an overwrite, prior to installing.

If the OP is a newbie, I wouldn't offer that advice. The simple "install over Mint" is safer as Linuxratty suggested.

---

### Post by critin on 2011-12-02
> If I just install it over top will it just over-write all the files or  do a fresh install?  I'd prefer the fresh install.  I don't have any  vital data on my Linux partition.

It's easy--over-writing is a fresh install.  Let the installer do its thing and it will be fine.  Just be sure to choose the right partition.

---

### Post by ernestj on 2011-12-02
I think a lot of people prefer Unity of GNOME 3. If I had to choose Ubuntu 11.04 or Mint 12, I would take Ubuntu 11.10.

---

### Post by Inversius on 2011-12-10
Not sure replacing Mint with Ubuntu is quite so straight forward with the 11.10 installer (or maybe I did something wrong?). I've recently done exactly this (replaced Mint with Ubuntu-welcome back old friend!). When I started the installer, I was presented with three choices. The first ( side by side install) automatically chose the Mint (ext4) partition, but wanted to split this between Mint and Ubuntu, the only choice was the relative partition size allocated to each. The second option was the disk wipe (nooooo!) and the third was the 'something else' partition management option. After a bit of messing around, I chose this option, selected the ext4 partition, ticked the format box then double click and selected ext4... for 'Use as' and the / option for the mount point (so mounting is done with reference to the Root, otherwise the installer gets all bitter and twisted about it...). Hit install now after this and all was smooth sailing. Is there really a simpler way?

BTW I found Mint12 to be buggy and unstable. Screen hash, hang-up on shut down and twice the whole thing crashed (froze) and had to be restarted. 'Clean and refreshing' I found to be ugly and boring (just to put the final boot in!). If you want a featureless (in all senses) anaemic version of Ubuntu, by all means try it. Me, I've finally learned to stop worrying and love the Unity ;)

---

