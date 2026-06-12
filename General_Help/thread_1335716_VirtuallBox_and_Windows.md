---
title: "VirtuallBox and Windows"
date: 2009-11-23
forum: General Help
---

### Post by Squegee on 2009-11-23
My family just bought a new computer, and along with the new computer they bought Windows 7, for some reason. Now that I have a faster computer I am looking to play more games, some of which might require windows, so i installed VirtualBox to install windows and play games, but I know windows likes to be registered. If I install my copy of windows 7, will I need to register it, and if I do will I be unable to use that same copy of windows for anything else, like if my parents decide to use it later instead of Linux?

---

### Post by blur xc on 2009-11-23
I don't think it works that way...  I have a "friend" that had a Vista home premium disk, and intalled at along side Ubuntu in a dual boot setup, but also used the same disk to make a Vista VM in Vbox, both work fine, both are registered and upgrade normally.

I read somewhere that MS tolerates "pirating", even though, imo, this is a weak case of pirating, because it helps maintain their market share, and they'd also rather have secure (by allowing updates) pirate windows installs than unsecured ones, to help control malware spread, if that makes any sense.

BM

---

### Post by bodhi.zazen on 2009-11-23
You need to read the Microsoft EULA and contact Microsoft if you have questions.

---

### Post by Spectre5 on 2009-11-23
> **Squegee said:**
> My family just bought a new computer, and along with the new computer they bought Windows 7, for some reason. Now that I have a faster computer I am looking to play more games, some of which might require windows, so i installed VirtualBox to install windows and play games, but I know windows likes to be registered. If I install my copy of windows 7, will I need to register it, and if I do will I be unable to use that same copy of windows for anything else, like if my parents decide to use it later instead of Linux?

Unfortunately this solution won't work very well (regardless of the licensing issues, which I believe that having it installed virtually would count).  In Virtualbox, you won't get hardware acceleration so you won't be able to run many newer/graphics games in VirtualBox.

You should check out Wine and Cedega for playing windows games in Linux - though it will generally be hit or miss for whether they work or not.  See the [Wine Database]("http://appdb.winehq.org/index.php") for a list of games and how well others have gotten them to work under Wine.  Sometimes a little tweak in Wine can make the difference of the game playing well and it playing unacceptably.

Also check out some of the Linux games - some will probably impress you more than you might think.  See Nexuiz, Battle of Wesnoth, Tremulous, AssaultCube, Urban Terror, Saurbraten, Glest, FreeCiv, Warzone 2100, Wormux, etc, etc...

---

### Post by snowpine on 2009-11-23
bodhi.zazen is correct as always

my opinion is that a virtual installation of Windows "counts" as one license just like any other installation... why wouldn't it?

---

### Post by blur xc on 2009-11-23
> **snowpine said:**
> bodhi.zazen is correct as always

my opinion is that a virtual installation of Windows "counts" as one license just like any other installation... why wouldn't it?

Well, imo, the stupid thing is that some Windows version don't allow being run in a VM per their EULAs.


BM

---

### Post by UranUtan on 2009-11-23
The OS doesn't know if it runs in a VM. Especially when you connect to MS to activate. The Activation server doesn't care on which machine your Win7 is installed.

So VM or physical machine, from the license perspective, it's identical. You know the solution already. Train your parents to use Linux.

---

### Post by MelDJ on 2009-11-23
> **Squegee said:**
>  I am looking to play more games, some of which might require windows, so i installed VirtualBox to install windows and play games,

why? virtualbox only supports directx8. so its quite impractical as many new games need directx>8

---

### Post by Squegee on 2009-11-24
I kinda figured i would have to register windows but I wasn't sure, and as for games i run some games with wine, but some of work, some don't so I was just looking for an alternative. Thanks for the advice/help, I don't think I will install windows and I can just hope to get lucky with some games 
Thanks again

---

### Post by sabre2th on 2009-11-24
One thing I've done off and on is to run Windows normally for games, with an Ubuntu VM for everything else.  It's not ideal, but it accomplishes what you're looking for as far as games and desktop environment.

Just food for thought

---

### Post by Spectre5 on 2009-11-24
> **sabre2th said:**
> One thing I've done off and on is to run Windows normally for games, with an Ubuntu VM for everything else.  It's not ideal, but it accomplishes what you're looking for as far as games and desktop environment.

Just food for thought

Then why run Ubuntu at all?  You loose all the security and a lot of other benefits of running Ubuntu/Linux...

---

### Post by sabre2th on 2009-11-24
> **Spectre5 said:**
> Then why run Ubuntu at all?  You loose all the security and a lot of other benefits of running Ubuntu/Linux...
It's for someone that wants to use a Linux desktop but needs native Windows capabilities.

For the record, Windows is not going to spontaneously burst into flames.  With Vista and Win7, you're perfectly safe unless you do something to cause problems (ie. clicking on things you shouldn't, etc.).

---

### Post by t0p on 2009-11-24
> **sabre2th said:**
> 
For the record, Windows is not going to spontaneously burst into flames.  With Vista and Win7, you're perfectly safe unless you do something to cause problems (ie. clicking on things you shouldn't, etc.).

That's a really irresponsible thing to post.  Vista is well-known for causing computers to spontaneously combust.  This is why Vista disks came bundled with a fire extinguisher.  A workaround was to install Vista in a VM, as virtual flames burn cooler than real fire.

We no longer need to worry about Vista, now Windows 7 has been released.  But we need to be aware that 7 comes with its own risks.  In the UK it is mandatory to wear protective headgear whilst operating Windows 7.

---

### Post by bodhi.zazen on 2009-11-24
> **t0p said:**
> That's a really irresponsible thing to post.  Vista is well-known for causing computers to spontaneously combust.  This is why Vista disks came bundled with a fire extinguisher.  A workaround was to install Vista in a VM, as virtual flames burn cooler than real fire.

We no longer need to worry about Vista, now Windows 7 has been released.  But we need to be aware that 7 comes with its own risks.  In the UK it is mandatory to wear protective headgear whilst operating Windows 7.

:lolflag:

---

