---
title: "GIMP: Wacom Bamboo Pen acting flaky"
date: 2011-10-18
forum: General Help
---

### Post by Nickel1010 on 2011-10-18
I'd find it hard to explain this without a picture, so:

[IMG]http://i.imgur.com/S7K9M.jpg[/IMG]
In this picture, I only drew inside of the red circle. All other offshooting lines are the issue I'm having.

I have my Wacom Bamboo Pen tablet working with pressure sensitivity in gimp, but unfortunately something very odd seems to be happening. The cursor seems to shoot off of the screen, rendering the tablet unusable.

Hardware related, maybe? I cannot see the mouse on screen actually moving, only the lines in gimp. The mouse appears to stay in the original position, which leads me to believe the problem is confined to gimp. Also, it seems a bit strange that the lines only shoot off at three different angles: 45 degrees, 180 degrees, and 90 degrees.

---

### Post by Favux on 2011-10-18
Hi Nickel1010,

This is a known problem with Oneiric (I assume you are in Oneiric).  We started a thread on the Oneiric forum, unfortunately it was too close to release.  See this Launchpad bug report:  [https://bugs.edge.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.edge.launchpad.net/ubuntu/+source/gimp/+bug/863154) and the Gimp bug report:  [https://bugzilla.gnome.org/show_bug.cgi?id=661872](https://bugzilla.gnome.org/show_bug.cgi?id=661872)

Hopefully with Alexia Death's contribution a fix is on the way.  As soon as someone from Ubuntu notices the bug report anyway.  So feel free to join the Lauchpad bug report or at least mark that it affects you.

---

### Post by Nickel1010 on 2011-10-19
Yes, I'm using Oneiric, silly me for not stating that.

Good to know it's not just me experiencing this, I'll add myself to the bug report.

Thanks!

---

### Post by osarusan on 2011-10-19
Yes, hopefully everyone with the bug will sign up. It hasn't gotten noticed the the bug team yet, so we'll likely need to get more people on there before anything gets done about it.

---

### Post by ulrichvonbeck on 2012-01-03
This is exactly what I'm seeing in gimp on my Ubuntu (11.11) box.  Anyone know if there is a fix yet?

---

### Post by Favux on 2012-01-03
Hi ulrichvonbeck,

Yes.  Install Aapo Rantalainen's PPA with Alexia Death's disable Gimp history buffer patch applied to Gimp:  [https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline](https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline)

---

### Post by fragos on 2012-01-04
You can get GIMP 2.7.4 with the Wacom fix by installing the ppa withe the following CLI. 

sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn
sudo apt-get update && sudo apt-get install gimp

It works very well for me. It's probably the last development release before GIMP 2.8 comes out.

---

