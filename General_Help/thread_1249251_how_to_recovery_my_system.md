---
title: "how to recovery my system"
date: 2009-08-25
forum: General Help
---

### Post by fanglinyong on 2009-08-25
hello ,everybody
i installed two kernels in my system, the ones version is 2.6.28,and the other is 2.6.30.
today , i use the code like this :
```
dpkg --get-selections|grep linux
sudo apt-get autoremove linux-image-2.6.30-*****

```after i reboot my pc, i remember that i had uninstall my older kernel2.6.28!
now ,i can't use my system !
who can tell me how to do ?

---

### Post by P4man on 2009-08-25
Heh, who needs a kernel ? :p

I guess you could boot from a liveCD, then chroot to your install and then reinstall a kernel.

---

### Post by nothingspecial on 2009-08-25
Whoops :shock:

Even I`ve never done that! You have no kernel?

Boot from a live cd and copy all your data. You could try making a seperate home partition and then reinstall, that way you`d keep all your settings.

Or you could try [[COLOR="Magenta"]this[/COLOR]]("http://maratux.blogspot.com/2009/03/oops-removed-all-kernels.html")

---

### Post by fanglinyong on 2009-08-25
without reinstall the sytem ,
no way to resuce my system????

---

### Post by unutbu on 2009-08-25
Boot from the LiveCD.
Open a terminal (Applications>Accessories>Terminal), and type
```

sudo mount /dev/sdaX /mnt  
```

Note that you must change sdaX to the appropriate device name for your Linux partition. 
If you do not know what the device name is, type
```

sudo fdisk -l

```
to list the partition table. (Note that "-l" is a dash followed by a lowercase L.)

Then type:
```

cd /mnt
sudo mount --bind {/,}proc
sudo mount  --bind {/,}sys
sudo mount  --bind {/,}dev
sudo chroot /mnt
grep -v rootfs /proc/mounts> /etc/mtab
apt-get install linux-image-2.6.28-generic
```

If at any stage you run into trouble or have questions, please post the complete terminal output.

---

### Post by P4man on 2009-08-25
Who said that ? I gave you the very short answer, nothingspecial gave you [_a very nice link that describes the process in detail_]("http://maratux.blogspot.com/2009/03/oops-removed-all-kernels.html"). 

You can follow that line for line (ubuntu or kubuntu doesnt matter), you will just have to adjust the 5 in "# mount /dev/sda[COLOR="Red"]5 [/COLOR]/mnt/tmp" with whatever partition your ubuntu is on.

edit: unutbu beat us to it I guess :)

---

### Post by nothingspecial on 2009-08-25
Try the pinky/purple link I posted.

---

### Post by blueridgedog on 2009-08-25
+1 on boot from live and use chroot.

This example assumes your root partition is sda1, change/adjust to suit your system:

Boot on a LiveCD then:

```
sudo mount --bind /dev /media/sda1/dev
sudo chroot /media/sda1
```

Then use apt-get to install the kernel you want.

(unutbu posted while I was typing...)

---

### Post by fanglinyong on 2009-08-25
thanks for everyone's reply,I will try ,and then ,give you my result!

---

### Post by fanglinyong on 2009-08-25
> **unutbu said:**
> Boot from the LiveCD.
Open a terminal (Applications>Accessories>Terminal), and type
```

sudo mount /dev/sdaX /mnt  
```Note that you must change sdaX to the appropriate device name for your Linux partition. 
If you do not know what the device name is, type
```

sudo fdisk -l

```to list the partition table. (Note that "-l" is a dash followed by a lowercase L.)

Then type:
```

cd /mnt
sudo mount --bind {/,}proc
sudo mount  --bind {/,}sys
sudo mount  --bind {/,}dev
sudo chroot /mnt
grep -v rootfs /proc/mounts> /etc/mtab
apt-get install linux-image-2.6.28-generic
```If at any stage you run into trouble or have questions, please post the complete terminal output.
ok ,first thanks your help!
when i ex the last command:```
 apt-get install linux......
```, the terminal said 
can't find the package linux-image-2.6.28-generic;

---

### Post by fanglinyong on 2009-08-25
> **blueridgedog said:**
> +1 on boot from live and use chroot.

This example assumes your root partition is sda1, change/adjust to suit your system:

Boot on a LiveCD then:

```
sudo mount --bind /dev /media/sda1/dev
sudo chroot /media/sda1
```Then use apt-get to install the kernel you want.

(unutbu posted while I was typing...)
sorry, your method needs a cd ,but i don't have !
i installed my system from hdd!!not from cd-rom!!!
thanks your help!!!

---

### Post by unutbu on 2009-08-25
fanglinyong, my mistake. Try 
```

apt-get install linux-image-2.6.28[COLOR="Red"]-15[/COLOR]-generic
```

PS. I am a little confused. blueridgedog and I both posted roughly the same instructions. Both called for you to boot from the LiveCD. 
If you do not have a CD-ROM drive, then how did you accomplish my instructions?

---

### Post by fanglinyong on 2009-08-25
> **unutbu said:**
> fanglinyong, my mistake. Try 
```

apt-get install linux-image-2.6.28[COLOR=Red]-15[/COLOR]-generic
```PS. I am a little confused. blueridgedog and I both posted roughly the same instructions. Both called for you to boot from the LiveCD. 
If you do not have a CD-ROM drive, then how did you accomplish my instructions?
i download the iso file, and then reboot my pc from hdd!

---

### Post by fanglinyong on 2009-08-26
i used ubuntu-desktop9.04,its kernel's version is 2.6.28-11,so ,i use this code 
```
 apt-get install linux-image-2.6.28-11-generic
```
now ,it works good!
at last, thanks everyone who help me !

---

### Post by P4man on 2009-08-26
> **fanglinyong said:**
> i download the iso file, and then reboot my pc from hdd!

Can you explain how to do that? You used grub to boot off an ISO file? I heard its possible but never found how to do it.

---

### Post by unutbu on 2009-08-30
P4man, here is one way to boot from ISO: [http://ubuntuforums.org/showthread.php?t=457318](http://ubuntuforums.org/showthread.php?t=457318)

---

### Post by fanglinyong on 2009-09-13
at last, thanks everyone's help!

---

