---
title: "Resized swap partition does not register"
date: 2009-08-29
forum: General Help
---

### Post by Salamancero on 2009-08-29
I resized my swap partition recently so I could make use of the hibernate function on Ubuntu.  Since then, I noticed that my swap partition does not register on Ubuntu.  Is there something that I can do to correct this?  

Any help is appreciated.  Thanks! :)

---

### Post by Elfy on 2009-08-29
Run this to check the UUID of the swap partition 

```
sudo blkid
```

One line will be for the swap - make note of the number.

Now check the swap line in fstab and the resume file

```
cat /etc/fstab |grep swap
cat /etc/initramfs-tools/conf.d/resume
```

The UUID's should match - if you find they are different the files need to be edited with the correct number

```
gksudo gedit /etc/fstab
gksudo gedit /etc/initramfs-tools/conf.d/resume
```

Save the files.

If you have had to change the UUID in the /etc/initramfs-tools/conf.d/resume file after you saved you will need to run

```
sudo update-initramfs -u
```

[https://help.ubuntu.com/community/UsingUUID#Resuming%20from%20Hibernation](https://help.ubuntu.com/community/UsingUUID#Resuming%20from%20Hibernation)

---

### Post by Salamancero on 2009-08-30
thanks!

The instructions worked.  That and I noticed there was an option in gparted saying swapon. :)

---

### Post by Elfy on 2009-08-30
> **Salamancero said:**
> thanks!

The instructions worked.  That and I noticed there was an option in gparted saying swapon. :)

Welcome :)

You can also turn swap on and off with the swapoff and swapon commands.

---

