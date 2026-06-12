---
title: "UUID for non-hard drives?"
date: 2011-07-26
forum: General Help
---

### Post by RogerTX on 2011-07-26
I've done a bit of searching, and I didn't find an answer to a pretty simple question (or two):

I understand about UUID for hard drives, but are there UUIDs for CD-ROM devices? (including DVD, etc)?   How about for NFS mounts?

(I'm getting boot errors about the necessity of using UUIDs, but my /etc/fstab has UUIDs for all devices except for the CD-ROM and the NFS mount, which is what prompted my question)

---

### Post by bodhi.zazen on 2011-07-26
Can you post the exact error message you are getting as well as the contents of you fstab ?

---

### Post by RogerTX on 2011-07-27
> **bodhi.zazen said:**
> Can you post the exact error message you are getting as well as the contents of you fstab ?

I'll have to write down the error message; it happens during boot, and I can't seem to find it anywhere in /var/log (are there any other places to look?)

My fstab is below -- all devices except for the NFS mount and the CD-ROM have UUID values.

```

# /dev/sda3
UUID=1eff8b79-886c-431f-bafa-e227770fecce / ext3  defaults,errors=remount-ro,relatime 0 1
# /dev/sda9
UUID=f631ca0d-318e-4f3e-b630-b04800252e17 /home ext3    defaults,relatime 0 2
# /dev/sda1
UUID=07D7-0B10  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2
UUID=6A98F10A98F0D593 /media/sda2     ntfs    defaults,umask=007,gid=46 0 0
# /dev/sda8
UUID=b425c984-e918-4e72-8d8a-76a1a6b46b81 /tmp            ext3    defaults,relatime 0 2
# /dev/sda6
UUID=3e29ca99-766c-4430-aad2-ec2df8c3ac75 /usr            ext3    defaults,relatime 0 2
# /dev/sda7
UUID=fdcd16e3-97e5-46a9-b3e1-6c1fe70cf85f /var            ext3    defaults,relatime 0 2
# /dev/sda5
UUID=9e9d5352-fdf2-40bd-a4ca-691e6045feb5 none swap    sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
lhnas01:/c/media	/media/NAS nfs noauto,soft,intr,rsize=8192,wsize=8192 0 0


```

---

### Post by dino99 on 2011-07-27
run: sudo blkid

and compare with yours into fstab

---

### Post by bodhi.zazen on 2011-07-27
> **RogerTX said:**
> I'll have to write down the error message; it happens during boot, and I can't seem to find it anywhere in /var/log (are there any other places to look?)

boot messages are on /var/log/boot

---

### Post by RogerTX on 2011-07-29
> **bodhi.zazen said:**
> boot messages are on /var/log/boot

Nope; it's an empty file -- well, it says (Nothing has been logged yet)

---

### Post by RogerTX on 2011-07-29
> **dino99 said:**
> run: sudo blkid

and compare with yours into fstab

It could be that a number is wrong, but I would have expected a completely different message

(In general, the message is warning that a future version will use only UUID numbers, and I should update fstab).  Still working on getting the exact message.

---

### Post by RogerTX on 2011-08-09
OK, the error message is complaining about some files in /etc/udev/rules.d directory.

It says "SYSFS{} will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{} to match a parent device in /etc/udev/rules.d/45-libnjb5.rules:28"

---

### Post by bodhi.zazen on 2011-08-09
> **RogerTX said:**
> OK, the error message is complaining about some files in /etc/udev/rules.d directory.

It says "SYSFS{} will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{} to match a parent device in /etc/udev/rules.d/45-libnjb5.rules:28"

Well, that is a message that SYSFS is depreciated. It still should work , but in the future will not.

You do not need to do anything.

If you wish, you can edit /etc/udev/rules.d/45-libnjb5.rules and make the change on line 28 .

```
gksu gedit /etc/udev/rules.d/45-libnjb5.rules
```

On line 28 change SYSFS to either ATTR or probably ATTRS would be better.

---

### Post by dcstar on 2011-08-10
> **RogerTX said:**
> I've done a bit of searching, and I didn't find an answer to a pretty simple question (or two):

I understand about UUID for hard drives, but are there UUIDs for CD-ROM devices? (including DVD, etc)?   How about for NFS mounts?

(I'm getting boot errors about the necessity of using UUIDs, but my /etc/fstab has UUIDs for all devices except for the CD-ROM and the NFS mount, which is what prompted my question)

Physical **Partitions** have UUIDs, devices and external mounts (where the local OS has no access to any UUID info) do not.

---

### Post by RogerTX on 2011-08-10
> **bodhi.zazen said:**
> Well, that is a message that SYSFS is depreciated. It still should work , but in the future will not.

You do not need to do anything.

If you wish, you can edit /etc/udev/rules.d/45-libnjb5.rules and make the change on line 28 .

```
gksu gedit /etc/udev/rules.d/45-libnjb5.rules
```

On line 28 change SYSFS to either ATTR or probably ATTRS would be better.

I prefer a clean boot and it would be great to get rid of these warnings (I know that it's just a warning for the future)

However, what about the stuff in between the curly brackets?  Does that seamlessly change to ATTR? Or do I need to do some translation?  One line, for example, says:

```

SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4127", MODE="660", GROUP="audio"

```

---

### Post by RogerTX on 2011-08-10
> **dcstar said:**
> Physical **Partitions** have UUIDs, devices and external mounts (where the local OS has no access to any UUID info) do not.

Thanks... this answers my original question.

---

