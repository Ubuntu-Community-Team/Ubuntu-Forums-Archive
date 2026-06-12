---
title: "old computer setup xubuntu whats the difference?"
date: 2010-11-02
forum: General Help
---

### Post by Vigh on 2010-11-02
hi, I have an old celeron 2Ghz, 256mb ram and want to install linux on it, I presume xubuntu is the best bet, what is the key difference between xubuntu and ubuntu? thanks

ant

---

### Post by TheAnachron on 2010-11-02
Xubuntu is basically like Ubuntu.
It is optimized for slow pcs.

While ubuntu has many applications that come with it, it is also quite big.
Xubuntu does not install that many apps, thus being smaller, however, you won't be able to do that much as in ubuntu by default.

---

### Post by WorMzy on 2010-11-02
Ubuntu uses [GNOME]("http://en.wikipedia.org/wiki/GNOME") as it's desktop environment. Xubuntu uses [Xfce]("http://en.wikipedia.org/wiki/Xfce").

---

### Post by TheAnachron on 2010-11-02
@WoRMzy I said that already? :P
[QUOTE="TheAnachron"]While ubuntu has many applications that come with it, it is also quite big.
Xubuntu does not install that many apps, thus being smaller, however, you won't be able to do that much as in ubuntu by default.[/QUOTE]
[QUOTE="Wikipedia"]Xfce (pronounced as four individual letters)[1] is a free software desktop environment for Unix and other Unix-like platforms, such as Linux, Solaris and BSD. It aims to be fast and lightweight, while still being visually appealing and easy to use.[/QUOTE]

---

### Post by WorMzy on 2010-11-02
Not really, you made no mention of either GNOME or Xfce. ;)

---

### Post by matt_symes on 2010-11-02
Hi

OP. Read the minimum specs for both.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You'll need more memory for Gnome.

Kind regards

---

### Post by TheAnachron on 2010-11-02
I assumed (and it looked like) he has no idea about desktop enviroments. I was trying to make it easier for him to just give a quick view about what both systems are made for.

---

### Post by sanderd17 on 2010-11-02
with 256 MB RAM, Xubuntu will have just enough to run, don't expect it to run easy. You could try the even smaller but unofficial Lubuntu (with Lxde instead of gnome or Xfce). Lubuntu is made to run with 128 MB RAM, so 256 will give you enough space to run your apps like they should. Lubuntu is not so old, so there might still be a few bugs in it.

If you do lots of things on the web, you might also try Peppermint OS, it's an unofficial derivate from ubuntu and uses also Lxde (like Lubuntu), but it comes with less apps than Lubuntu, the primary use is mailing, surfing chatting ... But you can still install all programs you are able to install in Ubuntu.

Btw: If you ask yourself how much different DEs (desktop environments) there are, there are 4 quite big players and some other small.

KDE is a bling-bling DE, everything is done to make it shiny.
Gnome is trying to look polished, not too much bling.
Xfce wants to have a lot of configuration possibilities (like Gnome and KDE) but use less memory than Gnome.
Lxde wants to use as less memory as possible and still provide a workable environment.

---

### Post by Vigh on 2010-11-05
okay fantastic so how do i set up Lxde on ubuntu distribution/ xubuntu distribution? regards

---

### Post by WorMzy on 2010-11-05
Simply install the lubuntu-desktop package.

```
sudo apt-get install lubuntu-desktop
```

Log out, and log back in. Pay attention to the login window though, you may need to choose to log into a LXDE session rather than a gnome session. If you can't see an option to choose, then you may need to restart before it'll show up.

---

### Post by phredbull on 2010-11-05
I have a similar spec'd computer, (P4 2.0gHz, 512 mb), and when I tried a live USB of Mint Isadora Fluxbox, it was the snappiest and most responsive my machine's ever been. I would use it, but I choose to sacrifice a bit of performance for eyecandy and stick with Gnome w/Compiz.

---

### Post by mastablasta on 2010-11-05
[QUOTE=sanderd17;10061638]with 256 MB RAM, Xubuntu will have just enough to run, don't expect it to run easy. QUOTE]
 
don't know about xubuntu but Ubuntu 10.04 on 256Mb ram runs just fine. nothing fast or fancy. it needs about 120-130 MB ram for system the rest goes to any applications you launch.
 
Lubuntu runs even better. and takes about 80 MB ram. which leaves more for applications. but on my notebook it recognised less keys and also the 10.04 version was showing batery lifetime incorrectly (or was it using it more?!), so i went with gnome (clearlooks theme, removed background pic).

---

### Post by cascade9 on 2010-11-05
> **sanderd17 said:**
> KDE is a bling-bling DE, everything is done to make it shiny.
Gnome is trying to look polished, not too much bling.
Xfce wants to have a lot of configuration possibilities (like Gnome and KDE) but use less memory than Gnome.
Lxde wants to use as less memory as possible and still provide a workable environment.

KDE- not that 'bling bling (I hear that from gnome users quite often...you do know yu dotn have to run kwin desktop effects, and if you do compiz is just as 'bling bling' 

Lxde- Errr.....doesnt openbox/fluxbox (etc) use less memory? They provide a 'workable enviroment' as well. 

> **TheAnachron said:**
> Xubuntu is basically like Ubuntu.
It is optimized for slow pcs.

While ubuntu has many applications that come with it, it is also quite big.
Xubuntu does not install that many apps, thus being smaller, however, you won't be able to do that much as in ubuntu by default.

Optomised for slow PCs? LOL. Try a minimal install of Xfce4 on ubuntu, compare it to xubuntu-desktop. :P 

@ Vigh- I'd try minimal Xfce as well as lubuntu. 

I'm biased, I dotn like lxde, I'll admit that. But I dont find that  Lxde is worth the extra annoyance compared to a minimal xfce. Your mileage and opnion may vary...

---

