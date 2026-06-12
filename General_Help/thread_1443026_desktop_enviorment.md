---
title: "desktop enviorment"
date: 2010-03-30
forum: General Help
---

### Post by joshbrice on 2010-03-30
is it possible to have more than one enviorment than just gnome?

---

### Post by bobcollard on 2010-03-30
> **joshbrice said:**
> is it possible to have more than one enviorment than just gnome?
A resounding YES might be in order.  You have the basic building block, Ubuntu already installed.  Check out Synaptic Pacakge Manager for Kubuntu-desktop or Xubuntu-desktop, that's KDE or Xfce for those who know them by their common names.   There are others, too many to mention here with small differences but those are the basics.  Then after installing them you have a choice in your login page with the choose button on the bottom left.  Once chosen it will not change until you change it.  Of course to get the full benefit from any desktop you should install the whole thing.  You can dual boot any different version.

---

### Post by uRock on 2010-03-30
Yes, you can install LXDE, KDE, or XFCE with ```
sudo apt-get install kde
``` ```
sudo apt-get install xfce
``` ```
sudo apt-get install lxde
```
By installing these packages, which are also in Synaptic Package Manager if you prefer to instal via GUI, you may log out, click on your screen name then select which desktop environment you want to use. For more info check out these links [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde) [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
Meh... dual-boot to try them I would say. Or a live CD. In my experience it can cause more trouble than it's worth to have more than one.

---

### Post by uRock on 2010-03-30
> **bobcollard said:**
> A resounding YES might be in order.  You have the basic building block, Ubuntu already installed.  Check out Synaptic Pacakge Manager for Kubuntu-desktop or Xubuntu-desktop, that's KDE or Xfce for those who know them by their common names.   There are others, too many to mention here with small differences but those are the basics.  Then after installing them you have a choice in your login page with the choose button on the bottom left.  Once chosen it will not change until you change it.  Of course to get the full benefit from any desktop you should install the whole thing.  You can dual boot any different version.

Keep in mind that when installing with this method, the previous desktop is uninstalled.(has happened to me)

---

### Post by t0p on 2010-03-30
> **iRock said:**
> Keep in mind that when installing with this method, the previous desktop is uninstalled.(has happened to me)

When exactly did this happen to you?  I have Hardy installed on one of my computers, with ubuntu-desktop, kubuntu-desktop and xubuntu-desktop all installed and available, right now.

Oh yes, a note to the OP: if you decide to try installing any/all of the alternative environments, you need to know that the packages are called ubuntu-desktop, kubuntu-desktop and xubuntu-desktop.  They are *not* called Kubuntu-desktop and Xubuntu-desktop, as bobcollard claims.  With Unix-type operating systems, case is vitally important.

---

### Post by uRock on 2010-03-30
> **t0p said:**
> When exactly did this happen to you?  I have Hardy installed on one of my computers, with ubuntu-desktop, kubuntu-desktop and xubuntu-desktop all installed and available, right now.

Oh yes, a note to the OP: if you decide to try installing any/all of the alternative environments, you need to know that the packages are called ubuntu-desktop, kubuntu-desktop and xubuntu-desktop.  They are *not* called Kubuntu-desktop and Xubuntu-desktop, as bobcollard claims.  With Unix-type operating systems, case is vitally important.

Very recently with Lucid. I installed Ubuntu, then installed lubuntu-desktop and it removed ubuntu-deshtop on my netbook. When installing just the "lxde" I can select which to use from the login menu.

(I like the new avatar.)

---

### Post by carlosgs91 on 2010-03-30
,

---

### Post by uRock on 2010-03-30
> **carlosgs91 said:**
> As I use Ubuntu I install kde by typing this:

[sudo apt-get install kubuntu-desktop](sudo apt-get install kubuntu-desktop)

Which install the entire Kubuntu distro. If I just install kde with that code, what will happen? Will I have a KDE fully working environment but without the KDE programs like Kopete, Konsole, ...?

I have tried all but KDE, but it only installed the necessary dependencies for the DE, not all of its programs.

---

### Post by t0p on 2010-03-31
> **iRock said:**
> Very recently with Lucid. I installed Ubuntu, then installed lubuntu-desktop and it removed ubuntu-deshtop on my netbook. When installing just the "lxde" I can select which to use from the login menu.

Wow, that is a crazy state of affairs.  I don't bother with it so much now, but some time ago I had great difficulty choosing whether to go witn ubuntu, Kubuntu and Xubuntu so I installed all three desktop environments so I could compare them easily.  I'd love to know what exactly was the devs' rationale in making only one environment installable at the time.  For the sake of Eris, choice is the numero uno big feature of Linux.  If the devs have decided to make that choice as exclusive as you suggest, they must have gone crazy.  What is linux without freedom of choice?  Answer: a pile of window-y, OSX-y wet weak w**k.

> **iRock said:**
> 
(I like the new avatar.)

Well thank you very much!  I've loved this character since the first time I clapped eyes on him.  Papa Lazarou is the best ringmaster and abductor of wives bar none.  *"Is Dave there?".... "You're* my *wife now*..." Brilliant!!

**Note:** For those of you who have no idea who or what a "Papa Lazarou" might be, I advise you to look at these Wikipedia articles: [Papa Lazarou]("http://en.wikipedia.org/wiki/Papa_Lazarou") and *[The League of Gentlemen]("http://en.wikipedia.org/wiki/The_League_of_Gentlemen")*... and to get the most of it, you should watch the shows, happily avaiable for download [right here]("http://www.filestube.com/a209938618fa3bc103ea,g/The-League-of-Gentlemen-S1-FULL.html").  *"Dave, Dave... you're* my *wife now!!"*... a true classic!

---

