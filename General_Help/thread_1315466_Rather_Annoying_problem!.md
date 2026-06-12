---
title: "Rather Annoying problem!"
date: 2009-11-05
forum: General Help
---

### Post by Wink2tall on 2009-11-05
:mad: Every time Ubuntu starts up, all of the windows and programs are connected to the top left corner with not menus (file, edit, view, etc.) and I found the way to fix it until I reboot, or restart. I have to open System > Preferences > Appearance and under the visual effects tab, it's always set to No Visual Effects and when I change it to either Normal or Extra, it performs a search for the drivers, and then all of the menus pop up and the windows and programs are no longer stuck in the upper left corner. Any idea's. Is my hardware just not set to read at startup or something of the sort. Any Help Appreciated! Thanks!

---

### Post by kio_http on 2009-11-05
Your problem is a graphic card driver one. Specify your graphic card model please.

---

### Post by ManiacDan on 2009-11-05
Those settings in the appearance menu are related to Compiz, which is the "fancy window settings" manager.  Go into synaptic package manager and install compizconfig-settings-manager.  That will drop a "compiz configuration" app into your preferences, which you can use to configure all kinds of neat stuff.  It may also prevent your settings from resetting.

-Dan

---

### Post by Wink2tall on 2009-11-05
Already have the Compiz Manager, I thought I might have tweaked something in there that caused this, but after I reset everything back, it still does it after a reboot or shutdown. I can tell you that I am using a Dell Inspiron 1501 on the newest version of Ubuntu, 9.10. 


01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]

It worked in 9.04 so I don't see why I should have a problem in 9.10.

---

### Post by regala on 2009-11-05
> **Wink2tall said:**
> It worked in 9.04 so I don't see why I should have a problem in 9.10.

whereas I do: do not upgrade to next Ubuntu release in the first month, it's always been that crappy :)

br

---

### Post by Iowan on 2009-11-05
Karmic is not crappy, it's just... unrefined. :D

---

### Post by Wink2tall on 2009-11-06
Lol yeah that's true. Well I would guess the main problem is that it isn't loading the driver when UBuntu starts...

---

### Post by P4man on 2009-11-06
I believe the X200M is blacklisted for known issues with compiz. I thought it was like that in 9.04 as well.

---

### Post by regala on 2009-11-06
> **P4man said:**
> I believe the X200M is blacklisted for known issues with compiz. I thought it was like that in 9.04 as well.

the real problem here is that if you have that blacklisted chip, X goes berserk instead of not doing anything. This is a regression AFAIK.

---

### Post by coffeecat on 2009-11-06
> **Wink2tall said:**
> Already have the Compiz Manager, I thought I might have tweaked something in there that caused this, but after I reset everything back, it still does it after a reboot or shutdown.

I may be misunderstanding your problem, and I certainly have no experience of ATI cards (don't intend to), but there is one CompizConfig Setting Manaager setting you might want to double-check.

Open CCSM > Window Management > Place Windows > Placement Mode. What setting do you have there? I don't like the default (whether compiz is enabled or not) where Windows open top-left. I've set that to "Centered", but that's my personal choice.

---

### Post by P4man on 2009-11-06
> **regala said:**
> the real problem here is that if you have that blacklisted chip, X goes berserk instead of not doing anything. This is a regression AFAIK.

The OP says he cant enable desktop effects, which is exactly what blacklisting should result in. Perhaps Im missing something?

---

### Post by Wink2tall on 2009-11-07
The odd thing is, when Ubuntu starts up, all I have to do to fix the problem is go to system > preferences > appearance > visual effects and change it to normal or extra and my windows aren't stuck anymore. When I do that it says looking for drivers and works fine. But before I do that, none of the windows have the minimize, maximize, and exit buttons in the upper corner... Any idea how I could get it to just load the driver on start-up.

---

### Post by regala on 2009-11-09
> **P4man said:**
> The OP says he cant enable desktop effects, which is exactly what blacklisting should result in. Perhaps Im missing something?

blacklisting will prevent the driver to load for that specific card. So Desktop Effects won't work. But they're enabled by default. So they "start", try to do their stuff with no real opengl support, compiz won't start. The regression is that metacity should start as fallback after compiz crashes (he must forget desktop effects, he won't have them). In fact, compiz shouldn't start as default WM in gnome, if it means getting a totally screwed Desktop when you have a blacklisted card...

---

