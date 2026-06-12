---
title: "Flash very unreliable"
date: 2009-12-11
forum: General Help
---

### Post by Replicon on 2009-12-11
Hi all,

I'm sure this has been discussed before, but I'm not finding the info just now.

For a while, I've been finding that flash is fairly lame on firefox. It will work fine, and then all of a sudden, just grey out, usually when opening another page with flash content.

For example, if I have a youtube video open, and I start middle-clicking on related videos (which opens more tabs with flash content from youtube), the video just turns into a grey square. The npviewer.bin process becomes defunct as part of this. Usually, just refreshing the page fixes it, but it's really lame that it breaks like this to begin with.

Then sometimes, it breaks in a similar manner, except I have to fully restart firefox to get it to work at all. In those cases, when I run strace on npviewer.bin, I see this:

```

...
select(11, [10], NULL, NULL, {0, 0})    = 0 (Timeout)
gettimeofday({1260515683, 731572}, NULL) = 0
gettimeofday({1260515683, 731607}, NULL) = 0
gettimeofday({1260515683, 731639}, NULL) = 0
gettimeofday({1260515683, 731673}, NULL) = 0
read(4, 0x80a50c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x806d34c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x806d34c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN}], 1, 0)     = 0
gettimeofday({1260515683, 731846}, NULL) = 0
poll([{fd=5, events=POLLIN}, {fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=10, events=POLLIN}], 4, 0) = 0
select(11, [10], NULL, NULL, {0, 0})    = 0 (Timeout)
read(3, 0x806d34c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x806d34c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN}], 1, 0)     = 0
read(4, 0x80a50c4, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x806d34c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x806d34c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN}], 1, 0)     = 0
gettimeofday({1260515683, 732192}, NULL) = 0
...

```

Looks like some resource doesn't get properly released or something, and it's waiting on it to free up.

Anyway, I'm pretty sure I have the latest and correct version (how do I check again?) - is this something that has a known fix that doesn't involve building flash plugin from source?

cheers

---

### Post by garvinrick4 on 2009-12-11
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=black][FONT=Verdana] Ensure the evil "libflashsupport" library is **not** installed:  [COLOR=#000000]Code:[/COLOR]
 $ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
 [COLOR=Blue]**Note:** the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]
[/FONT][/COLOR][/SIZE][/FONT]

---

### Post by garvinrick4 on 2009-12-11
If you want a new flash install:


sudo apt-get remove flashplugin-nonfree

sudo apt-get clean

sudo apt-get install flashplugin-nonfree



The Clean just purges system and fetch's a new one from repositories when requested.
Instead of using same one over again.

---

### Post by zaphod777 on 2009-12-11
Also I have found that the newly released chrome browser has flash built in and works very well.

It's fast I don't have any of the random issues that I had before in Firefox.

---

### Post by Replicon on 2009-12-12
Hmm, still not working right. I didn't have any of the evil packages installed, and installing a new flashplugin-nonfree didn't resolve the issue.

According to synaptic, I am running flashplugin-nonfree version 10.0.1.218+really9.

I'm on 8.04, and running FF 3.0.15.

It's actually been like this since I went from 7.10 to 8.04, just never bothered to look into it until now. :)

---

### Post by spoon_ on 2009-12-12
I know this happens on 64-bit systems with the flash plugin that you get from the repositories. The fix is to get the 64-bit flash plugin from Adobe: [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

---

### Post by Replicon on 2009-12-12
> **spoon_ said:**
> I know this happens on 64-bit systems with the flash plugin that you get from the repositories. The fix is to get the 64-bit flash plugin from Adobe: [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

Thank you! This fixed the problem. I manually ran the key parts of the script here:

[http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html)

Looks like it's working great now!

---

