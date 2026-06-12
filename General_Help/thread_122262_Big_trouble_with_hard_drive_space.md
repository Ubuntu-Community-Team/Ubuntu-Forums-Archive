---
title: "Big trouble with hard drive space"
date: 2006-01-27
forum: General Help
---

### Post by Wolfbite on 2006-01-27
The partition Linux is on is approx. 85gb. However, after having copied 25gigs of files from the windows partition, I now only have 700mb free! I know Ubuntu can't be that big. What I suspect is that I somehow have both the 64-bit install and the normal install on the harddrive. I decided to forget about the 64-bit version since it messed completely up, and installed the normal Ubuntu instead. But how can I read the harddrive to see if the 64-bit is still there? When I think about it, I might have the same 25 gigs of windows files in two places on the harddrive, since I also copied them over when I used the 64-bit version. That would be 50g, and make 700mb free a little more believable.

PS: Also, it is normal for amaroK to use 75-95% of the cpu resources? I got an AMD64 3000+.

---

### Post by Wolfbite on 2006-01-27
The amarok problem disappeared. Heh. But the hard drive thing is driving me nuts, I don't have room for anything!

---

### Post by lha on 2006-01-27
Ubuntu install takes usually ~2GB, so to get that 85GB's used, you would need to copy your files _three_ times and have _four_ instances of Ubuntu... AFAIK, Ubuntu doesn't allow you to install it on a partition which already contains a system. (If that partition isn't formatted before installation or during installation.)

If you want to try to find where all your space has gone, try following commands:

```
du -sh *
```
This shows you the size of all files in your current directory. It also scans trough directories and calculates how much space is used by files in them. If you do this at /, you'll need sudo to be able to read all directories. (It will take a long time to read the whole filesystem.)

```
df -h
``` Shows you info on how much space is used on each partition.

```
sudo fdisk -l
``` This shows your partitions, so it doesn't tell much of hd usage. It may still provide useful information, eg if you have a partition which isn't mounted, it will show up here.

```
locate my_file
``` will search for file that have 'my_file' in their filename. Useful for searching duplicates if you know all duplicates of a file have the same name.

---

### Post by Wolfbite on 2006-01-27
Thanks a lot, Iha, the first command helped me find out where those gigs were being abused! I had 50g in the trash, but it only showed when in root. Haha, naughty Ubuntu. I love you, Iha! ^^

---

