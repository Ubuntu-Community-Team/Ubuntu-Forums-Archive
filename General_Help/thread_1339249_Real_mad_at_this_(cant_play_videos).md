---
title: "Real mad at this (cant play videos)"
date: 2009-11-27
forum: General Help
---

### Post by bryan4 on 2009-11-27
i am really upset.. this has been going for a while.. whenever i try to play a youtube video it only plays for like a min then stops. when i try to watch a movie or any other video other youtube it doesnt even play.. i  think i have 526 mb of memory or something. i am really mad and frustrated. im about to throw this computer out the window. i cant get into to windows xp because its messed up due to a virus or something (by the way i partition ubuntu) oh and im using ubuntu 9.04 and i wanna upgrade but i guess i have to make the partition bigger but i cant get into windows xp cause it messed up and i dont think i have any blank disks. what do i do?

---

### Post by SlugSlug on 2009-11-27
you want to upgrade but you cant - due to space??  
whats the output of 
```
df -h
```

---

### Post by bryan4 on 2009-11-27
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   20M 100% /
tmpfs                 122M     0  122M   0% /lib/init/rw
varrun                122M  120K  122M   1% /var/run
varlock               122M     0  122M   0% /var/lock
udev                  122M  148K  122M   1% /dev
tmpfs                 122M   76K  122M   1% /dev/shm
lrm                   122M  2.4M  120M   2% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   12K 1012K   2% /tmp

---

### Post by bryan4 on 2009-11-27
> **SlugSlug said:**
> you want to upgrade but you cant - due to space??  
whats the output of 
```
df -h
```

well i really dont wanna upgrade.. i just usually use my computer to work on my website and listen to music and watch videos.

---

### Post by SlugSlug on 2009-11-27
well your problem is your root drive is full !!

/dev/sda5             2.3G  2.2G   20M 100% /

you need to try boot a live disk and setup your partitions,

---

### Post by audiomick on 2009-11-27
> **SlugSlug said:**
> well your problem is your root drive is full !!

/dev/sda5             2.3G  2.2G   20M 100% /

you need to try boot a live disk and setup your partitions,

Be careful fixing this. I tried to fix exactly this ( / 100% full ) for a friend of mine recently. I did everything by the book: backup, re-size partition, reboot, all seems to work. I don't know if this was really true, though.
The computer, a laptop, had been running 8.04 and the owner wanted to upgrade, so I did a fresh install of 9.10 using the existing, re-sized home partition. Now Nautilis does really weird stuff. If I try to open things in places, some links don't react, others try and open a music player instead of the directory they point to.

The lesson is, do your backups properly...

---

### Post by bryan4 on 2009-11-27
> **SlugSlug said:**
> well your problem is your root drive is full !!

/dev/sda5             2.3G  2.2G   20M 100% /

you need to try boot a live disk and setup your partitions,

how do i do that?
what materials do i need?
is there an easier way?

---

### Post by coffeecat on 2009-11-27
Since Windows is messed up because of a virus, do you want to abandon Windows and just run Ubuntu? If so, your best option would be to copy any personal data off that machine onto an external drive and do a fresh install to the whole disc. Much better than trying to move partitions around and make what sounds like a bad situation worse.

If you want to upgrade to 9.10, then the choice is easy. Download the 9.10 desktop CD and do a fresh install from that.

But if you want to keep Windows for a possible later rescue, then boot up into Ubuntu (if you can) and post the output of:

```
sudo fdisk -l
```That way we can see your partition layout and advise what is best.

---

### Post by bryan4 on 2009-11-27
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        2108    16900380    7  HPFS/NTFS
/dev/sda3            2109        2434     2618595    5  Extended
/dev/sda5            2109        2412     2441848+  83  Linux
/dev/sda6            2413        2434      176683+  82  Linux swap / Solaris

---

### Post by coffeecat on 2009-11-27
OK. **BIG** decision time. :wink:

Your partition sizes are (approximately):

sda1 (Dell Utility) - 23MB
sda2 (Windows C: ) - 16GB
sda5 (Ubuntu root) - 2.3GB
sda6 (swap) - 172MB

To do anything remotely useful in Ubuntu, you need a root partition of at least 4GB, but this will still give you insufficient room to store videos - which was the problem you started off with. I would want at least 10GB if I was going to store just a few videos as well as run Ubuntu, which means that you would have to shrink the Windows partition by about 8GB to get enough space on the HD. Which would leave about 8GB for Windows. Windows in 8GB? I doubt it.

So - do you want to sacrifice Windows so that you can install Ubuntu to the whole 20GB? And if you store the sort of video files I've got in my collection, 20GB isn't going to last long. Sorry.

Or - do you want to keep Windows and try to shrink its partition just a little iddy-bit so that you've got an Ubuntu partition that will at least work?

Over to you.

---

### Post by bryan4 on 2009-12-13
i want to keep windows but i wanna keep ubuntu also..

---

### Post by Uachtarain on 2009-12-13
Install Google Chrome ASAP.... Remove other browsers or leave them??. This problem has been with Firefox and has been for a couple of years now. Not worth the time to fix. Sit back and watch your blood pressure go way down....!!

Fergal

---

### Post by coffeecat on 2009-12-13
> **bryan4 said:**
> i want to keep windows but i wanna keep ubuntu also..

There's not really much more that I can say. You have a 20GB hard disc. You are going to have a hard time squeezing Windows, Ubuntu and stored video files all in 20GB. All I can suggest, then, is to see if the Windows partition can shrink down a bit more but still work, so that you can have an Ubuntu root partition of at least 5GB.

---

### Post by coffeecat on 2009-12-13
> **Uachtarain said:**
> Install Google Chrome ASAP.... Remove other browsers or leave them??. This problem has been with Firefox and has been for a couple of years now. Not worth the time to fix. Sit back and watch your blood pressure go way down....!!

Fergal

I suggest you read the thread again. The OP's problem is a completely full Ubuntu root partition. That is why they cannot play flash videos. There's no room to stream them to.

Oh, and flash works just fine in Firefox for me. Has done for much more than two years.

---

