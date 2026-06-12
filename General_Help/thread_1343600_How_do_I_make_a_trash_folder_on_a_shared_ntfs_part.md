---
title: "How do I make a trash folder on a shared ntfs partition?"
date: 2009-12-02
forum: General Help
---

### Post by jjjjeremy on 2009-12-02
Dual boot Windows7/9.10

Have an ntfs partition for the files that I edit/use in both.

Just got it to boot by adding this to /etc/fstab :
/dev/sda3 /media/share ntfs umask=000 0 0

and then making this startup command:
sudo mount /dev/sda3

everything is writing fine, but I also want to delete to a trash folder. I have tried, but it doesn't go.

Do I just make a .Trash-00000 folder (or something that looks like that) in that partition, or is there a different way to make a partition trash-able?

Even better, is there a way that I can get Ubuntu and Windows to recognize the same folder in that partition as the trash folder, and have the same trash files be in both the trash folder in Windows and the trash folder in Ubuntu?

---

### Post by jjjjeremy on 2009-12-02
bump

---

### Post by jjjjeremy on 2009-12-02
bump

---

### Post by jjjjeremy on 2009-12-04
bump, nothing yet, really?

---

### Post by cariboo on 2009-12-04
It seems to me that windows 7 and ubuntu automagically create trash folders on an ntfs formated drive.

---

### Post by jjjjeremy on 2009-12-05
That's the thing, it's just not working. I am wondering if it's somehow in the way that the drive is mounted, or something like that.

There is a $RECYCLE.BIN and a .Trash-1000 folder, but I can't send to trash, just auto delete.

---

### Post by jjjjeremy on 2009-12-05
It was just an ownership issue. I solved with

 sudo mount /dev/XXXX -t [partition type] [location] -o uid=XXXX

[http://ubuntuforums.org/showthread.php?t=1228323](http://ubuntuforums.org/showthread.php?t=1228323)

---

### Post by jjjjeremy on 2009-12-05
ok, that one didn't hold. It just changed the ownership for that specific mounting instance.

Turns out, ntfs-3g assigns ownership at mounting, so the above command only held for that specific time that the drive was mounted, and once I restarted, it changed to the ownership specified in /etc/fstab

so, I went back to /etc/fstab, and changed the last line to 
/dev/sda3 /media/share ntfs-3g users,owner,auto,rw,uid=1000 0  0

Just read this [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) (how to fstab)

---

### Post by jjjjeremy on 2013-03-28
I love myself!

Since I wrote this I've re-installed ubuntu quite a few times, and I love just being able to go back to my old posts for the answers to my recurring problems!

---

### Post by wildmanne39 on 2013-03-28
Thread closed. Please do not post in old threads.

---

