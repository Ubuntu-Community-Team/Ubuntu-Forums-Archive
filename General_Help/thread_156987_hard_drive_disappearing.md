---
title: "hard drive disappearing"
date: 2006-04-08
forum: General Help
---

### Post by lozzd on 2006-04-08
Hey,

I hope this is in the right section. I never really know where to put threads on this forum.

I'm running a server on Ubuntu, using console only. Its running absolutely fine, couldn't be better, except... All my hard drive space is just disappearing. At a very slow rate. 

If I do a "sudo du -h -s" in / it tells me:

```
4.2G    .
```

Am I right in thinking this command will tel me the overall usage on the drive based on actual files? 
It differs quite a bit from my actual usage:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0               33G   27G  4.2G  87% /

```

I can't really see what can gradually and consitently taking up more room. I keep deleting all my Apache logs, but I'm getting to the point where my if I "du" my log folder, its only 160mb. 

Does anyone know anywhere else data could just be piling up?! Where is it all going?
I would just buy a bigger hard drive and fit it but my server is co-located in London which isn't the easiest of places to just pop in and put a new drive in! 

Help!

Thanks,
Laurie

---

### Post by DavidTangye on 2006-04-08
It sounds like you might need to find individual files that are getting very big. Try ...
> find / -size +1G
If that fails try +100M etc

---

### Post by halfvolle melk on 2006-04-08
Maybe ~/.Thrash is getting full.

---

### Post by lozzd on 2006-04-08
[QUOTE=DavidTangye]It sounds like you might need to find individual files that are getting very big. Try ...

If that fails try +100M etc[/QUOTE]

Hmmm it won't accept either G or g or M or m. So i typed 1000 and a few large files showed up but I'm talking under a meg. What the hells going on :/

---

### Post by lozzd on 2006-04-08
[QUOTE=halfvolle melk]Maybe ~/.Thrash is getting full.[/QUOTE]

I have no idea what that is, but there's only one file in there and its 120k big.

---

### Post by halfvolle melk on 2006-04-08
That's /.Trash btw (your trash bin), sorry about that. Also 'du' only checks from the dir it's executed from. Like this:

```
jz@bc:/$ cd ~   *<- your home dir*
jz@bc:~$ du -hs
923M    .
jz@bc:~$ cd /   *<- root of file system*
jz@bc:/$ sudo du -hs
Password:
5.2G    .
```

---

### Post by lozzd on 2006-04-08
[QUOTE=halfvolle melk]That's the ./trash btw, sorry about that. Also 'du' only checks from the dir it's executed from. Like this:

```
jz@bc:/$ cd ~
jz@bc:~$ du -hs
923M    .
jz@bc:~$ cd /
jz@bc:/$ sudo du -hs
Password:
5.2G    .
```[/QUOTE]

Ah ok, that could possibly by why its confusing me. So if I do it from /, it won't tell me the hard drive usage on the entire drive, of all the files?

---

### Post by halfvolle melk on 2006-04-08
[QUOTE=lozzd]So if I do it from /, it won't tell me the hard drive usage on the entire drive, of all the files?[/QUOTE]
AFAIK (not that much ;) ) it will give a summary of all mounted devices*, that's what it appears to do here anyway. Also throw in the 'sudo' if performing this from root to prevent a whole lot of these:
```
du: `./root/.gconf': Permission denied
```

*edit: I mean all mounted partitions on all mounted drives.

---

### Post by lozzd on 2006-04-08
[QUOTE=halfvolle melk]AFAIK (not that much ;) ) it will give a summary of all mounted devices, that's what it appears to do here anyway. Also throw in the 'sudo' if performing this from root to prevent a whole lot of these:
```
du: `./root/.gconf': Permission denied
```[/QUOTE]

Thanks hehe, I tried the sudo, and even using the grand total option and looking into it, as far as i can see it counts all recursive subdirectorys. So the 4.7gb its reporting should be the total on the drive. But somehow 27gb has disappeared? 
It's annoying because I really don't think I could have 27gb of data on this drive. 4.7gb sounds about right.

---

### Post by halfvolle melk on 2006-04-08
Last trick I know
```
sudo du|sort -n
```
You can tweak that command a bit more, but I don't know how from the top of my head. Check 'man du' for that.

---

### Post by lozzd on 2006-04-08
[QUOTE=halfvolle melk]Last trick I know
```
sudo du|sort -n
```
You can tweak that command a bit more, but I don't know how from the top of my head. Check 'man du' for that.[/QUOTE]


Hmm thats confirms my theory that the disk is being filled randomly with nothing, as that reports:

1504520 ./var
1586928 ./usr
4343728 .

So basically with the older core folders, and all added up (4343728) thats the 4.7gb that is being used on the hard drive. 

Thanks for your help but this isn't pleasing me very much :P Where is my hard drive disappearing to?!

---

### Post by lozzd on 2006-04-09
Erk, well, my time is running out. Anyone else got any ideas why my system is reporting so many GB to have just disappeared?

Thanks in advance!

---

### Post by Celerex on 2006-04-09
```
cd /
sudo du -chs *
```


This will give you a dump much like this:
```

95M     bin
104K    boot
0       cdrom
4.0K    command
5.7M    data
848K    dev
14M     etc
1002M   home
2.7M    include
900K    info
4.0K    initrd
0       initrd.img
284M    lib

... yada yada ...

3.0M    share
4.0K    srv

... more yada yada ...

1.5G    usr
1.3G    var
31G     total

```

Then, once you know the big folders are, go into those folders and repeat the du command to try and find your big files. Good luck.

---

### Post by lozzd on 2006-04-10
Thanks for the reply, thats a good method and all but same problem. Observe my output:

```
lozzd@zebedee:~$ cd /
lozzd@zebedee:/$ sudo du -chs *
Password:
3.0M    bin
14M     boot
0       cdrom
2.7M    dev
33M     etc
137M    home
4.0K    initrd
0       initrd.img
0       initrd.img.old
123M    lib
48K     lost+found
12K     media
4.0K    mnt
4.0K    opt
907M    proc
1000K   root
8.0M    sbin
4.0K    srv
4.0K    swap
0       sys
1.2M    tmp
1.6G    usr
1.8G    var
0       vmlinuz
0       vmlinuz.old
4.5G    total

```

Same problem again. 4.5G total. 

```
lozzd@zebedee:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0               33G   28G  3.7G  89% /
```

Help!!

Thanks

---

### Post by lozzd on 2006-04-10
Ok for the future information of anyone that has this problem, if you happen to be coloocated many miles away from your server and run a RAID, don't reboot. I'm off to London to see how much data I really have left.

---

### Post by Celerex on 2006-04-10
Wow. First sorry about the reboot thing.

This might indicate that there's a bigger problem with your hardware. DU and DF not matching is not good. I'm sure when you're there you'll run all the tools you need to. Good luck.

---

### Post by lozzd on 2006-04-10
[QUOTE=Celerex]Wow. First sorry about the reboot thing.

This might indicate that there's a bigger problem with your hardware. DU and DF not matching is not good. I'm sure when you're there you'll run all the tools you need to. Good luck.[/QUOTE]

Well, now I've calmed down let me clarify that a bit further.

I performed a read only fsck on the supposedly mirrored RAID array. Infact, I even checked they were mirrored just before reboot. They supposedly were. The fsck turned up so many errors you wouldn't believe, which is slightly worrying considering there isn't anything which should've corrupted any data, as everything was working ok (apart from the apparent free space disappearing). So, I was trying to reboot to perform a full fsck so it could fix the errors, when the RAID died and decided it'd needed to sync. Which fails every time. 

Turns out I didnt get to the datacenter today, as my car broke down. Guess who wasn't having a very good day? So I'm up bright and early and hopefully will have a better stroke of luck. 

Thanks for your help.

---

