---
title: "Why did swap space disappear ?"
date: 2009-12-04
forum: General Help
---

### Post by lostinxlation on 2009-12-04
Hi,
I had Xubuntu 9.10 on my PC and it had swap space of 500MB. I installed Slackware yesterday and specified that 500MB space for slackware swap area. I expected that both of Xubuntu and Slackware could share the same swap area, but I found the swap space on Xubuntu was 0k according to "top" output, so obviously Xubuntu is missing swap space.
Is there any way to share the swap space between 2 linux OSs(particularly slackware and Ubuntu) ?

---

### Post by fallingleaf on 2009-12-04
You need to explicitly put the swap partition in /etc/fstab on your Xubuntu install.

---

### Post by RedSquirrel on 2009-12-04
When you installed Slackware, its installer created a swap space with the 'mkswap' command. This changed the UUID of the swap partition. On Slackware, that doesn't matter because it refers to the swap space by its device node, /dev/sda2 or /dev/hda2 or whatever.

Xubuntu uses UUIDs, so you will have to fix **/etc/fstab** on your Xubuntu installation to reflect the changed UUID for your swap partition.

```
ls -l /dev/disk/by-uuid/
```should show you the UUIDs for your system.

Alternatively, you could refer to the swap partition in Xubuntu's **/etc/fstab** using the partition's device node (/dev/sda2 or /dev/hda2, ...) instead of using the UUID.

---

### Post by egalvan on 2009-12-05
> **fallingleaf said:**
> You need to explicitly put the swap partition in /etc/fstab on your Xubuntu install.

the OP stated that 
> I had Xubuntu 9.10 on my PC and it had swap space of 500MB

so the swap partition is already in his fstab; although the UUID could have been changed... see next.


> **RedSquirrel said:**
> When you installed Slackware, its installer created a swap space with the 'mkswap' command. This changed the UUID of the swap partition.


again, swap partition already existed, so unless the Slackware install explicitly re-sized or removed/replaced the partition, it should exist with the same UUID.


run these codes and paste the results here, so we can check what is going on.

this will show all devices and their UUID, along with extra info.
```
sudo blkid
```


this shows devices that are/should be mounted.
```
gedit /etc/fstab
```


NOTE.... if the UUID was changed, it IS NOT a simple matter of just changing the UUID in the fstab!!

initramfs and a "resume" file need to be changed, as well...

On your Xubuntu install, the fstab should have the original UUID of the swap partition...
 make sure you save this information!
it's MUCH easier to re-write the original UUID, than to regenerate the initramfs and change the files...

Of course, Slackware may then complain,
BUT if it uses hdx/sdx type of identification, all will be well...

---

### Post by RedSquirrel on 2009-12-05
> **egalvan said:**
> again, swap partition already existed, so unless the Slackware install explicitly re-sized or removed/replaced the partition, it should exist with the same UUID.

The Slackware installer creates swap space by running mkswap. The default behaviour of the mkswap command is to generate UUIDs. Hence, even if you specify the same partition should be used for swap, you will end up with a new UUID. If you are running mkswap *manually* (that is, not as part of some installer program), then you can specify the UUID with the -U option.

---

### Post by lostinxlation on 2009-12-05
Thanks.
 
So, installing Slackware on the system that Ubuntu is already in messed up the swap space for Ubuntu, and it got me curious what would happen if I installed Xubuntu on the system where slackware already existed.. So, i tried it.
 
I made one more 500MB swap space,which made it two 500MB swap spaces(one is accessable by slackware at that point and another is a brand new partition) in the HDD. I installed Xubuntu and the end result came out with 500MB swap for slackware and 1000MB for Xubuntu.

---

