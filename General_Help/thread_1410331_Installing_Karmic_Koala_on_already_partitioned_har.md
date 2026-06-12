---
title: "Installing Karmic Koala on already partitioned hard drive"
date: 2010-02-18
forum: General Help
---

### Post by xcrunner78 on 2010-02-18
I partitioned my hard drive on my computer with G-parted, the second partition (sda3) has data stored on it.  I use to have Karmic Koala on sda1, but something went wrong and I want to install it back on sda1.  How would I do this without losing my data on sda3?  When I use the live disc, it want to install it onto sda3.  I cannot figure out how to install it only on sda1.

Also, when I stored data, I want to store it on the sda3 partition.  I already have on that partition a /jason file which was my old Karmic Koala.

Thank you,
Jason

---

### Post by jpl888 on 2010-02-18
When in the installer you need to choose the option to manually partition. Then you will be able to keep sda3 intact.

Perhaps post a picture of the installer if you are not sure what to do then.

---

### Post by oldfred on 2010-02-18
with manual install you have to tell it which partition is / (root) adn what format to use and which is swap. If you have a separate /home you also have to tell it that but make sure not to format that partition.

[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

If your /Jason is just a data directory you do not have to specify it as part of the install but will have to mkdir, and mount it. If you want permanent mounting then you have to edit fstab.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Share data partition
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

---

### Post by xcrunner78 on 2010-02-19
Okay, let me try and I'll get back to you.

---

### Post by xcrunner78 on 2010-02-20
Ok, so i have it done finally!  Now another problem ariseds.

When I follow the directions on [http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html) this happens:

I did these steps and I'll put problems in quotes:

[B]mkdir mydata
[/B]**su**         "[FONT=Verdana][/FONT]su: Authentication failure after I put in my password"
**sudo mount /dev/sda3 /home/jason/mydata**
**chown -R carla:carla  /home/carla/mydata   "**changing ownership of `/home/jason/mydata': Operation not permitted...this happened at each ownerships[B]"


[/B]So I stopped right there before I do anything else wrong.

Any suggestions will be grealy appreciated!

---

### Post by xcrunner78 on 2010-02-20
Okay, got it to work...I inserted sudo before the chown and it worked.

But, when I restart the computer, the other partition is still not automatically mounting...even after I gedit /etc/home

---

### Post by jpl888 on 2010-02-20
Here is my /etc/fstab see if that helps:-

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=c2f21413-fc90-4751-9362-a0833b750067 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=204f6cfa-05e8-4fad-868e-8d692b2643b5 /boot           ext2    defaults        0       2
# /home was on /dev/sda3 during installation
UUID=ba4562c0-3651-410a-b3d8-108b75908648 /home           ext3    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by oldfred on 2010-02-21
You manuallly mounted but now if you want to permanently mount it, you need to modify fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

You can mount with device (sdax, UUID or label)

To see UUIDs
sudo blkid

my entry for my data partition:

# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2

---

