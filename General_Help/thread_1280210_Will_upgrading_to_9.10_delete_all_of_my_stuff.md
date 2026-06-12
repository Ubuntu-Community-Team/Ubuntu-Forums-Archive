---
title: "Will upgrading to 9.10 delete all of my stuff?"
date: 2009-10-01
forum: General Help
---

### Post by thnikk on 2009-10-01
So I'm considering upgrading to 9.10 I just want to know if it will delete all of my stuff before I install. Any help would be appreciated.

---

### Post by JC Cheloven on 2009-10-01
If you upgrade (not fresh-install), your files, programs and settings will survive.
It will not hurt to make a backup of your important files first, though.

---

### Post by thnikk on 2009-10-01
oh ok, thanks a lot ^^

---

### Post by dcstar on 2009-10-01
> **thnikk said:**
> So I'm considering upgrading to 9.10 I just want to know if it will delete all of my stuff before I install. Any help would be appreciated.

Set up a separate /home partition and any upgrade/reinstall will not touch your user data.

Leaving /home in the root partition means that it is always going to get wiped when an install is done.

---

### Post by oboedad55 on 2009-10-01
> **thnikk said:**
> So I'm considering upgrading to 9.10 I just want to know if it will delete all of my stuff before I install. Any help would be appreciated.

Just bear in mind that 9.10 is still a beta. There are things that don't work so well yet. If you like experimenting or testing have at it. Otherwise if you have a working system why not keep it?

---

### Post by sigurnjak on 2009-10-01
Since we are on subject of upgrade   , what happens to all my extra ppa repos  ? Do they get updated or i should remove them before upgrade ?

---

### Post by dearingj on 2009-10-02
> **sigurnjak said:**
> Since we are on subject of upgrade   , what happens to all my extra ppa repos  ? Do they get updated or i should remove them before upgrade ?

They'll be disabled during the upgrade, but kept on the list so you can re-enable them later.

---

### Post by CheetahDC on 2009-10-02
> **dcstar said:**
> Set up a separate /home partition and any upgrade/reinstall will not touch your user data.

Leaving /home in the root partition means that it is always going to get wiped when an install is done.

How do I set up a seperate /home partition?

---

### Post by MaxIBoy on 2009-10-02
> **dcstar said:**
> Set up a separate /home partition and any upgrade/reinstall will not touch your user data.

Leaving /home in the root partition means that it is always going to get wiped when an install is done.
That's only if you do a fresh install. Upgrading without reinstalling outright will not delete anything.

On the other hand, while none of your personal files get deleted, you MIGHT have issues with programs getting screwed up, graphics drivers not working, etc. Such problems will either not exist, or they will take up to a day to work through. Which is why some people advise to back up your files first anyway. But these problems rarely require a reinstall to fix them. (Unless you've done some heavyduty customization, in which case you know enough to recover without reinstalling anyway.)

---

### Post by JC Cheloven on 2009-10-02
> **CheetahDC said:**
> How do I set up a seperate /home partition?
Many gnu-linux users prefer to setup a /home partition. I don't find it useful. I usually make a separate partition for my data, and have the discipline of using it, instead of my /home/name_of_user directory.

Since I like to have several distros / OSes in my computer, this eases a lot having alll my files at hand. 

Just another point of view.

---

### Post by pricetech on 2009-10-02
Three words:
Backup
Backup
Backup

I've been trying for years to get that across to people BEFORE they lose their stuff.  Sometimes it takes AFTER they lose their stuff, sometimes it doesn't.

---

