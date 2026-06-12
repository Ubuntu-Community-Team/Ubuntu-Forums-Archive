---
title: "Accessing encrypted drive fro livecd"
date: 2009-08-24
forum: General Help
---

### Post by schwartz on 2009-08-24
my system crashed today ([http://ubuntuforums.org/showthread.php?t=1248641](http://ubuntuforums.org/showthread.php?t=1248641)) and I don't know how to fix it (if you can help with that other thread I'd really appreciate it).

When it boots it does get past the full drive encryption that I setup using the alternate cd install method so I figure worst case I can boot off the live cd and grab the few files that are important that are more recent than my last backup.

I tried following this set of notes on accessing the encrypted drive from the live cd but it's not working.

"The live cd is missing some software required to read the encrypted 
volume.  You can install the software and read the volume with the 
following steps.

sudo apt-get install cryptsetup lvm2
sudo modprobe dm_crypt
sudo modprobe sha256_generic
sudo modprobe aes_generic
sudo crypsetup luksOpen /dev/sdXY cryptoroot

The drive will then probably mount itself.  If it doesn't, the device 
will show under /dev/mapper, so you can mount it manually.
"

I get the error "Command failed:  No key available with this passphrase."

Can anyone help me access this drive?

thanks,
Bill

---

