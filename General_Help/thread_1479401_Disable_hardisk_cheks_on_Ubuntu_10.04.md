---
title: "Disable hardisk cheks on Ubuntu 10.04"
date: 2010-05-10
forum: General Help
---

### Post by Acheron3 on 2010-05-10
Hello, I've just upgraded to Ubuntu 9.10 and every several reboots my hardisk is checked for errors. It tooks about 1 hour or more. Is there a simple way to disable it and to perform these checks only when requested?
Thank you in advance.

---

### Post by CharlesA on 2010-05-10
By default, it will check after 20 mounts, or if the volume is marked dirty.

Have you run fsck from a livecd and made sure that the volume is clean?

---

### Post by Acheron3 on 2010-05-10
Yes, it seems to perform the checks about every 20 boots but it's still annoying for me because I need my pc in my work and I can be waiting a long time to boot it. I would prefer, if possible, to perform the checks only when I request it.

---

### Post by fillintheblanks on 2010-05-10
I'd also like to know how to disable this.

it always goes to 70% then you have to wait like 15 minutes before you can get to desktop, annoying :mad:

---

### Post by jerome1232 on 2010-05-10
It should only be checking every 32 mounts, at least that's the default.

At any rate I wouldn't completely disable checking but you can change it to be time based or increase the amount of mounts before it checks the system with tune2fs. I'm assuming of course that you are using ext2, ext3, or ext4.

When you see sdx# you need to replace x with the real drive letter and # with the real partition number. ie first disc second partition is /dev/sda2.

To check the current settings

```
sudo tune2fs -l /dev/sdx#
```

To change the number of mounts before a fsck is forced

```
sudo tune2fs -c # /dev/sdx#
``` you can replace # with any number, setting it to 0 or -1 will disable mount dependant checking entirely.

if you wanted to go a time based route (weekly, monthly etc...) then set the max mount count to 0 or -1 as describe above and do this. In this particular example I'm setting it to once a month, you would use 1w for once a week, maybe 12m for once a year or whatever you want.
```
sudo tune2fs -i 1m /dev/sdx#
```

---

### Post by Acheron3 on 2010-05-10
Thank you
It seems it has worked. There's what I've typed and what I've got on Terminal:
```

root@josep-laptop:~# sudo tune2fs /dev/sda2 -c -1
tune2fs 1.41.11 (14-Mar-2010)
Setting maximal mount count to -1

```

---

### Post by jerome1232 on 2010-05-10
Yup that means it worked, although I would recommend at least enabling the time based checking, I mean is once every 6 months going to kill ya?

```
sudo tune2fs -i 6m /dev/sda2
```

---

### Post by Acheron3 on 2010-05-10
> 
Yup that means it worked, although I would recommend at least enabling  the time based checking, I mean is once every 6 months going to kill ya?


Ok it's a good option but is there a way to perform disk checks on request?

---

### Post by jerome1232 on 2010-05-10
> **Acheron3 said:**
> Ok it's a good option but is there a way to perform disk checks on request?

Not that I know of, but I do remember there is a way to make the periodic checks happen at shutdown. Some app in the repo's...

 I have no idea off the top of my head what it was and I'm taking off atm so if that's something you want I'll have to get back to ya.

---

### Post by Acheron3 on 2010-05-10
Ok thank you anyway I have to go now but I will look for it and I'll post the way if I found it!

---

### Post by kolinab on 2010-05-10
I too remember that there was some utility that you could load . . . I used it for a while but have forgotten it. The nice thing was, it would tell you how many more mounts until your drive had to be checked again. That way you could defer the check as many times as you wanted. I uaually didn't let it go too long . . . it's just that I prefer to choose when it happens. Would be nice to find this program again and see if it still works with Lucid.

---

### Post by CharlesA on 2010-05-10
If you want to force a fsck use this command:

```
sudo touch /forcefsck
```

fsck will check the disk on next boot.

---

### Post by kolinab on 2010-05-11
> **CharlesA said:**
> If you want to force a fsck use this command:

```
sudo touch /forcefsck
```

fsck will check the disk on next boot.

Does that force it for all disks? The reason I ask is because somehow my root partition and my home partition are on different cycles. At least using this command I could get them in time with each other again.

I also found some information on autofsck at [https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

I installed the package showfsck, which tells you how many more mounts until the next check.

I haven't installed autofsck again to see how it works in Lucid.

K

---

### Post by bigsmitty64 on 2010-05-11
I had this last night and thought something was screwed on my drive!   :)
  I never saw it check in my Karmic install. Just did it last night in Lucid for the first time.

---

