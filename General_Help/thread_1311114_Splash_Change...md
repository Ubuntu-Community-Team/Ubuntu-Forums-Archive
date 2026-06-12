---
title: "Splash Change.."
date: 2009-11-02
forum: General Help
---

### Post by HarshReality on 2009-11-02
While I am certain the source is unavailable.. Can anybody point me to 2 things..

1. Tutorial on changing the boot splash
2. Location online to acquire boot splash animations.

The end goal is something similar to:
[http://troy-sobotka.blogspot.com/2009/07/karmic-ubuntu-910-boot-sequence-concept.html](http://troy-sobotka.blogspot.com/2009/07/karmic-ubuntu-910-boot-sequence-concept.html)

---

### Post by Giblet5 on 2009-11-02
You can find that and other goodies at gnome-look.org but I wouldn't spend a lot of effort trying to create your "Animated Hypnosis-Generating Fractals usplash v0.01"... There are rumors that usplash will go away.

I installed kubuntu-desktop so that I could have a choice as to interface style. That changed the usplash to the usual blue Kubuntu Knight Rider theme.

It's only there for 5-10 seconds anyway...

---

### Post by HarshReality on 2009-11-02
Understandable.. however as this is going on my lappy and wont be getting the 'tweakers' upgrades that isnt a true concern. I 'wish' they would have taken all the submissions and added a repo package for the additional startup animations rather than having to search all over the web for things.. but then its all part of the game with just about any version of 'nix.

---

### Post by Giblet5 on 2009-11-02
> **HarshReality said:**
> Understandable.. however as this is going on my lappy and wont be getting the 'tweakers' upgrades that isnt a true concern. I 'wish' they would have taken all the submissions and added a repo package for the additional startup animations rather than having to search all over the web for things.. but then its all part of the game with just about any version of 'nix.

I do agree... But usplash is a horrible kluge. It runs during a stage of the boot process when there is no reliable way to test current hardware to ensure that it will work. People like me, who know how to write new subsystems like usplash from scratch, don't want to waste time on that while there are bigger fish to fry.

One rumor is that "[Plymouth]("http://www.phoronix.com/scan.php?page=article&item=fedora_plymouth&num=1")" will be the new usplash.

---

