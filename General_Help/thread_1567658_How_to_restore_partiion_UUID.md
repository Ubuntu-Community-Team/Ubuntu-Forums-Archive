---
title: "How to restore partiion UUID?"
date: 2010-09-04
forum: General Help
---

### Post by printfw on 2010-09-04
After installing another OS on second drive, UUID for swap on my main system was missing. In other words there is no appropriate symlink in */dev/disk/*. I've tried to create it manually, but it dissappears again after rebooting. Temporarily i solved this problem by adding in */etc/fstab* direct address to swap device. The question is how to restore UUID for swap partition correctly?
Here some things that could be helpful to understand a problem:
```
sudo blkid /dev/sda6
/dev/sda6: TYPE="swap"
```
*/dev/sda6* is swap partition.
Also i've tried to use *tune2fs*:
```
sudo tune2fs /dev/sda6 -U uuid_generated_by_uuidgen
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Bad magic number in super-block during try to open /dev/sda6
Couldn't find valid filesystem superblock.
```

---

### Post by louieb on 2010-09-04
Wonder what happened to the UUID?

anyway try the mkswap command - that should generate a new UUID.  
```
mkswap /dev/sda6 
```

If the other OS is Solaris or BSD - see the waring in the man pages.

---

### Post by SPr on 2010-09-04
> **printfw said:**
> After installing another OS on second drive, UUID for swap on my main system was missing.

Swap space has no UUID*. What's wrong with using /dev/sda6 in /etc/fstab?

My PC:
```

cat /etc/fstab|grep -i swap
/dev/hda3       none            swap    sw              0       0

ls -l /dev/disk/by-uuid/|grep hda3

blkid|grep hda3
/dev/hda3: TYPE="swap"

```

If you have two OS on two different drives in the same computer they can both use the same swap partition.

*Apparently from what I've Googled it can be forced though I'm not sure what the benefits would be.

---

### Post by printfw on 2010-09-04
> **louieb said:**
> Wonder what happened to the UUID?

anyway try the mkswap command - that should generate a new UUID.  
```
mkswap /dev/sda6 
```

If the other OS is Solaris or BSD - see the waring in the man pages.
Thanks, it helped. Other OS is Debian, and I think Debian installation program has marked /dev/sda6 as swap for new OS. I didn't notice that.

> **SPr said:**
> Swap space has no UUID*.
It may have it. My /etc/fstab:
```
...
UUID=d94014cb-a184-4341-a106-037f30c74656  none            swap  sw                                    0  0
...
```
```
sudo blkid /dev/sda6
/dev/sda6: UUID="d94014cb-a184-4341-a106-037f30c74656" TYPE="swap"
```

> **SPr said:**
> What's wrong with using /dev/sda6 in /etc/fstab?
Nothing wrong, it's just not default in ubuntu.

> **SPr said:**
> If you have two OS on two different drives in the same computer they can both use the same swap partition.
They can. But I have some doubts about correct work of hibernate mode.

---

