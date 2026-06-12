---
title: "Absolute newcomer needs some help please"
date: 2006-03-02
forum: General Help
---

### Post by ninebob on 2006-03-02
Hello all!

I'm a regular to forums, but a newbie to linux, so "kid gloves" please!

I would consider myself to be a proficient computer user, some would say expert, but my experience so far has been solely with windows. I've been able to to re-build friend's computers, format, partition and re-install windows, drivers etc without problem. Recently I've had Linux recommended to me, so I thought I'd give it a go. Not least because I dislike Micro$$$oft at the best of times - I've already ditched Office in favour of OpenOffice for windows.

The deciding factor was a blog I read by one of my favourite authors, Max Barry - it's here: [http://www.maxbarry.com/2005/02/22/news.html](http://www.maxbarry.com/2005/02/22/news.html) 

So, I ordered my ubuntu CDs, and when they arrived I've managed to get through the install without too much difficulty. (I think I f*cked it up a tiny bit, and created one more partition than I needed to, but I have a big enough HDD and can still dual-boot XP and Ubuntu with no problems, so I can live with my mistake until I reformat and start again).

However, I need help with the following:

1. From my Ubuntu desktop, I can't see my "other" drive - i.e. I can't access any of the documents, programs, music or other files from windows. What this means is that although I love the feel of Ubuntu, all I can use it for at the moment is web browsing. I could do with some pointers in the direction of becoming more integrated!

2. In windows, I run 2 monitors, with the desktop simply extended onto the 2nd. In Ubuntu, the GRUB screen and loader screen are cloned to the second monitor (much like windows), but upon arriving at the desktop only the primary monitor works, with just gibberish on the secondary.

That's all for now - I'm hoping someone can help! Once I can access my existing files from Ubuntu I'll probably be asking more, like how to install winamp and so on (if I don't figure it out myself). Looking forward to learning more about the previously unknown world of linux.........

Cheers,
Simon :')

---

### Post by o_fortuna on 2006-03-02
[QUOTE=ninebob]Hello all!

I'm a regular to forums, but a newbie to linux, so "kid gloves" please!

I would consider myself to be a proficient computer user, some would say expert, but my experience so far has been solely with windows. I've been able to to re-build friend's computers, format, partition and re-install windows, drivers etc without problem. Recently I've had Linux recommended to me, so I thought I'd give it a go. Not least because I dislike Micro$$$oft at the best of times - I've already ditched Office in favour of OpenOffice for windows.

The deciding factor was a blog I read by one of my favourite authors, Max Barry - it's here: [http://www.maxbarry.com/2005/02/22/news.html](http://www.maxbarry.com/2005/02/22/news.html) 

So, I ordered my ubuntu CDs, and when they arrived I've managed to get through the install without too much difficulty. (I think I f*cked it up a tiny bit, and created one more partition than I needed to, but I have a big enough HDD and can still dual-boot XP and Ubuntu with no problems, so I can live with my mistake until I reformat and start again).

However, I need help with the following:

1. From my Ubuntu desktop, I can't see my "other" drive - i.e. I can't access any of the documents, programs, music or other files from windows. What this means is that although I love the feel of Ubuntu, all I can use it for at the moment is web browsing. I could do with some pointers in the direction of becoming more integrated!

2. In windows, I run 2 monitors, with the desktop simply extended onto the 2nd. In Ubuntu, the GRUB screen and loader screen are cloned to the second monitor (much like windows), but upon arriving at the desktop only the primary monitor works, with just gibberish on the secondary.

That's all for now - I'm hoping someone can help! Once I can access my existing files from Ubuntu I'll probably be asking more, like how to install winamp and so on (if I don't figure it out myself). Looking forward to learning more about the previously unknown world of linux.........

Cheers,
Simon :')[/QUOTE]
1. It's very easy to get windows partitions mounted and accessible. Follow [this]("https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28windows%29") guide from the Ubuntu Wiki (which, by the way, is a wonderful resource).

2. You should use Twin View, I think. Find the guide [here.]("http://www.ubuntuforums.org/showthread.php?t=85769")

---

### Post by steve.horsley on 2006-03-02
munting windows partitions:
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

### Post by Sutekh on 2006-03-02
[QUOTE=ninebob]

1. From my Ubuntu desktop, I can't see my "other" drive - i.e. I can't access any of the documents, programs, music or other files from windows. What this means is that although I love the feel of Ubuntu, all I can use it for at the moment is web browsing. I could do with some pointers in the direction of becoming more integrated![/QUOTE]

Have a read of this link to show you how to 'mount' windows partitions, so that you can access them from Ubuntu

[Mounting Windows Partitions in Ubuntu - by ]("http://www.psychocats.net/linux/mountwindows.php")[aysiu]("http://ubuntuforums.org/member.php?u=21941")

[QUOTE=ninebob]
2. In windows, I run 2 monitors, with the desktop simply extended onto the 2nd. In Ubuntu, the GRUB screen and loader screen are cloned to the second monitor (much like windows), but upon arriving at the desktop only the primary monitor works, with just gibberish on the secondary.[/QUOTE] I don't know much about using two monitors, but if you search for things like 'dual head', 'multiple monitors', 'twinview' you should find plenty of information.

[QUOTE=ninebob]
That's all for now - I'm hoping someone can help! Once I can access my existing files from Ubuntu I'll probably be asking more, like how to install winamp and so on (if I don't figure it out myself). Looking forward to learning more about the previously unknown world of linux.........

Cheers,
Simon :')[/QUOTE]
There are winamp clones for Linux (you will rpobably find it very difficult to install winamp)

[XMMS - X Multimedia System]("http://www.xmms.org/")

Can be installed using **apt-get**
```
sudo apt-get install xmms
```

[BMP - Beep Media Player]("http://beep-media-player.org/site/BMPx_Homepage")

Can be installed by enabling the universe repository through this link [Enabling Extra Repositories - by ]("http://www.psychocats.net/linux/sources.php")[aysiu]("http://ubuntuforums.org/member.php?u=21941")

Then installed using **apt-get**
```
sudo apt-get install beep-media-player
```

---

