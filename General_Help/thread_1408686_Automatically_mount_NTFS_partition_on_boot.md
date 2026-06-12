---
title: "Automatically mount NTFS partition on boot"
date: 2010-02-16
forum: General Help
---

### Post by efAston on 2010-02-16
Hi,

I'm running kubuntu 9.10 and it's going like a dream at the moment. I was just wondering if there's a way to get my NTFS partition to mount automatically when I boot up. 

Sometimes I'll go to open amarok and it'll skip through all the files as if they're not there or it can't access the audio device. If I forget to open Dolphin and click on my NTFS drive to mount it, it's a pretty unintuitive problem.

Thanks for everything,
Aston

---

### Post by akakingess on 2010-02-16
Hopefully this will help you, this is the info on fstab which is used to automount partitions [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)  let me know if this works for you or not, I will be out for a couple of hours but will check in when I get back. Good luck.

---

### Post by TapamN on 2010-02-17
I'm having the same problem. Adding a line to fstab doesn't work. I've added the following line... 

/dev/sda2 /media/windows ntfs-3g user,auto 0 0

to fstab and I get the following message when trying to mount via "mount /media/windows":

Mount is denied because setuid and setgid root ntfs-3g is insecure with the
external FUSE library. Either remove the setuid/setgid bit from the binary
or rebuild NTFS-3G with integrated FUSE support and make it setuid root.
Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

Following the instructions on that page does not help.

I've also trying using the NTFS Conifguration Tool. This will cause the partition to be mounted automatically at startup, but as root, so only root will have write access... I spend most of my time working from a user account, so it's not all that useful.

The only way I've found to get my Windows partition to mount with user read/write permissions is with

sudo mount /dev/sda2 /media/windows -t ntfs-3g -o uid=1000

...but that's not automatic.

Automatic user r/w mounting of NTFS partitions used to work for me on 8.04, so downgrading to it might get the desired result...

---

### Post by Morbius1 on 2010-02-17
TapamN,

Change this:
>  /dev/sda2 /media/windows ntfs-3g user,auto 0 0To this:
```
 /dev/sda2 /media/windows ntfs defaults,nls=utf8,umask=007,gid=46 0 0
```What this will do is mount the partition with owner = root but with read / write permissions ( umask=007 ) granted to all local login users ( gid=46 ).

EDIT: If you prefer to be the owner then you can also go with this:
```
 /dev/sda2 /media/windows ntfs defaults,nls=utf8,umask=007,uid=1000 0 0
```

---

### Post by TapamN on 2010-02-17
That worked! Thanks.

---

### Post by efAston on 2010-02-18
Hi,

I tried the same, but got
bash: /dev/sda2: Permission denied

Is there anything I'm missing?

Cheers,
Aston

---

### Post by ironclaw on 2010-02-18
> **efAston said:**
> Hi,

I tried the same, but got
bash: /dev/sda2: Permission denied

Is there anything I'm missing?

Cheers,
Aston

Don't run the code on the command line; change the corresponding line in /etc/fstab to automount NTFS partitions.

---

### Post by akakingess on 2010-02-19
yes, from the terminal run something like
```
sudo gedit /etc/fstab
```then it will ask for your password and open the fstab file into which you enter the drive info that you want to automount, any other questions, let us know.

sorry, I use gedit out of habit, but you can use nano or vi or whatever straight editor you choose/have.

---

### Post by Zorael on 2010-02-19
One thing to keep in mind when wanting to make mounts permanent in fstab, is that all **current** mounts are listed in mtab (**/etc/mtab**).

So if GNOME or the KDE Plasma device notifier or whatnot automounted your device, and you're happy with the settings and options it automatically used (UTF-8, owner user/group, file/directory masks, et al), you can basically just copy the relevant line from mtab into fstab.

---

