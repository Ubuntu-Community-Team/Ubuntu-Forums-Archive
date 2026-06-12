---
title: "Cannot update ffmpeg libavdevice52 libavfilter0"
date: 2011-04-05
forum: General Help
---

### Post by jamesisin on 2011-04-05
I started this thread earlier today but it vanished, so here it is again.

I have three packages that will not update:

```
ffmpeg libavdevice52 libavfilter0
```

The Update Manager notified me of them, but they were not checked and would not be checked.  I ran all other updates.  Then I tried running the updates manually:

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ffmpeg libavdevice52 libavfilter0
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

I also tried the usual fixit stuff for apt-get:

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

Same end.

This is happening on three of five machines running 10.04 (including one 64bit machine).

What to do?

---

### Post by NoNameWill on 2011-04-05
I am getting the same thing.  I tried to re-install through synaptic and it said that those won't reinstall because the a repository is missing. So I un-installed ffmeg and now that wont install because of unresolved dependencies. :confused: This was supposedly a security update. 

I did a ```
sudo apt-get update
```
Then ```
sudo apt-get auto remove
``` This removed the rest of the Kdenlive program that FFmeg removed with it's removal. 
So how do we fix this? TIA

---

### Post by plucky on 2011-04-05
Its a Bug 

See [Bug Report](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/751114) and affects me as well.

Good Luck

---

### Post by jamesisin on 2011-04-05
I commented on the bug report and linked that back to this thread.  If anyone has additional information they should contribute to the bug report directly though.

---

### Post by wduda on 2011-04-05
I solved this this way:

```
sudo apt-get install libavutil49
```

and then:

```
sudo apt-get install ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0
```

I don't know if it is a proper way, but seems to solve conflicts.

---

### Post by jamesisin on 2011-04-05
How did you come to decide upon libavutil49 and what is it?

---

### Post by wduda on 2011-04-05
> **jamesisin said:**
> How did you come to decide upon libavutil49 and what is it?

When I was trying to upgrade today by:

```
sudo apt-get upgrade
```

i was informed that these packeges can't be upgraded:

```
ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0
```

After that I was trying to reinstall them by:

```
sudo apt-get install ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0
```

and than I got info about packets conflicts as in the [bug]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/751114") description, where is:

```
Depends: libavutil49 but it is not going to be installed
```

So i decided to install libavutil49 first.
Is it working for you ?

---

### Post by FrancisT on 2011-04-05
> **wduda said:**
> When I was trying to upgrade today by:

```
sudo apt-get upgrade
```

i was informed that these packeges can't be upgraded:

```
ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0
```

After that I was trying to reinstall them by:

```
sudo apt-get install ffmpeg libavdevice52 libavfilter0 libavformat52 libpostproc51 libswscale0
```

and than I got info about packets conflicts as in the [bug]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/751114") description, where is:

```
Depends: libavutil49 but it is not going to be installed
```

So i decided to install libavutil49 first.
Is it working for you ?

It worked for me with a few bobbles as various other packages deinstalled themselves automatically and needed to be reinstalled. Specifically xvidcap removed itself and when I readded it, it removed vlc so I had to readd that.

```

sudo apt-get install libavutil49
sudo apt-get install libavdevice52 libavformat52 libpostproc51 libswscale0
sudo apt-get install xvidcap
sudo apt-get install vlc-nox vlc-plugin-pulse vlc mozilla-plugin-vlc

```

It looks to me like the various AV dependency trees have got tangled

---

### Post by panzet on 2011-04-06
Hello, same happens to me, on Ubuntu 10.04 64 bits.

When I installed libavutil49 (as have been said in other post in this thread), a lot of soft and dependencies were removed. It includes VLC, Mplayer, Openshot and also some DVD authoring and DVD ripping soft (Devede, DvdStyler,etc...)

It also actualized ffmpeg, libavdevice52 and libavfilter0, and installed libavcodec52, libavformat52, libpostproc51 and libswscale0.

I've been trying to reinstall all software desinstalled, and I succesfully installed most, without dependencies problems, but not for Devede, Dvd-slideshow, Dvdstyler...

And also, I've noted that some dependencies removed were very similar than the newer ones, but the last without "-extra-",  for example, it installed libavcodec52, uninstalling libavcode**c-extra-**52

Definitely, I'm not an expert on Ubuntu, only a user at home and work, but... maybe this is a problem with two different versions of one dependencies (one with -extra- and other without it) needed by different programs?? It appears that Devede, DVDStyler, etc... need the dependencies with '-extra- and other soft needed the 'newer' ones. Surprisingly, DVDrip didn't needed these dependencies, an I installed it.

At this moment, I've using VLC more than devede or dvdstyler,, so I will try with this configuration, hoping that dependencies troubles will be solved soon...

Sorry for my english!

Panzet

---

### Post by Paddy Landau on 2011-04-06
Affects me as well on three machines:
 
[LIST]
[*]Ubuntu Lucid 32-bit
[*]Ubuntu Lucid 64-bit
[*]Lubuntu Lucid 32-bit
[/LIST]
 It seems to be widespread.

When you [visit the bug]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/751114"), remember to vote for it (the green bit at the top).

---

### Post by Silvernail on 2011-04-06
When I ran 'check' from the update manager I get this error message.
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFF96872D340A3
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5


---

### Post by dirty_harry on 2011-04-06
> **wduda said:**
> 

```
Depends: libavutil49 but it is not going to be installed
```So i decided to install libavutil49 first.
Is it working for you ?

worked, thx

---

### Post by Cavsfan on 2011-04-06
Should be good to go now. I just got all 6 updates via CLI commands although Update Manager also showed 6 available updates.
Yesterday, there were 3 held back I would guess waiting on the other 3 as they needed to go together.

---

### Post by jamesisin on 2011-04-06
Agreed.  This afternoon I was able to download nine updates (including the three formerly uncheckable updates) through the Update Manager.  Looks like it took a whole day for the open source community to fix the bug they created yesterday.  I'm impressed.

---

### Post by pqwoerituytrueiwoq on 2011-04-06
> **jamesisin said:**
> Agreed.  This afternoon I was able to download nine updates (including the three formerly uncheckable updates) through the Update Manager.  Looks like it took a whole day for the open source community to fix the bug they created yesterday.  I'm impressed.
it was about 2 or 3 days 
i check for updates every day
now i have to figure out why winetricks will not update automatically (wants to partial upgrade)

---

### Post by windowsconvert09 on 2011-04-06
Confirmed, a *sudo apt-get update* allowed the updates to be checked in Update Manager.

---

### Post by Paddy Landau on 2011-04-07
A quick [look at the bug]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/751114") shows it was fixed.

---

