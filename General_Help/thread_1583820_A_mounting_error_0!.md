---
title: "A mounting error 0?!"
date: 2010-09-28
forum: General Help
---

### Post by leo144 on 2010-09-28
hey guys, 
ive got a problem i have no idea how to solve:

each time i start my ubuntu 10.04 lucid it keeps saying: "an error occurred while mounting 0"
i dont really understand what that is... maybe one of you has already dealt with an error like that.

here is my sudo blkid output (this might help): 

/dev/sda6: UUID="cfd794ab-33df-4be4-ad74-68cc8d9e504b" TYPE="swap" 
/dev/sda7: UUID="d57fd9a6-6737-4aba-ae71-7f7a3744cf2e" TYPE="ext4" 
/dev/sda1: LABEL="WinRE" UUID="9C324DF6324DD644" TYPE="ntfs" 
/dev/sda2: UUID="D4547FCB547FAEBC" TYPE="ntfs" 
/dev/sda3: UUID="78A94E2829DC7EBB" TYPE="ntfs" 
/dev/sda5: UUID="0810afbc-42fe-482b-a9d8-deef056410cf" TYPE="ext3" 

thanks guys!!

---

### Post by bcraig24 on 2010-09-29
Bump

Ive got the same problem..

blkid output:

/dev/sda1: UUID="e1606c6e-e959-492d-824e-c0a8f0cd619b" TYPE="ext4"
/dev/sda5: UUID="d5492173-5794-46af-aa21-87abe18d571a" TYPE="swap"

Can someone please help me out this is really urgent =(

---

### Post by WorMzy on 2010-09-29
Could both of you post the contents of your /etc/fstab file please.

Put [CODE[COLOR="black"]][[/COLOR]/CODE] tags around it to help retain it's readability.

---

### Post by bcraig24 on 2010-09-29
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw                0         0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

//192.168.1.2/sharing /var/sharing cifs
credentials=/home/ben/.smbpasswd,uid=ben 0 0

---

### Post by WorMzy on 2010-09-29
I'm no expert on Samba, but I'm pretty sure that it's mount information should be on one line, just like any other mount.

Run
```
gksu gedit /etc/fstab
```

and delete the line break, so that it appears like this:

```
//192.168.1.2/sharing /var/sharing cifs credentials=/home/ben/.smbpasswd,uid=ben 0 0
```

I'm also doubtful that you can use your username as the uid argument. You may want to change it to "uid=1000", assuming that 1000 is your user ID (open a terminal and run "echo $UID" to check).

---

### Post by leo144 on 2010-09-29
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


#Entry for /dev/sda5 :
UUID=0810afbc-42fe-482b-a9d8-deef056410cf	/	ext3	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=9C324DF6324DD644	/media/WinRE	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda2 :
UUID=D4547FCB547FAEBC	/media/sda2	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda3 :
UUID=78A94E2829DC7EBB	/media/sda3	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=cfd794ab-33df-4be4-ad74-68cc8d9e504b	none	swap	sw	0	0

```

---

### Post by WorMzy on 2010-09-29
Leo, you have a similar problem, this line:

```
    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0

```

Shouldn't be there. Either delete it or comment it out (with a # at the start of the line)

---

### Post by leo144 on 2010-09-29
thanks man, now i dont have this annoying bug anymore
i really appreciate your help!!!

---

