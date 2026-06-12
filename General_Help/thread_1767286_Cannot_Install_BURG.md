---
title: "Cannot Install BURG"
date: 2011-05-25
forum: General Help
---

### Post by fleamour on 2011-05-25
blkid:

```
/dev/sda1: LABEL="System Reserve" UUID="01CBED418332E900" TYPE="ntfs" 
/dev/sda3: LABEL="Ubuntu Store" UUID="F8C033E4C033A7B0" TYPE="ntfs" 
/dev/sdb3: LABEL="Restore" UUID="DC2CB62F2CB60514" TYPE="ntfs" 
/dev/sdb5: UUID="f4c5bfdc-cf61-46d5-bd07-2c1ac32f49db" TYPE="swap" 
/dev/sdb1: UUID="7c6f7176-45f9-4df0-897b-00f4075661b4" TYPE="ext4" 
/dev/sdb4: UUID="9e598d1e-ce06-4c5a-b634-9814f7a01a18" TYPE="ext4" 
/dev/sdc1: LABEL="TDK" UUID="9975-B739" TYPE="vfat"
``` 

Following this guide:

[http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/](http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/)

I think I wanna install to secondary HDD, so:

```
sudo burg-install “(hd1)”
```

I get error: 

```
bash: syntax error near unexpected token `('
```

Any ideas?

---

### Post by cecilpierce on 2011-05-25
> **fleamour said:**
> blkid:

```
/dev/sda1: LABEL="System Reserve" UUID="01CBED418332E900" TYPE="ntfs" 
/dev/sda3: LABEL="Ubuntu Store" UUID="F8C033E4C033A7B0" TYPE="ntfs" 
/dev/sdb3: LABEL="Restore" UUID="DC2CB62F2CB60514" TYPE="ntfs" 
/dev/sdb5: UUID="f4c5bfdc-cf61-46d5-bd07-2c1ac32f49db" TYPE="swap" 
/dev/sdb1: UUID="7c6f7176-45f9-4df0-897b-00f4075661b4" TYPE="ext4" 
/dev/sdb4: UUID="9e598d1e-ce06-4c5a-b634-9814f7a01a18" TYPE="ext4" 
/dev/sdc1: LABEL="TDK" UUID="9975-B739" TYPE="vfat"
``` 

Following this guide:

[http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/](http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/)

I think I wanna install to secondary HDD, so:

```
sudo burg-install “(hd1)”
```

I get error: 

```
bash: syntax error near unexpected token `('
```

Any ideas?

Try sudo burg-install /dev/sdb for second drive or sda for the first.

---

### Post by fleamour on 2011-05-25
That worked, but still boots standard vanilla GRUB2 without BURG eye candy.

I also used this tool to install, no joy:

[http://bit.ly/iHO2mn](http://bit.ly/iHO2mn)

---

