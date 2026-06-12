---
title: "Error Installing grub"
date: 2010-04-28
forum: General Help
---

### Post by gunjannigam on 2010-04-28
I had Ubuntu 9.04 installed on my HDD. I recently installed Windows XP and my grub was gone so I tried to reinstall it two ways but none of them worked. I had  mounted my Ubuntu partition and have Grub Legacy  .
This is what I did
Firstly
```

sudo grub

```Followed by
```

find /boot/grub/stage1

```which resulted 
```

(hd0,5)

```then
```

root (hd0,5)

```then
```

setup (hd0)

```which resulted
```

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested


```Secondly I tried this 
```

mount | tail -1 

```which resulted
```

/dev/sda5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

```then 
```

sudo grub-install --root-directory=/media/disk /dev/sda5 --recheck

```which resulted
```

Probing devices to guess BIOS drives. This may take a long time.
The file /media/disk/boot/grub/stage1 not read correctly.

```Kindly help to solve out the problem

---

### Post by zvacet on 2010-04-28
See if [this]("http://members.iinet.net.au/~herman546/p15.html#12_") helps.

---

### Post by gunjannigam on 2010-04-28
> **zvacet said:**
> See if [this]("http://members.iinet.net.au/%7Eherman546/p15.html#12_") helps.

I tried using the AutoGrub Disk software listed on this page but that also didn't help. It stucked in the middle while installing grub for my Linux

---

