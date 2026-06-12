---
title: "fstab problem"
date: 2010-01-19
forum: General Help
---

### Post by gregkane on 2010-01-19
I'm very new to this and I've apparently changed my fstab file and now my boot drive fails to mount. The original file is still there "fstab.BAK". How do I rename the current fstab to another name and rename the fstab.BAK to fstab?

Since this is read only in the /etc directory I have not been able to make this happen from a command prompt.

Any help would be greatly appreciated!

---

### Post by Ahriman on 2010-01-19
To rename the current (faulty) fstab to fstab.BROKEN try:
```
sudo mv /etc/fstab /etc/fstab.BROKEN
```
(it will ask for your password)

To rename the original (fstab.BAK) to fstab, try:
```
sudo mv /etc/fstab.BAK /etc/fstab
```

---

### Post by gregkane on 2010-01-19
Ahriman

Thanks but I tried that and it tells me it is a read only file system. I tried to change the attributes (chmod ugo+rw /etc/fstab) but that doesn't seem to work

---

### Post by Ahriman on 2010-01-19
Are you booting via the LiveCD? If so, then you will have to mount the disk that has your /etc/fstab on it in order to do the file rename operations.

---

### Post by gregkane on 2010-01-19
When I let it boot it goes into a terminal mode. I have not tried to boot from the CD. The change in the fstab is calling for my secondary (non-bootable) drive to boot. I can't have that secondary drive made bootable.

I'd rather not have to reinstall the OS just to change one file. Is there some way to manually mount the drive (I know the correct uuid) and not have it try and read the fstab file?

thanks

---

### Post by shreepads on 2010-01-19
A silly question, are you logged in as an admin user?

If yes, try
sudo cp /etc/fstab /etc/fstab.broken
sudo mv /etc/fstab.bak /etc/fstab

---

### Post by gregkane on 2010-01-19
that is not a silly question to a newbie like me... but yes, I'm logged in and I get the error cp: cannot create regular file "/etc/fstab.broken" : Read only file system

and I tried changing the file to RW with sudo chmod 0777 /etc/fstab but no luck. Its like everything is locked into read only.

---

### Post by blackened on 2010-01-19
You should boot into the liveCD, from there you should issue the commands (make sure you replace *yourrootpartition* with the appropriate partition name/number)
```
mkdir rootmount

mount -t ext4 /dev/*yourrootpartition* ~/rootmount

sudo cp ~/rootmount/etc/fstab ~/rootmount/etc/fstab.broken

sudo cp ~/rootmount/etc/fstab.BAK ~/rootmount/etc/fstab

```

Reboot.

---

### Post by gregkane on 2010-01-19
Thank you! .... worked like a charm. I didn't understand I could boot from the cd without housing my disk - maybe I should learn to read better!

Thanks to all that took the time to help me out!

---

### Post by blackened on 2010-01-19
The flexibility in the Linux filesystem is just outstanding, but it's fairly unforgiving if you make a mistake in configuration.

Please mark this thread as solved.

---

