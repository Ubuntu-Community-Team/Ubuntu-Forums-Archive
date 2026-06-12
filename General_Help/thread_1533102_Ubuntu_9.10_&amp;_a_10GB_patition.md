---
title: "Ubuntu 9.10 &amp; a 10GB patition"
date: 2010-07-17
forum: General Help
---

### Post by jokes_finder on 2010-07-17
hello, guys!

well, I've the same problem here as davoudi
-I'm new to Ubuntu -
I've installed ubuntu 9.10 on a 10GB partition
Ubuntu doesn't read except 3GB
when I tried "df -h"
here's the output:
"Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            2.7G  2.2G  350M  87% /
udev                  1.3G  288K  1.3G   1% /dev
none                  1.3G  936K  1.3G   1% /dev/shm
none                  1.3G   96K  1.3G   1% /var/run
none                  1.3G     0  1.3G   0% /var/lock
none                  1.3G     0  1.3G   0% /lib/init/rw
"

when I was upgrading to the newer version of ubuntu, it screamed for more space claiming that I only have about 300 or 500 MB free space - don't remember -:shock:

I found the file .xsession-errors - there's another one called .xsession-errors.old - but don't know what to do with it..:confused:

need help guys
thanks in advance

---

### Post by linuxman94 on 2010-07-17
It looks like this is a wubi install. Is it?

---

### Post by amsterdamharu on 2010-07-17
If you installed ubuntu on a 10G disk then you should have enough space unless your home folder holds many big files. Are you sure you installed it and are not running ubuntu off a live cd/squashfs loop device&#65311;

What is in your /etc/fstab? (you can open this file with gedit or any text editor)

---

### Post by jokes_finder on 2010-07-17
@linuxman94: yes it is

@amsterdamharu: for the home folder, i don't think so; i opened it and found " totalling 13.4 MB". I'm not running ubuntu from a cd, it's just from the HDD.

there's smth i wanna say.. i logged on the windows - since i installed ubuntu beside the windows version - and check the partition and found the there r more than 6 GB free space

---

### Post by jokes_finder on 2010-07-17
Any help, guys??

---

### Post by oldfred on 2010-07-17
I do not remember now but the older installer defaulted to about 2GB and you had to manually expand it to get more space even if it was available. It allowed a minimal install but then did not have enough room for all the updates. It assumed you knew to expand it and only you knew how much space you could use.

If you had 10GB, can you go into gparted from the liveCD and expand the root partition to use the full 10GB?

---

### Post by bcbc on 2010-07-17
with wubi you tell it how big to make the install. e.g. 3, 4, 10, 15 GB. Then it creates a virtual disk that is that size. That's the maximum size your wubi install can be.

the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?") mentions some options for increasing it. I don't know if LVPM still works on newer versions of Ubuntu (some parts definitely don't work, but maybe the resize does).
But you could use the other option to create a separate virtual disk for /home and use up the remaining space from the 10gb for this. However, I'm not sure if this would leave enough for you to upgrade though.

But this seems like a lot of work for a small install. Unless there's a good reason, I'd just backup important data from the current wubi and then install a fresh 10.04. Or better still, do a direct install to partition. 10GB should be fine for a direct install, as long as you don't plan on installing tons of stuff.

---

### Post by jokes_finder on 2010-07-19
Thanks for u guys
& special thanks for bcbc
as u, bcbc, said, i did. everything is going great now.

---

### Post by bcbc on 2010-07-19
> **jokes_finder said:**
> Thanks for u guys
& special thanks for bcbc
as u, bcbc, said, i did. everything is going great now.

Great, enjoy :)

---

