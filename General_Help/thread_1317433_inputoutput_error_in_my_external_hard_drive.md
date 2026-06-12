---
title: "input/output error in my external hard drive"
date: 2009-11-06
forum: General Help
---

### Post by Ftuuky on 2009-11-06
Hello people, I'm very new to Linux and to this forum but I have a serious problem: I'm using Ubuntu 9.04 without any problems and suddenly my external hard drive stops showing me its files: I see a blank window but it says it has files in there and when I try to do something it shows up an error 'input/output' and I have no idea what's going on, I haven't done anything. I tried several times to mount/unmount it and by rebooting the laptop but nothing happened.

I'm sorry if this is the wrong place or if it's a noob question but the truth is I'm not very bright when it comes to this stuff. 


Thanks in advance for your help.

---

### Post by Ftuuky on 2009-11-06
Please help me, I have really important documents in that hard drive...

---

### Post by Ftuuky on 2009-11-06
Please, someone?

---

### Post by Bucky Ball on 2009-11-06
Open a terminal (Applications->Accessories) and paste this in:

```
gksudo nautilus
```This open a file browser GUI with you as root. Can you now get to the files? If so, the permissions have somehow changed for that external hard drive. I am presuming you are using 9.10? 8.04 is a better place to start for beginners. Rock solid. 9.10 is wet behind the ears and problematic (check the posts in the forum). I would give it six months.

8.04 LTS (Long Term Support) is the current enterprise release and supported until 2013 (from memory), advisable if you are running server, production machine or any machine you need to be stable. If you really need those files and you get no resolution from this thread I suggest installing 8.04 and see if that gives you more luck.

Let us know how you go.

---

### Post by Ftuuky on 2009-11-06
> **Bucky Ball said:**
> Open a terminal (Applications->Accessories) and paste this in:

```
gksudo nautilus
```This open a file browser GUI with you as root. Can you now get to the files? If so, the permissions have somehow changed for that external hard drive. I am presuming you are using 9.10? 8.04 is a better place to start for beginners. Rock solid. 9.10 is wet behind the ears and problematic (check the posts in the forum). I would give it six months.

8.04 LTS (Long Term Support) is the current enterprise release and supported until 2013 (from memory), advisable if you are running server, production machine or any machine you need to be stable. If you really need those files and you get no resolution from this thread I suggest installing 8.04 and see if that gives you more luck.

Let us know how you go.

   I think I'm using the 9.04 version... I tried what you said but I still can't access the files.

---

### Post by Ftuuky on 2009-11-06
It didn't work...

---

### Post by fatdunky on 2009-11-06
What type of file system is it?, unfortunately i had this issue with a NTFS drive and the only way i could solve it was to format the drive as i think the files had become corrupt.

But if you have an NTFS drive i would first recommend booting up into windows install/recovery console and runinng chkdsk -f. 

If you have linix file system like ext2/3/4 or similar you could also try running the fsck command (you will need to unmount the drive first)

---

### Post by Ftuuky on 2009-11-06
> **fatdunky said:**
>  If you have linix file system like ext2/3/4 or similar you could also try running the fsck command (you will need to unmount the drive first)

  fsck.ext2: Permission denied while trying to open /dev/sdb1 You must have r/w access to the filesystem or be root

---

### Post by fatdunky on 2009-11-07
try sudo in front of it?.

For example if i wanted to run it onthe hdd i have mounted to /media/New_emule2

sudo umount /media/New_Emule2
<enter password>
sudo fsck /media/New_Emule2

---

### Post by Ftuuky on 2009-11-07
> **fatdunky said:**
> try sudo in front of it?.

For example if i wanted to run it onthe hdd i have mounted to /media/New_emule2

sudo umount /media/New_Emule2
<enter password>
sudo fsck /media/New_Emule2

   It gives me an error...

---

