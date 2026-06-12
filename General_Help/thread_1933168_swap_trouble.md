---
title: "swap trouble"
date: 2012-02-28
forum: General Help
---

### Post by Allavona on 2012-02-28
Hey all! When booting after a fresh install I now seem to get this message at boot:

"The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present"

What is this exactly? Is my swap not being found? Any help would be greatly appreciated!

---

### Post by pedja_portugalac on 2012-02-28
Very strange. Why should swap be crypted? Did you coose to encrypt entire disk?

---

### Post by Allavona on 2012-02-28
No, not the entire disk. I chose to encrypt my /home during install and upon reboot this message appears.

I've tried sudo swapon /dev/mapper/cryptswap1 but it tells me the device is busy. Strange indeed.

I do get an option to try manual recovery at the prompt, I guess I'll try that! Thanks!

---

### Post by pedja_portugalac on 2012-02-28
You can try it, mount all devices and resume normal boot.

---

### Post by chipbuster on 2012-02-28
/dev/mapper/cryptswap1 is the encrypted swap space, I believe. Since it would be possible to recover files off of unencrypted swap, swap is encrypted when you choose to encrypt anything on your disk.

I don't think there's actually an issue as long as the computer boots normally. I got that all the time on my encrypted 11.10, just delays the boot by a few seconds, which is expected when stuff is encrypted

---

### Post by Allavona on 2012-02-28
Yes, its not an issue. I chose the manual option and booted that way, saw that all was as it should be, then rebooted normally and voila! no message. Maybe sudo swapon /dev/mapper/cryptswap1 did the trick. Thanks for all your help! Another positive learning experience.

---

### Post by Khayyam on 2012-02-28
> **pedja_portugalac said:**
> Very strange. Why should swap be crypted? Did you coose to encrypt entire disk?

For much the same reason you might encypt the HD, data written to swap can be read off it just the same way you might recover data from a failing HD. Encypting swap is actualy quite easy to do as there need be no pass and the whole thing can be scrubbed at boot.
 
> **Allavona said:**
> No, not the entire disk. I chose to encrypt my /home during install and upon reboot this message appears.

hhmmm ...  "cryptswap1" is what must have been passed as '--target', so, if this is not your username (unlikely) then the installer also attempted to setup swap as a dm-crypt device. This is either a feature, or something you selected to do (was there an option "encrypt swap"?)

> **Allavona said:**
> I've tried sudo swapon /dev/mapper/cryptswap1 but it tells me the device is busy. Strange indeed.

Its not really that strange, they are not really devices until they are 'un-mapped', that is dm-crypt has converted it from a 'locked' and un-readable section of your disk into a mountable 'partition' that you can write to (they are like 'loop' devices in that regard). You can't 'swapon' because essentially its not a swap until its been mapped to correspond to a device, and for this to happen dm-crypt needs to be provided with either the pass and/or information about device mappings. How Ubuntu does this I'm not sure, generally its something your prompted for early in the boot process (for user home directories, etc) or, if swap, the boot process uses a random pass and then runs cryptsetup, mkswap, and swapon.

Where things are going wrong I'm not sure, but hopefully the above gives you some idea of how encrytpted partitions work. For a "manual recover" I think it simply means mounting via 'crytpsetup luksOpen /path' but as this not a map you will have a passphrase for you probably won't have any luck with it.

One question though, if you selected to have your home encypted, is it? Does 'cryptsetup status <name>' (where I assume '<name>' would be your user name) show it as mapped? 

HTH in some way ... khay

---

