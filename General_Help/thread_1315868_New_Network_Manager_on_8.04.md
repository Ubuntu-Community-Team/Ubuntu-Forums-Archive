---
title: "New Network Manager on 8.04?"
date: 2009-11-05
forum: General Help
---

### Post by t0p on 2009-11-05
I've got 8.04 on my desktop computer and I don't want to upgrade yet.  But I would like the extra functionality of the latest Network Manager.  How could I go about installing it?

---

### Post by t0p on 2009-11-06
bump

---

### Post by t0p on 2009-11-08
No one?   :(

I found [this]("http://ubuntuforums.org/showthread.php?t=884656"), but it's for Network Manager 0.7.  That is, Intrepid's network manager.  I guess I could try that.  But I'd prefer it if I could update to the latest iteration.

---

### Post by jollysnowman on 2009-11-08
I believe the packages are nm-applet and network-manager-gnome.

---

### Post by t0p on 2009-11-08
> **jollysnowman said:**
> I believe the packages are nm-applet and network-manager-gnome.

When I look up those packages in Synaptic, it tells me I have got the latest versions.  This is because I *have* got the latest versions - for Hardy.  The Hardy repos do not contain the versions released for Intrepid/Jaunty/Karmic.

What I need is a way to get those packages... and to get them working (I'm sure there will be a shed-full of dependencies that I won't be able to get either).

---

### Post by jollysnowman on 2009-11-08
Ooooh ok. Try these links:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by t0p on 2009-12-07
Thanks jollysnowman, but none of those links are helpful.

Because of the problems I'm experiencing [here]("http://ubuntuforums.org/showthread.php?t=1348644"), doing something about the awful network manager in Hardy is once again a priority.  So I'm back to searching for a solution as to get a newer version of network-manager installed on my Hardy box.

I thought maybe backports would solve my problem  But I looked through the [list of Hardy backports]("http://packages.ubuntu.com/hardy-backports/") available and - no network manager.

I returned to this post about how IntuitiveNipple had made Network Manager 0.7 available for Hardy.  I decided to give it a go - I followed the instructions on [his wiki]("http://tjworld.net/wiki/Linux/Ubuntu/Hardy/NetworkManager0.7") - but to no avail.  Apt-get still says that I have the  most recent versions already installed. (I'm going to pm IntuitiveNipple about that.)

So, I'm back to the drawing board.  To sum up: I want to replace the network manager in Hardy (version 0.6.6) with a newer version.  If anyone knows how I might do this, please post a reply.

---

