---
title: "So, I think I've buggered grub up :( (bash editing?)"
date: 2010-08-18
forum: General Help
---

### Post by demonmagus on 2010-08-18
Please see the last post for the current problem :(

Hey all, I'm dual booting ubuntu with xp, I do not have xp installation disks though (lost).

Basically, when I switched my comp. on there was a grub rescue problem. However, now the problem is of that where it says "minimal bash like editing is supported" and honestly I've no idea what to do.

I've got a live CD so I tried reinstalling grub (says it went fine?) but the same thing happens.

So, I found this...

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

But when I try sudo fdisk -1 the terminal says that '1' is an invalid option 0_o

I'm in such a jam and as you've gathered, very new to this.


Thanks!

---

### Post by dabl on 2010-08-18
> **demonmagus said:**
> 

But when I try sudo fdisk -1 the terminal says that '1' is an invalid option 0_o



That's not the number one, that's a lowercase letter "L".

---

### Post by demonmagus on 2010-08-18
> **dabl said:**
> That's not the number one, that's a lowercase letter "L".

Haha oh deary me.

Thanks :). However just to make sure, on that page I linked it said remember which device is your linux distribution... I assume it's the one that isn't Linux Swap/ Solaris?

And it also says if I have boot on a different partition that'll have to be loaded as well? How would I know if this is the case.

---

### Post by demonmagus on 2010-08-18
Oh, a bit futher down it says:
When that is done you need to run update-grub to create the configuration file. If you have a separate /boot partition you need to mount it first!
$ update-grub

To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda
$ grub-install /dev/sda

If you encounter any errors, try grub-install --recheck /dev/sda
$ grub-install --recheck /dev/sda

Now where it says you must mount the /boot - does that mean do it again or..?

---

### Post by demonmagus on 2010-08-18
Ok I've entered this chroot and typed everything as stated. Nothing seems to happen, it just prints the line...

However, how on earth do I exit chroot? It says ^X so I've tried typing it, typing exit...

Nothing!

---

### Post by hudsonl on 2010-08-18
> **demonmagus said:**
> Ok I've entered this chroot and typed everything as stated. Nothing seems to happen, it just prints the line...

However, how on earth do I exit chroot? It says ^X so I've tried typing it, typing exit...

Nothing!


Reboot by typing ...

> shutdown -r now

---

### Post by demonmagus on 2010-08-18
> **hudsonl said:**
> Reboot by typing ...

> shutdown -r now

Thanks, it hasn't really done anything =/

---

### Post by oldfred on 2010-08-18
Are you at a grub rescue prompt, or have you booted into the command line?

At grub rescue you should manually boot.

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hdX,Y)
      linux /vmlinuz root=/dev/sdXY ro
      initrd /initrd
      boot

---

### Post by demonmagus on 2010-08-18
> **oldfred said:**
> Are you at a grub rescue prompt, or have you booted into the command line?

At grub rescue you should manually boot.

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hdX,Y)
      linux /vmlinuz root=/dev/sdXY ro
      initrd /initrd
      boot

Sorry, now there is no grub rescue, it just gives me that message in the first post with

Grub>

Thanks

---

### Post by oldfred on 2010-08-18
While the full chroot is sometimes required, the simplified version usually works with grub2.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change [COLOR=Red]sda5[/COLOR] if not correct.
```
sudo fdisk -l
sudo mount /dev/[COLOR=Red]sda5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```If that returns any errors run:
```
sudo grub-install --recheck --root-directory=/mnt /dev/sda

```You can copy & paste these commands - one at a time. You only have to change the [COLOR=Red]sda5[/COLOR] if the fdisk says linux is on a different partition.

---

### Post by demonmagus on 2010-08-18
> **oldfred said:**
> While the full chroot is sometimes required, the simplified version usually works with grub2.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change [COLOR=Red]sda5[/COLOR] if not correct.
```
sudo fdisk -l
sudo mount /dev/[COLOR=Red]sda5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```If that returns any errors run:
```
sudo grub-install --recheck --root-directory=/mnt /dev/sda

```You can copy & paste these commands - one at a time. You only have to change the [COLOR=Red]sda5[/COLOR] if the fdisk says linux is on a different partition.

Thank you, I'll have to try it tomorrow since my keyboard has also decided to die! Hah.

---

