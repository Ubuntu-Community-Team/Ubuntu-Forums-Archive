---
title: "Advice on recovering encrypted data from corrupted partition"
date: 2011-07-20
forum: General Help
---

### Post by jackvaughn on 2011-07-20
Hi all,

I recently suffered a hard disk failure, meaning I had to replace the faulty device.

After attempting to mount the old faulty hard drive using and external caddy, I got the following message...

[I][B]Unable to mount 144 GB Filesystem
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B][/I]

I'd like to attempt to recover what I can from my /home directory but unfortunately I use encryption (although I do actually know my pass phrase).

What procedures and software can I use to try and recover data from this drive?

Any help would be much appreciated.

I am currently using Ubuntu 10.10 Maverick

Jack

---

### Post by smurphy_it on 2011-07-20
I believe you need to grab the software, and then "decrypt" the FS before you can use it.

```
sudo apt-get install lvm2 cryptsetup 
```
then you have to load the module for encryption:
```
sudo modprobe dm-crypt
```

After that you would have to open the Luks Encrypted volume.

```
cryptsetup luksOpen /dev/<drive> <hddname>
```
Followed by mounting it:
```
sudo mount /dev/mapper/<hddname> /mnt/<hddname>
```

---

### Post by jackvaughn on 2011-07-20
Thanks for the advice.
Unfortunately when I use

```
cryptsetup luksOpen /dev/sdb5 myolddrive
```

I get the error message:

*Device /dev/sdb5 is not a valid LUKS device.*

I am assuming this is because the partition cannot be read properly.

Any other suggestions please?

Jack

---

### Post by alphaamanitin on 2011-07-20
If you need the data you should stop using the device now and clone it to a new hard drive.  I use the dd command to clone drives.  This way you can work on the new HD without fear of increasing the damage done by working for recovery.  Warning though, cloning a drive with I/O errors can damage the drive even more.

AlphaA

---

### Post by smurphy_it on 2011-07-20
Hmm, try some of these commands.
```
sudo demsg | grep /dev
```

Most likely the device inserted will be a /dev/mapper/....

Other ones you can try, however I don't think they'll work until after the LVM volume has been decrypted.

```
sudo pvscan
```
```
sudo vgscan
```

---

### Post by smurphy_it on 2011-07-20
I forgot this one to try apparently.
```
sudo cryptsetup status /dev/sdb5
```

Will error out if you don't give it the right device name of course.

---

