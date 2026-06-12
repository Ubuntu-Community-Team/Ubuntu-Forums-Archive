---
title: "Ubuntu 10.04 Brasero Burning Speed problem"
date: 2010-07-31
forum: General Help
---

### Post by newmoon_h on 2010-07-31
I'm having a small issue with Brasero Disk Burner.That is burning DVD (Data Files) with Brasero is very slow. I have selected burning speed 12x and even maximum but when I give it to burn it only burns at 2.5x speed on average and takes 20 long mins to burn a dvd. I have tried different Brand's disk and in every case the same thing happens. I have used Ubuntu 9.10 before and had no issues with Brasero. I have checked the same brand's disks with a software called Imgburn in Windows 7 and all worked absolutely fine. Any idea why it is happening in Ubuntu 10.04 only?

---

### Post by darolu on 2010-07-31
I have never been a fan of Brasero; I use [Gnome Baker]("https://help.ubuntu.com/community/GnomeBaker") and I have never had a single problem with it, maybe it will work for you too, give it a try.

Sometimes I use the command line to burn CD/DVD disks, specially when I have to burn .iso images, the (in my opinion) most popular CLI burning software is **wodim**, you may want to try it as well, if there is an error it will be printed in your terminal, here's a link with its manual (man): [http://man.cx/wodim(1)](http://man.cx/wodim(1))

---

### Post by deserthowler on 2010-08-01
I have 2 different machines, one using 10.04 with Brasero and one using 9.10 with k3b.  They both burn CDs fast but can only do about 4-5x write speed on DVDs.  I think DVD write is just slow.

Earl

---

### Post by R33D3M33R on 2010-10-28
Please see this bug: [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/628710](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/628710)

---

### Post by perixx on 2010-11-03
Uh-oh. 

So they found a bug, a low priority one, that is. Writing DVD's at a speed below 2x. Here, it's below 1x speed. 
The second time I'm supposed to start searching what's been messed up now. Or booting into my trusty old Windows box for doing the business. Last time the problem was disabled DMA by default (couldn't believe this, but I had to).

Goddamnit, not only I have no sound (yes or no, it's a surprise with every new distro!), it's also Brasero crapping out again, business as 'usual'. I'd be tempted to say: OK, the Xfce base is the culprit. But I also tried Ubuntu to no better result. 
Video tearing is imminent with the open source drivers - I've read that only kernel 2.35 will get me rid of this... with Ubuntu? Yeah, when compiling an own kernel perhaps, or waiting another 6 months to find out things didn't change at all with the next release. 
All in all it seems, the more polished this baby's surface gets, the less careful developing and reliability is going on.

In three years of Uubuntu experience, it wasn't the fact that there ARE bugs, giving me a hard time, it's HOW they appear: with mind-destroying persistence. Just remembering that infamous Thunar-bug with hidden files which took them boys over a year to address and another request and release to get that fix from backports. The sound mess with Alsa and Pulse and other problems. Now - again - DVD burning. For the same reason I've been switching to Mint at version 9.04, until I finally caught a rootkit. Well, now I'm back in Ubuntu-trouble it seems. But before I waste any more time with all this, I'll give Suse Linux another shot and maybe 'aptosid' (daft name but if it's worthwhile...).  

perixx

---

### Post by R33D3M33R on 2010-11-04
Yeah, it's low priority and it will probably expire, because nobody seems to care about it. I just switched back to Kubuntu, I have less bugs with it.

---

### Post by perixx on 2010-11-04
> **R33D3M33R said:**
> Yeah, it's low priority and it will probably expire, because nobody seems to care about it. I just switched back to Kubuntu, I have less bugs with it.As for me, I found Kubuntu 
a) too bloated and 
b) less stable and less well-designed
in comparison to Xubuntu or Ubuntu. Plus, I've seen better designed KDE distributions and I like to K.I.S.S. :)
That's why I'm looking for an alternative right now. From a philosophy point of view, Debian Sid is certainly one of my favourites. And there are others...

perixx

---

