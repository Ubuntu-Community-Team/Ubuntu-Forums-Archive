---
title: "Problems mounting an encrypted external drive"
date: 2012-08-25
forum: General Help
---

### Post by Welly Wu on 2012-08-25
I have a System76 Lemur Ultra Thin (lemu4) with Ubuntu 12.04.1 64 bit Long Term Service installed as the primary and default operating system. I also have an older Seagate FreeAgent Desk 1.50 terabyte USB 2.0 external desktop hard disk drive. I launched the Disks utility and I formatted this hard disk drive using GPT. I created a partition using LUKS encryption version 1 and the /ext4 file system. I put in a unique randomly generated 40+ character password and I verified it is exactly the same at the time of creation. When I launch Nautilus, I see it and I try to mount it, but it keeps giving me an error after I put in the same exact password:

Unable to mount 1.5 TB Encrypted
One or more block devices are holding /dev/sdf1

I did a Google search for this specific error message and I did not find anything useful that solved my problem.

What is going on here?

How do I mount this encrypted hard disk drive properly?

What else do I need to know?

I am trying to replace TrueCrypt 7.1a with LUKS because it is built-in Ubuntu 12.04.1 64 bit LTS.

Please reply soon with answers and a solution. Thank you.

---

### Post by Welly Wu on 2012-08-26
I unplugged it. Then, I plugged it back in. I mounted it by typing in my password. It works.

---

### Post by bodhi.zazen on 2012-08-26
I do not think you can mount a LUKS partition with nautilus (not sure).

You first decrypt the LUKS partition with 

```
sudo cryptsetup luksOpen /dev/sdf1 crypt_name
```

Then mount it

```
sudo mount /dev/mapper/crypt_name /mount/point
```

See also [http://doboko.com/2012/02/how-i-encrypt-and-mount-drives-in-ubuntu-using-luks/](http://doboko.com/2012/02/how-i-encrypt-and-mount-drives-in-ubuntu-using-luks/)

---

### Post by Welly Wu on 2012-08-26
I successfully mounted three LUKS version 1 encrypted volumes in Nautilus and I am copying data from one portable hard disk drive to a desktop hard disk drive now. It works.

---

