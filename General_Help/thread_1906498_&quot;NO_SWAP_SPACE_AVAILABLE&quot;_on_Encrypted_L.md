---
title: "&quot;NO SWAP SPACE AVAILABLE&quot; on Encrypted LVM"
date: 2012-01-09
forum: General Help
---

### Post by Ignus Fatum on 2012-01-09
Hi there fellow (K)(X)(L) Ubuntees,

Today I manually installed Ubuntu 11.10 (32bit) on an encrypted LVM.
I have reserved 4096mb of SWAP, the same amount as my RAM.
But Ubuntu is unable to mount/detect/see/use the SWAP.:(

My setup is as follows:
80gb harddrive
1000gb hardrive

80gb harddrive is partitiond as follows:
unencrypted boot partition: 512mb ext2 mounted as /boot
Encrypted LVM (1) = Volume group 1 79gb is split in 3 logical partitions.
vg1-lvroot 25gb ext4  mounted as /
vg1-lvswap 4,1gb swap space
vg1-lvhome 51gb ext4 mounted as /home

Encrypyred LVM (1) = Volume group 2 1000gb is spilt in 2 logical partitions.
disk_c 500gb ext4 mounted as /backup_c
disk_d 500gb ext4 mounted as /backup_d

**BLKID **gives me the following output: 

ignus@ubuntu:~$ sudo blkid
[sudo] password for ignus: 
/dev/sda1: LABEL="boot" UUID="a03649d6-ec1f-46d3-a409-24de0fd310e5" TYPE="ext2" 
/dev/sda5: UUID="07413661-294e-4ff7-be07-7e6fdd93de0f" TYPE="crypto_LUKS" 
/dev/sdb5: UUID="c2122406-4603-4ec6-86f6-974baadfcb3f" TYPE="crypto_LUKS" 
/dev/sdc1: UUID="1FA4-AF02" TYPE="vfat" 
/dev/mapper/sda5_crypt: UUID="cJr7HH-rVwA-GpeG-UEBM-lnMY-UnCs-msFIq2" TYPE="LVM2_member" 
/dev/mapper/vg1-lvroot: LABEL="root" UUID="d36153e5-60fb-49e1-8a14-96f369c89d2f" TYPE="ext4" 
/dev/mapper/vg1-lvhome: LABEL="home" UUID="99d6f38c-0a84-44af-9d5d-5508b08a0216" TYPE="ext4" 
/dev/mapper/sdb5_crypt: UUID="7pxmTH-AwEX-Qe0O-6GdP-J5Ld-K126-UAPdsR" TYPE="LVM2_member" 
/dev/mapper/vg2-disk_c: LABEL="backup_c" UUID="ceaaf2d8-3e90-4b36-8234-5ed8c958dd7d" TYPE="ext4" 
/dev/mapper/vg2-disk_d: LABEL="backup_d" UUID="f4b5bc3c-291e-494c-8195-6bba3a98af4f" TYPE="ext4" 

and** /etc/fstab** holds the following static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/vg1-lvroot /               ext4    errors=remount-ro 0       1
/dev/mapper/vg2-disk_c /backup_c       ext4    defaults        0       2
/dev/mapper/vg2-disk_d /backup_d       ext4    defaults        0       2
# /boot was on /dev/sda1 during installation
UUID=a03649d6-ec1f-46d3-a409-24de0fd310e5 /boot           ext2    defaults        0       2
/dev/mapper/vg1-lvhome /home           ext4    defaults        0       2
/dev/mapper/vg1-lvswap none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

**SWAPON** doesn't work either:
ignus@ubuntu:~$ sudo swapon -a
swapon: /dev/mapper/vg1-lvswap: read swap header failed: Invalid argument
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory

Did I somewhere make a fatal error during the partioning setup and do I need to do it all over again or can this be resolved on the installed system? I have tried gparted but it doesn't see the logical volumes on the encrypted lvm so no luck there. I would like to thank you very much for your time and advice in advance.

Cheers,

Ignus

---

### Post by MadsRC on 2012-01-09
Could you use the "code" tag?
This way your terminal output is easily read like this:
```
random data from the awesome terminal
```

Then I'll see if I can figure it out.

What I normally do though, on encrypted systems, is not to create a SWAP partition, but a SWAP file on the encrypted volume.

I got a guide for it somewhere at home... I'll link it when I get home.

---

### Post by Ignus Fatum on 2012-01-09
> ```
random data from the awesome terminal
```:P

LOL. I might be a noob, but not such a noob.

> What I normally do though, on encrypted systems, is not to create a SWAP partition, but a SWAP file on the encrypted volume.
I got a guide for it somewhere at home... I'll link it when I get home.

If you would, that would be very nice, but is there anyway that I can ad 4 gb I used for the swap partion to the home partition before I make the swap file or is this 4gb gone untill the next install? Anyway thanks for your help,

---

### Post by MadsRC on 2012-01-09
Just tried googling my way to that link, but can't find it. Will post it when I get home later.

I haven't worked with LVM enough to be sure if it is possible to erase your current SWAP partition and add it to your home. But from what I gather from around the interwebz, it shouldn't be a problem as you can always resize LVM. So you should be able to erase SWAP and resize the home partition. Wouldn't try it though, before one of the Ubuntu experts have commented that.

Would try it myself when I get home, but my test PC is being used as a backup for someone who just broke their primary laptop.

---

### Post by MadsRC on 2012-01-09
I seem to have deleted my link... Shame, cause there wore a lot of nice stuff in it...

But from searching google I found this:
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

Seems to be roughly the same procedure as the link I wanted to find.

---

### Post by imachavel on 2012-01-09
where is your encryption key stored?

---

### Post by MadsRC on 2012-01-10
Hmm, I'm actually not 100% sure. Don't have an LVM/LUKS encrypted PC atm.

So, actually, I'm not sure if the key is stored in the RAM or somewhere else?

---

### Post by MadsRC on 2012-01-10
I got confused. Did you mean the actualy passphrase that you enter (ie. where it is stored once the system is decrypted (Like in the RAM, for extraction if the RAM is pulled out) OR the keyfile (if such is in use instead/ontop of the passphrase)?

---

