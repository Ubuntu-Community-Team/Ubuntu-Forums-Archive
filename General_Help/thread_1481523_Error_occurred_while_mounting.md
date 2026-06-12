---
title: "Error occurred while mounting /"
date: 2010-05-12
forum: General Help
---

### Post by sideaway on 2010-05-12
Hey there, whenever I try to start Ubuntu, I get the error "Error occurred while mounting /, Press s to skip or m to recover manually.

So I've thrown in the live CD to look at my fstab file, but everything appears normal? Can anyone help?

---

### Post by sideaway on 2010-05-12
Here is my fstab files...

```
proc                                       /proc             proc  nodev,noexec,nosuid               0  0  
UUID=59a10b95-b87e-4e09-a88a-0a3b478215eb  /                 ext4  errors=rw,user,noauto             0  1  
UUID=3bfc7fb3-cb68-40c1-b6d0-3c53dc7572c5  /home             ext3  defaults                          0  2  
UUID=93645ecc-7ce6-483e-9b4e-334c823a0c8d  none              swap  sw                                0  0  
/dev/fd0                                   /media/floppy0    auto  rw,user,noauto,exec,utf8          0  0  
/dev/sda1                                  /media/Games      ntfs  auto                              0  7  
/dev/sdb1                                  /media/TV         ntfs  auto				     0  3  
/dev/sdc1                                  /media/HDMovies2  ntfs  auto                              0  4  
/dev/sdd1                                  /media/Music      ntfs  auto                              0  5  
/dev/sde1                                  /media/HDMovies   ntfs  auto                              0  6
/dev/sdg1                                  /media/Gigabeat   msdos auto                              0  0
//192.168.1.6/torrents/                    /media/torrents   cifs  auto                              0  0  
```

And here is the output of blkid
```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="16B017E9B017CE5D" TYPE="ntfs" 
/dev/sdb1: LABEL="New tb" UUID="28BFFB126F16DD75" TYPE="ntfs" 
/dev/sdd1: UUID="518E81ED0DC23652" TYPE="ntfs" 
/dev/sdc1: LABEL="First tb" UUID="F2388FA0388F6309" TYPE="ntfs" 
/dev/sde1: UUID="705EB65471F84A8A" TYPE="ntfs" 
/dev/sdf1: UUID="59a10b95-b87e-4e09-a88a-0a3b478215eb" TYPE="ext4" 
/dev/sdf3: UUID="2CD0D4C9D0D49B02" TYPE="ntfs" 
/dev/sdf4: UUID="3bfc7fb3-cb68-40c1-b6d0-3c53dc7572c5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdf5: UUID="93645ecc-7ce6-483e-9b4e-334c823a0c8d" TYPE="swap" 

```

---

### Post by t0p on 2010-05-12
Possible stoopid question: have you tried hitting 'm' to recover manually?  It might sound intimidating, but Ubuntu is awfully good at helping users figure out how to fix problems like this.

---

### Post by sideaway on 2010-05-12
Hey thanks for the reply, I have, and it appears to mount / correctly! But it mounts it read only - so I cannot change anything. Which I thought's kinda pointless for a recovery console... :P

---

