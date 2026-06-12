---
title: "Encrypted ubuntu woes - var and tmp"
date: 2010-07-14
forum: General Help
---

### Post by Zorgoth on 2010-07-14
I need to run Linux at work with /var and /tmp encrypted.  Home and swap I've got fine.  I used to have /var and /tmp working fine when I was running 32-bit, but recently I had to upgrade to 64-bit and so I tried to set up encrpytion the same way as last time, using this thread: 

[https://fnmail.saic.com/exchweb/bin/redir.asp?URL=http://blog.larsstrand.org/article.php?story=EncryptedSwapAndHomeUbuntu](https://fnmail.saic.com/exchweb/bin/redir.asp?URL=http://blog.larsstrand.org/article.php?story=EncryptedSwapAndHomeUbuntu)

I treated /var essentially the way this thread treated /home, except that to preserve the data I first tarballed the contents and then set up the encrypted filesystem on a live CD before untarring them back in (also using the live CD).  During this stage I got no errors whatsoever.  It is exactly when I installed my 32-bit system except that then there was sensitive data on the partition so I first overwrote it with random data.

Before setting up encryption I installed all the packages that were on my 32-bit Ubuntu.

The only thing I changed in this run from last time is that I didn't overwrite them with random data because there was no sensitive data there anyway this time.  Then when I booted up, /dev/mapper/crpyptotmp didn't even exist and var loaded but for some reason (probably permissions) it didn't work right and messed up GNOME so badly I didn't have any graphical interface at all.  I am reinstalling the OS again now and hope someone can help me...

Here are the crypttab and fstab I am using; they are the same as my old setup and use the same partition table:

```

# <target name>	<source device>		<key file>	<options>
cryptoswap /dev/sda7 /dev/urandom cipher=aes-cbc-essiv:sha256,size=256,hash=sha256,swap
cryptotmp /dev/sda5 /dev/urandom cipher=aes-cbc-essiv:sha256,size=256,hash=sha256,tmp
cryptovar /dev/sda6 none luks

```
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/mapper/cryptotmp       /tmp            ext2    defaults        0       2
/dev/mapper/cryptovar       /var            ext4    defaults        0       2
# swap was on /dev/sda7 during installation
/dev/mapper/cryptoswap swap swap sw 0 0

```

I don't understand why overwriting the partitions with random data first would make a difference (maybe it prevents the system from writing to them early on), but I am going to try doing that as well this time on the theory that it worked last time.

---

### Post by Zorgoth on 2010-07-14
OOPS!  My link is bad; that was from my corporate email for some reason.

This is the real link:

[http://blog.larsstrand.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.larsstrand.org/article.php?story=EncryptedSwapAndHomeUbuntu)

---

### Post by Zorgoth on 2010-07-14
Solved, not quite sure how.

---

### Post by raphha on 2010-10-27
Hi everyone,
I ran into the same problem and finally managed to get encrypted /tmp working with the following settings

/etc/fstab
```

/dev/mapper/temp_crypt /tmp ext2 defaults 0 0

```

/etc/crypttab
```

temp_crypt /dev/sda6 /dev/urandom cipher=aes-cbc-essiv:sha256,tmp

```

The difference that made the difference was to omit the size=256 part... I didn't try to use the hash=sha256 at all.

Best regards and good luck,
Raph

---

