---
title: "mount hard drive from live cd"
date: 2010-09-15
forum: General Help
---

### Post by spiky001 on 2010-09-15
Hi I need to mount the hard drive while running live cd
```
mount /dev/hda /mount/media
```
I have made a mount point media, I get a return of 

"mount point /mount/media/ does not exist"

fdisk -l shows hda through to hda7

---

### Post by 3Miro on 2010-09-15
Type:
```
 sudo fdisk -l 
```
to find out what Ubuntu sees and what not. /dev/hda is the hard drive however, you probably want one of the partitions on it. So you want

```
 sudo mount /dev/hda1 /media/myhdd 
```
(1 is for the first partition, 2 is for the seconds and so on. Also extended partitions don't count)

You should first create the folder /media/myhdd

```
 cd /media/
mkdir myhdd 
```

---

### Post by coffeecat on 2010-09-15
> **3Miro said:**
> /dev/hda is the hard drive however, you probably want one of the partitions on it.

Agreed. Definitely.

@spiky001, you can't mount a whole hard drive. You have to mount a partition. Also - are you sure about it being hda? IDE PATA drives have been designated sda (b, etc) by the kernel drivers for some years now, the same as SATA drives. Whatever - your fdisk output should tell us.

---

### Post by spiky001 on 2010-09-15
ok followed instructionsresult is      ```
 # mount /dev/hda2 /media/myhdd mount: mount point /media/myhdd does not exist
```    fdisk -l     Device Boot      Start         End      Blocks   Id  System /dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS /dev/hda2            1913        9729    62790052+   5  Extended /dev/hda5            1913        3736    14651248+  83  Linux /dev/hda6            3737        3918     1461883+  82  Linux swap / Solaris /dev/hda7            3919        9729    46676826   83  Linux      I am only using live cd will it still mount it? sorry I have never had to use live cd before

---

### Post by coffeecat on 2010-09-15
You have to make the mountpoint /media/myhdd the way 3Miro said.

Yes, you can do all that with a live CD, but which live CD is that? With a # root prompt and your hard drive designated hda, is that an ancient Knoppix disc? If so, you'd be better off with an Ubuntu disc.

Also, when you post terminal output, please enclose it in code tags otherwise it's unreadable. You can do this by highlighting the output in the message field and clicking the # icon just above the message field. Thanks.

---

### Post by spiky001 on 2010-09-15
ok solved problem  ```
mount -t ntfs /dev/hda1 ./media/myhdd
```  it was the . that was 1 problem plus file system  thks for help though  sorry for tags on last post they didn,t seem to work

---

