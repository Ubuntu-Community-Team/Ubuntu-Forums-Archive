---
title: "Ubuntu or Xubuntu on older machine?"
date: 2006-06-22
forum: General Help
---

### Post by Cable on 2006-06-22
We have an older HP computer here that is currently running Win98SE.  It crawls!  But the Win98 install has been on there for a while, so it's not fresh by any means.  Anyway, it has a Pentium III CPU, 320 MB of RAM, and a nVidia GeForce 2 MX 400.  I'm thinking about installing Linux on it to help it run better/faster and to make it more usable.  Would you recommend using Ubuntu/GNOME or Xubuntu/XFCE?

---

### Post by Griff on 2006-06-22
[QUOTE=Cable]We have an older HP computer here that is currently running Win98SE.  It crawls!  But the Win98 install has been on there for a while, so it's not fresh by any means.  Anyway, it has a Pentium III CPU, 320 MB of RAM, and a nVidia GeForce 2 MX 400.  I'm thinking about installing Linux on it to help it run better/faster and to make it more usable.  Would you recommend using Ubuntu/GNOME or Xubuntu/XFCE?[/QUOTE]

My vote would be for Xubuntu, but you could try both.  I have gnome/xfce on a laptop of mine that has a little bit better hardware and I've been using xfce more and more here recently.  I think it's pretty cool having a desktop that idles at 84 MB :D.

---

### Post by bruce89 on 2006-06-22
I have Xubuntu on 380MB of memory, and a Celery 300, and it is really slow.  I would recommend Xubuntu in this case, but it depends on what speed the processor is).

---

### Post by user1397 on 2006-06-22
well considering the minumum for gnome is 256 MB RAM, it could run, but i bet it'll be pretty slow.  so i would say xfce also.

---

### Post by jimcooncat on 2006-06-22
Either one should work fine on that hardware, I prefer Xubuntu myself. You could also install both -- just add ubuntu-desktop if you install Xubuntu (or xubuntu-desktop if you use a plain dapper disk). You can then pick from the sessions menu on the login screen.

Win98SE should have performed fine on that machine, so to me it sounds as if it's plagued with some malware. Good choice to move platforms!

Also consider installing Epiphany as the default browser. You can keep Firefox, too; but you might like the snappiness of Epiphany much better.

---

### Post by K.Mandla on 2006-06-22
Definitely Xubuntu.

If you're comfortable with an even lighter installation, you might try Fluxbox or even OpenBox on a server installation. Both of those will fly, no matter what your specs (okay, so a 120Mhz P1 might have problems ... :) )

I keep a 750Mhz P3 with a lightweight XFCE installation that just plays music. I started with a server installation and added

```
sudo apt-get install x-window-system-core xfce4 xfce4-terminal thunar
```
for a bare minimum of functionality (if you're willing to use the terminal all the time, you could drop thunar; if you're willing to jump to the tty windows with CTRL+ALT+F1, etc., you could skip xfce4-terminal).

On something that needs efficiency like that, I add [Swiftfox]("http://www.getswiftfox.com"). I know there are lighter browsers, but I like a Linux-tweaked version of Firefox.

Anyways, just some ideas.

---

### Post by user1397 on 2006-06-22
[quote=jimcooncat]You could also install both -- just add ubuntu-desktop if you install Xubuntu (or xubuntu-desktop if you use a plain dapper disk). You can then pick from the sessions menu on the login screen.[/quote]although this is one way to do it, i suggest just trying out the live cd's or having ubuntu/xubuntu on different partitions, because if you install both gnome/xfce on the same partition, you might get some bugs/issues/things that will bug you so much that they'll make you want to get rid of one of the desktop environments.  anyways, if you do it anyway, make sure to install them like this (if you're installing xubuntu over ubuntu): ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```or "ubuntu-desktop" if you're installing ubuntu over xubuntu.

---

### Post by Cable on 2006-06-22
[quote=K.Mandla]

```
sudo apt-get install x-window-system-core xfce4 xfce4-terminal thunar
``` for a bare minimum of functionality (if you're willing to use the terminal all the time, you could drop thunar; if you're willing to jump to the tty windows with CTRL+ALT+F1, etc., you could skip xfce4-terminal).
[/quote] 
Well, this isn't my computer.  It's actually a family computer, so the terminal isn't really an option.  :-P  It doesn't get used much any more since it's so slow.  I believe the CPU is 500 MHz.  Anyway, I do all the computer care around here, and I don't believe it has any malware.  I just think it's a Windows install ridden with garbage slowing it down.  My brother and sister like to download lots of junk.  I just want to make it usable (decent speed) and easy for my family to use.  Maybe once it runs better it'll get used more often.  Sounds like Xubuntu is the better choice.  Currently downloading the desktop cd!

---

### Post by user1397 on 2006-06-22
make sure to use this guide, but replace all the ubuntu parts with xubuntu of course: [SIZE=2][downloading and installing ubuntu]("http://www.psychocats.net/ubuntu/iso.html")[/SIZE]

---

### Post by AskHL on 2006-06-22
That system is slightly better than my other one, which has 256 MB of RAM. That computer works very well with Xubuntu but is very slow with regular Ubuntu. I say use Xubuntu. Xfce is pretty neat too.

---

### Post by jnev on 2006-06-22
my laptop is a 366mhz pentium 2 with 256mb ram, and I have it running kde. amazingly, when it boots it consumes only ~80mb of ram. while it doesn't open any apps very quickly, it runs a lot better than you'd think it would, and it runs kde better than gnome. however, I'm currently installing fluxbox to play with it, and maybe I'll just use that for my window manager. I used to have xubuntu (xfce) but it just seemed like a lightweight DE with almost no configurability (I was probably looking in the wrong places, but it just didn't click with me).

---

### Post by bionnaki on 2006-06-23
a light-weight distro that I recommend is zenwalk.

xubuntu might be a bit heavy for you.

---

### Post by K.Mandla on 2006-06-23
[QUOTE=Cable]I just think it's a Windows install ridden with garbage slowing it down.  My brother and sister like to download lots of junk.  I just want to make it usable (decent speed) and easy for my family to use.[/QUOTE]
I shudder to mention it, but if you have the time and inclination, you could build an [nLite]("http://www.nliteos.com/nlite.html")'d version of Windows, to speed it up a little. 

Before I left Windows, I used to build custom installation CDs for some of my slower computers. I had a CTX EzBook 700E that ran at 200Mhz with 128Mb, and I set it up to stream audio off the internet with a stripped-down version of XP. If you subtract all the pointless garbage that gets installed by default, XP will run fairly smooth on old hardware.

Nlite is pretty cool, but Linux is far superior. Still, it's an option if your family doesn't like Ubuntu.

EDIT: Yay! Post #300!

---

### Post by Cable on 2006-06-23
[quote=bionnaki]xubuntu might be a bit heavy for you.[/quote]

Why is that?  Just curious...

---

### Post by Josh M on 2006-06-23
I am running Xubuntu on a PII 400Mhz, with 384Mb of ram. 

I originally installed Gnome but I found it too slow. Xfce is better, quite useable, but far from snappy.

---

