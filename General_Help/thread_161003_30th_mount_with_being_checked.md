---
title: "30th mount with being checked"
date: 2006-04-16
forum: General Help
---

### Post by soongwoo on 2006-04-16
Is there a way to control the running fsck on other than root partition
at boot time? In addition to that, interval, too.

I could not find the posting that someone said the frequency and interval
for running fsck at boot time are configurable.

Thanks in advance
soongwoo

---

### Post by ubernoob on 2006-04-16
You can change the last digit from "0" to "1" for filesystem, or "2" for everything else. It is the sequence that it will be checked.

---

### Post by GilGalad on 2006-04-16
Do 'man tune2fs':

   tune2fs - adjust tunable filesystem parameters on ext2/ext3 filesystems

The option you want is '-c'

---

### Post by ubernoob on 2006-04-16
[QUOTE=ubernoob]You can change the last digit from "0" to "1" for filesystem, or "2" for everything else. It is the sequence that it will be checked.[/QUOTE]

I realised that this was not a good answer. I meant in /etc/fstab ;)

---

### Post by soongwoo on 2006-04-18
Thanks. You mean change the last digit to "1" in /etc/fstab,
if the partition with "1" will be fschecked after the boot.

Am I right?

soognwoo

---

### Post by soongwoo on 2006-04-18
If a command like "tune2fs -c 1 /dev/hda1" is executed then
the /dev/hda1 would be checked every boot.
Am I right?

soongwoo

---

### Post by ubernoob on 2006-04-20
[QUOTE=soongwoo]Thanks. You mean change the last digit to "1" in /etc/fstab,
if the partition with "1" will be fschecked after the boot.

Am I right?

soognwoo[/QUOTE]


Both "1" and "2" will be checked. The only diffrence is the order. Thats why root partition should be "1". You need to check that first.


> 	If a command like "tune2fs -c 1 /dev/hda1" is executed then
the /dev/hda1 would be checked every boot.
Am I right?

Yes, i think so.

---

