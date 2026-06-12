---
title: "qbittorrent Torrents turn Invisable during activation"
date: 2011-10-27
forum: General Help
---

### Post by TBerk on 2011-10-27
What happens is either newly added torrents or pre-existing torrents look to have been deleted when you double-click on them.

The expected result is that they toggle from inactive to active.

If you have the right settings you can see them 'running' by the activity in the Title bar via Global Up/Down traffic.

Clicking on the 'Stop ALL' button allows them to re-appear.  Very strange.

I'm of a mind one of two things have taken place to cause this; 

- Dependency and/or some other recent patch/update (as in patched just today) And/Or

- Some most recently added torrent w/ the ability to purposely or inadvertently cause the problem.

It seems I'm not the only one because a bug has been logged which I think describes the problem:

**Torrent names and stats disappear**
[https://bugs.launchpad.net/bugs/882090]("https://bugs.launchpad.net/bugs/882090")

I'm not sure what other forum to start this in, so here we are in General Help...


TBerk

---

### Post by TBerk on 2011-10-27
Current versions:


Ubuntu - 10.10
Qbittorrent - 2.4.3-0ubuntu1
libtorrent-rasterbar6 - 0.15.4-0ubuntu1

---

### Post by xyzzyman on 2011-10-27
You should add the qbittorent ppa to get the latest version 2.9.0 as you are very much behind. In the terminal type:

sudo add-apt-repository ppa:hydr0g3n/ppa
sudo apt-get update && sudo apt-get install qbittorrent

That'll update your qbittorrent. As you can see there have been lots of updates and fixes since your version: 

[http://www.qbittorrent.org/news.php](http://www.qbittorrent.org/news.php)

Not promising it will fix it but couldn't hurt.

---

### Post by TBerk on 2011-10-27
I'm going to try that, last night I was compiling the latest version but hadn't switched over....

OK, I ran:

> sudo add-apt-repository ppa:hydr0g3n/ppa
sudo apt-get update && sudo apt-get install qbittorrent

and it did indeed update my version to 2.9.0 but it didn't change the behaviour.

When you (re)activate a torrent it will turn invisible on the list of torrents, but seem to behave normally otherwise. What it means in practical terms is that I lose control of tracker revision, observation of available sources, peers, etc.

---

### Post by haqking on 2011-10-27
> **TBerk said:**
> I'm going to try that, last night I was compiling the latest version but hadn't switched over....

you dont need to compile anything, you can download a .deb from the website or as above use the PPA which would be preferred method to maintain updates

I suppose i should too seeing as i am using version 2.2 :) but it works fine so havent botherd updating it ;-)

---

### Post by TBerk on 2011-10-27
Yeah, I understand compiling isn't necessary but that's what I was doing anyway.

What I had most recently done, as explained above, is to run:

```

sudo add-apt-repository ppa:hydr0g3n/ppa
sudo apt-get update && sudo apt-get install qbittorrent

```

I'm current @ v2.9.0.   Still has the same behaviour.

I'm looking at a second system, w/ the same Ubuntu patches (but obviously differing hardware) that still works OK, for similarities and differences.

Next would be a root canal and reinstall of qBT.

---

### Post by dniMretsaM on 2011-10-27
2.9.1 is out. Upgrade and give it a try.

---

### Post by xyzzyman on 2011-10-27
Have you tried deleting/renaming the ~/.config/qBittorrent folder and let it start with a fresh config file? Maybe it's corrupted? That's a brute way of fixing some problems but lots of times it works even though you never understood what broke to begin with.

---

### Post by TBerk on 2011-11-01
> **xyzzyman said:**
> Have you tried deleting/renaming the ~/.config/qBittorrent folder and let it start with a fresh config file? Maybe it's corrupted? That's a brute way of fixing some problems but lots of times it works even though you never understood what broke to begin with.

I thought of this but hadn't tried it yet; been a busy last few days.

Having just checked it's behaviour and found no change, I'm going to pursue this now and report back...


~/.local/share/data/qBittorrent/   was found @ 

/home/my_host_name/.local/share/data
  
[ I mention this because if you are looking for that 1st location w/ a GUI based file utility (Nautilus started w/ gksudo for example...) it's easier to find.  ]

In any case I deleted said directory, uninstalled qBit and reinstalled.

Didn't help any. Torrents still turn invisible when activated.


gonna go check the bug being tracked for this...

---

### Post by TBerk on 2011-11-06
> **xyzzyman said:**
> Have you tried deleting/renaming the ~/.config/qBittorrent folder and let it start with a fresh config file? Maybe it's corrupted? That's a brute way of fixing some problems but lots of times it works even though you never understood what broke to begin with.

OK, this seems to have solved my problem BUT I hadn't actually enabled 'show hidden files/folders' in my search like I thought I had. 

So I didn't find these folders, I thought they were non-existent, and so they remained to trip me up each time I reinstalled Qbittorrent.

This is my Mea Culpa.

That said I'm marking this 'solved' even though it didn't really get the whole forensic treatment and everything.

Thx to all who replied.


TBerk

---

