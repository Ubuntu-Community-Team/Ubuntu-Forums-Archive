---
title: "Stop bootup password for encrypted swap?"
date: 2010-05-08
forum: General Help
---

### Post by cbraxton on 2010-05-08
I've set up a Lucid system with software RAID and encryption, with three encrypted partions - swap (/dev/md1), the root filesystem (/dev/md2), and /home (/dev/md3). The unencrypted /boot partition is /dev/md0.

This works well but the passphrase had to be entered three times at bootup. Obviously it would be preferable to enter the passphrase once to unlock the root partition, then have the others unlocked via key files. So I added key files to the swap and home partitions and modified /etc/crypttab to use them:

```

md1_crypt UUID=8066adbc-584c-4766-b188-bc2a7b61a2f0 /root/keys/swap-key luks,swap
md2_crypt UUID=bac82294-f3b9-45e4-89ad-407cf8b19b7b none luks
md3_crypt UUID=7d82a0b7-c811-4cc3-9fe7-1961c74b5ff2 /root/keys/home-key luks

```

The key files are owned by root and have 0400 protection. (The /root/keys directory is 0500.)

This worked fine for the /home partition, but I am still getting a second password prompt to unlock swap. I know the key file is OK since the swap partition can be unlocked with it from the command line.

I further attempted to "fix" this by removing the swap partition from /etc/fstab and /etc/crypttab entirely and setting up swap in /etc/rc.local instead:

```

# Set up our encrypted swap partition
/sbin/cryptsetup luksOpen /dev/md1 md1_crypt --key-file=/root/keys/swap-key
/sbin/swapon /dev/mapper/md1_crypt

```

Once again, this works if executed from the command line, but when booting up I still get the password prompt to unlock the swap partition.

Since the swap partition is no longer referenced in fstab or crypttab, why is there still a bootup password prompt for it? What else needs to be done to stop it? Is there a better way to fix this?

---

### Post by Wicked-Cricket on 2010-06-20
Was this ever figured out? I've got the same issue although mine is two passphrases - only my swap and home partitions are encrypted. Any way to "chain" these (one unlocks both)?

---

### Post by tkibugu on 2011-12-15
_[i have deleted post contents]_[]("http://agnulinuxuser.blogspot.com/2011/12/encrypting-swap-partition.html")

---

