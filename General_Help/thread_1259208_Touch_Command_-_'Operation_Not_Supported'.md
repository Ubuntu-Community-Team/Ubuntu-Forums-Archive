---
title: "Touch Command - 'Operation Not Supported'"
date: 2009-09-06
forum: General Help
---

### Post by Spike-X on 2009-09-06
I'm trying to use the touch command to alter the timestamp of a file on a Samsung YP-Z5 MP3 player (because for some reason, any new file I add gets stamped with a Date Modified of Mon 31 Jul 1972. Why that's even happening is a whole other issued I'd like to resolve).

When I execute the command

```
touch -m filename.mp3
```

after a few seconds I get

```
touch: setting times of `filename.mp3': Operation not supported
```

What am I doing wrong?

---

### Post by lisati on 2009-09-06
My first thought is that perhaps the file is read-only or write protected in some way.

---

### Post by Spike-X on 2009-09-06
```
The permissions of "filename.mp3" could not be determined.
```

Doesn't really help, does it?

---

### Post by hal10000 on 2009-09-06
Please post the output of [COLOR="Red"]ls -l filename.mp3[/COLOR]

---

### Post by Spike-X on 2009-09-06
```
-rw------- 1 spike-x spike-x 8269828 1972-07-31 00:45 filename.mp3
```

---

### Post by Spike-X on 2009-09-06
I also tried it with a couple of other files in the same directory, with the same result.

---

### Post by hal10000 on 2009-09-06
> I also tried it with a couple of other files in the same directory, with the same result.
Then look if you have write permission on the dirctory where these files are located:
[COLOR="Red"]ls -ld your_directory[/COLOR]
You may also post the output of [COLOR="Red"]lsattr filename.mp3[/COLOR] and [COLOR="Red"]lsattr your_directory[/COLOR] to see if there are set any extended attributes.

---

### Post by lswb on 2009-09-06
Is it possible that the filesystem used on the player does not support separate modification and access times? Have you tried just using "touch filename.mp3" without the -m option?

---

### Post by hal10000 on 2009-09-06
And maybe it's also possible that the player is write protected? I know this is on some usb sticks, which you can write-protect with a small switch.
Also there may be a fat filesystem on the player, if so, then the touch command would make no sense.

---

### Post by Spike-X on 2009-09-06
> **hal10000 said:**
> Then look if you have write permission on the dirctory where these files are located:
[COLOR="Red"]ls -ld your_directory[/COLOR]

```
drwx------ 1 spike-x spike-x 0 1970-01-01 10:00 Music
```

> **hal10000 said:**
> You may also post the output of [COLOR="Red"]lsattr filename.mp3[/COLOR] 

```
lsattr: Inappropriate ioctl for device While reading flags on filename.mp3
```

> **hal10000 said:**
> and [COLOR="Red"]lsattr your_directory[/COLOR] to see if there are set any extended attributes.

```
lsattr: Inappropriate ioctl for device While reading flags on Music/(every file in the directory)
```

---

### Post by Spike-X on 2009-09-06
> **hal10000 said:**
> And maybe it's also possible that the player is write protected? I know this is on some usb sticks, which you can write-protect with a small switch.

I've not seen any such switch, nor seen any mention of one in the player manual.

Also there may be a fat filesystem on the player, if so, then the touch command would make no sense.

This would seem the most likely explanation at this point.

I also noticed that, after renaming a couple of random files, their modification dates were also changed to 31 Jul 1972. So there's obviously a problem with the player's internal date having been reset (which I've tried numerous times to fix). I guess I'll have to try and find a solution for the core problem there.

Thanks for your help, Hal.

---

### Post by Spike-X on 2009-09-06
> **lswb said:**
> Is it possible that the filesystem used on the player does not support separate modification and access times? Have you tried just using "touch filename.mp3" without the -m option?

I tried doing this just now, with the same outcome.

---

### Post by hal10000 on 2009-09-07
> Is it possible that the filesystem used on the player does not support separate modification
Type [COLOR="Red"]mount[/COLOR] and look in the line for your players mount point to see the filr system and wether it is mounted rw

---

### Post by Spike-X on 2009-09-08
> **hal10000 said:**
> Type [COLOR="Red"]mount[/COLOR] and look in the line for your players mount point to see the filr system and wether it is mounted rw

This seems to be the relevant line:

```
gvfs-fuse-daemon on /home/spike-x/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=spike-x)
```

---

### Post by hal10000 on 2009-09-08
Please post the output of [COLOR="Red"]sudo fdisk -l[/COLOR] while your player is plugged in.

---

