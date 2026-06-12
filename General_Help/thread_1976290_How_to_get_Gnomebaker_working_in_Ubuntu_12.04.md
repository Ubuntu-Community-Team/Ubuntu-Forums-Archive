---
title: "How to get Gnomebaker working in Ubuntu 12.04?"
date: 2012-05-08
forum: General Help
---

### Post by MrsUser on 2012-05-08
I tried to install Gnomebaker following this instruction:

[http://www.liberiangeek.net/2012/04/how-i-installed-gnomebaker-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/how-i-installed-gnomebaker-in-ubuntu-12-04-precise-pangolin/)

However, when starting Gnomebaker, it throws an undefined error. Did anyone get Gnomebaker to work in Ubuntu 12.04 (64-bit)?

---

### Post by billmnfl on 2012-05-19
I see this has been here for a few weeks.  Does anyone have any ideas how to get gnomebaker working in Ubuntu 12.04 Precise 64 bit? 
I tried the same thing that is listed in the previous post, but no joy.
Please help.

---

### Post by MrsUser on 2012-10-02
GnomeBaker 0.6.4 now available for Ubuntu 12.04 via PPA:

[http://www.iloveubuntu.net/gnomebaker-064-available-ubuntu-1204-ppa](http://www.iloveubuntu.net/gnomebaker-064-available-ubuntu-1204-ppa)

```
sudo add-apt-repository ppa:gnomebaker/stable
sudo apt-get update
sudo apt-get install gnomebaker
```

---

### Post by jerrrys on 2012-10-02
I don't know anything about Gnomebaker, but k3b works really sweet and its in the software center.

---

### Post by MrsUser on 2012-10-02
I tried Gnomebaker. It works very well and is stable. Tested burning a few CDs and DVDs, also rewritable ones. Everything went fine. It's by far better than Brasero (which produces mostly damaged CDs). The only thing that bugs me about Gnomebaker is a sound that is being played when the burn process is finished. It's loud as hell and it can't be switched off in prefs.

So I guess I'll use K3b then, even though I don't like to install KDE components.

---

### Post by raja.genupula on 2012-10-02
> **jerrrys said:**
> I don't know anything about Gnomebaker, but k3b works really sweet and its in the software center.

Hi Jerry 

+1 to K3B

---

### Post by The Cog on 2012-10-02
xfburn is another option - it's been reliable for me. It's more-or-less the opposite of k3b: lightweight with very few options. Depends what on your personal taste, really.

---

### Post by jerrrys on 2012-10-02
Hi raja

@MrsUser
Yes k3b will dump kde dependencies on you and maybe we both should take a look at xfburn.  K3b just works, but lighter is better :) 

And about that gnomebaker wake-up call; don't look good :(

[http://sourceforge.net/tracker/?func=detail&aid=1886245&group_id=127397&atid=708502](http://sourceforge.net/tracker/?func=detail&aid=1886245&group_id=127397&atid=708502)

---

### Post by MrsUser on 2012-10-03
I had tried Xfburn already and didn't have any good experience with it. For instance, it wasn't able to handle rewritable DVDs. It was almost as disappointing as Brasero. Besides, why Ubuntu developers still set Brasero as the default burn app is beyond me. A burn app is a vital standard basic app that should work out of the box, no matter what. They'd be much better off with Gnomebaker, even with this annoying sound effect. At least, Gnomebaker works and is solid and stable. It didn't fail any of the burn tests I did with it. K3b, of course, is the best burn app for Linux. Unfortunately, it's a KDE app. It'd be nice to have something that is completely Gnome compliant. Gnomebaker can do that, even though it's not as feature-rich as K3b. But at least it does the basic job well. If only this sound effect... seriously, this is the only thing that keeps me from using it. A small thing, but it ruins the whole usage. I don't want to get startled each time a burn process finished. And I don't want to mute my whole machine either.

---

### Post by The Cog on 2012-10-03
That's odd. 
I burned a rewritable DVD+rw only 3 days ago with xfburn.

But I've used k3b as my fall-back for years. It was reliable long before any others (that I could find) were. And unless you use it, the KDE libraries just sit on disk. So go for k3b.

---

### Post by MrsUser on 2012-10-04
Maybe Xfce burn improved. It's been a while since I tried it. Oh, and yes, I guess I'll go back to K3b again. Although I'd really love to use a Gnome compliant app.

---

