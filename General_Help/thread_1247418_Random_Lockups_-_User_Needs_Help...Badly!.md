---
title: "Random Lockups - User Needs Help...Badly!"
date: 2009-08-22
forum: General Help
---

### Post by elraymundo on 2009-08-22
Hello everyone,

I'm very, very new with Linux, so please be gentle. :)

I recently upgraded from 8.04 to 9.04 (going through the process of upgrading to 8.10 in-between) and while using both 8.04 and 9.04 my machine completely locks up, apparently at random.

When I say the machine locks up, I mean this:

1. The mouse does not move. The pointer icon is frozen.
2. The keyboard does not work. No combination of keys works at all.
3. I have to reboot to get out of the locked-up state.
4. The lock-ups seem to happen regardless of the app I am using (it has happened while browsing different sites, while not having a browser open at all, while opening a PDF, while switching between virtual windows, etc).
5. I was running Gnome and this evening, at the recommendation of a friend, I switched to KDE and removed Gnome. The lock-ups continue.
6. The lock-ups happen anywhere from two minutes after I reboot to 90 minutes-ish after I reboot. I've surfed for quite a long time and had no issues until the lock-up occurred and surfed the exact same site for two minutes and had the machine lock-up.

The problem is I really have absolutely no idea how to even begin troubleshooting this. I need someone who is willing to work through this with me. Can anyone lend a hand? I'd sure appreciate it - this is making me absolutely nuts.

Thanks!!

---

### Post by dearingj on 2009-08-22
Do you have any other operating systems installed, such as Windows or another flavor of Linux, and do these lockups happen when you're running those systems?

---

### Post by zkriesse on 2009-08-22
Do you have one or the ability to burn an ISO image of the latest version of Ubuntu? I think in the process of your "upgrade" you may have messed more than a few things up.

---

### Post by elraymundo on 2009-08-22
The machine is running Kubuntu 9.04 as the only OS. It was running Ubuntu 8.04 and Ubuntu 9.04 before I switched to KDE and nuked Gnome.

I can burn an ISO easily enough. But I wonder if that is the problem, since the lock-up issue existed when I had 8.04 as well? (The 8.04 lock-ups are what made me stop using Ubuntu for quite a while. I only recently...like yesterday...decided to give it another try.)

---

### Post by elraymundo on 2009-08-23
Hi everyone,

I hope you haven't given up on me yet. :)

Last night I did a fresh install of 9.04 on my machine. I did not wipe the hard drive first - I just reinstalled from DVD using an ISO image.

The lock-ups have decreased in frequency, but they still occur. Two hours ago I left to meet my wife at the store - the browser was open to a relatively static site (no crazy flash or other scripted stuff running on the site) and no other apps open on my machine. When I came home, the machine was locked up - no mouse movement, no keyboard, nothing. Reboot.

Does anyone have any ideas what the problem might be? I'd like to get this fixed and then move my wife's machine over to Ubuntu as well, but I'll have a hard time justifying it if I can't even get the browser to work consistently.

If I decide to do another install from disk, should I wipe the hard drive first? Is it worth the trouble? And if I do wipe the hard drive, how do I do that?

Any help is very much appreicated! :)

---

### Post by clackamas on 2009-08-23
I had been struggle with random locks while surfing the web.  However, I believe I found the application causing the problem in my case:

It is the Gecko Multimedia player.  

After completely un-installing the Gecko Player and using Adobe's flash install instead, I have not had any trouble with web browsing related lockups.

---

### Post by dearingj on 2009-08-23
I really doubt that the Gecko player is to blame in this case, as elraymundo did mention that these crashes happen when the browser is not showing any flash content and when there is no browser running at all, however I would recommend installing Adobe's flash player anyway because I have found it to be much more stable than other flash players.

Elraymundo- have you tried pressing ctrl+alt+F1 when these crashes happen? If it works, that will take you to a terminal where you can at least shut down your system safely.

---

### Post by Monkey.feets on 2009-08-24
Could be a hardware issue that has nothing to do with OS.  Sometimes a bad RAM stick or overheated CPU can cause lockups.

Try running Memtest86 to check RAM for issues.

After your system locks and you reboot if you go into CMOS you can see the CPU temp, if it is exceedingly high you may need a new fan and heatsink.

---

