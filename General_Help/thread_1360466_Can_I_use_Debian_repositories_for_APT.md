---
title: "Can I use Debian repositories for APT?"
date: 2009-12-20
forum: General Help
---

### Post by Mike_IronFist on 2009-12-20
I know that not all Ubuntu packages are binary compatible with Debian due to some changes Ubuntu developers have made, but from what I can tell, it's not vice-versa; It seems like when a developer makes a .deb file that works with Debian, it should also work with Ubuntu.

So, is my assertion correct here? Would I be able to use the Debian Sid repositories without destroying my system?

---

### Post by sgosnell on 2009-12-20
Yes.  I occasionally enable the Debian repositories for apps that aren't in the Ubuntu repositories.  Just be careful, or you might end up with broken dependencies down the line.

---

### Post by Mike_IronFist on 2009-12-20
> **sgosnell said:**
> Yes.  I occasionally enable the Debian repositories for apps that aren't in the Ubuntu repositories.  Just be careful, or you might end up with broken dependencies down the line.

Thanks for the info! I just really wanted the more up-to-date stuff from Debian Sid. I used Sidux and found it a poor substitute for Ubuntu, but I think combining the two would be a fun experiment.

---

### Post by ad_267 on 2009-12-20
Eh, you  can, but it's not a good idea. I wouldn't be surprised if it wasn't long before your dependencies were all stuffed and you can't install anything.

It's OK to install a couple of apps from the debian repos that don't have other stuff depending on them, but anything else and you're asking for trouble.

---

### Post by bodhi.zazen on 2009-12-20
If you are wanting to do this you should, IMO, learn to use pinning :

[https://wiki.ubuntu.com/PinningHowto](https://wiki.ubuntu.com/PinningHowto)

Take care, just because it is a .deb does not mean it is compatible and adding debian repositories and mindlessly running "apt-get update && apt-get dist-upgrade" is asking for problems =)

---

### Post by Mike_IronFist on 2009-12-21
> **bodhi.zazen said:**
> If you are wanting to do this you should, IMO, learn to use pinning :

[https://wiki.ubuntu.com/PinningHowto](https://wiki.ubuntu.com/PinningHowto)

Take care, just because it is a .deb does not mean it is compatible and adding debian repositories and mindlessly running "apt-get update && apt-get dist-upgrade" is asking for problems =)

Thanks for the advice, I almost made a dire mistake there! Well, that's what the UbuntuForums are for.

---

### Post by HappyFeet on 2009-12-21
> **Mike_IronFist said:**
> I just really wanted the more up-to-date stuff from Debian Sid.

You are better off installing PPA packages for more up to date stuff.

---

### Post by dcstar on 2009-12-21
> **HappyFeet said:**
> You are better off installing PPA packages for more up to date stuff.

Or enable the Backports option for newer packages from the next version that may be made available.

---

### Post by Mike_IronFist on 2009-12-21
Thank you everyone. I appreciate your quick responses.

---

