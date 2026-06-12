---
title: "Memory usage and ways to minimise it."
date: 2011-06-01
forum: General Help
---

### Post by Prosthetic Head on 2011-06-01
My apologies if this has already been addressed, but I've need unable to through the search.

The default Ubuntu install is no longer comfortable in 512MB of RAM which I what I have on my old Thinkpad X32 and don't really want to upgrade. I'm not trying to do anything that I couldn't do fine with 512MB and Ubuntu 8.04. On upgrading to 11.04 everything works much better at log in, but as soon as I start using software centre and firefox at the same time or similar it starts swapping and grinds to a halt.

I don't blame the ubuntu devs for focusing on features on modern-ish systems rather than efficiency on older systems but I would be nice for this system to remain usable. 

So, Does anyone have any suggestions of thinks to installed, kill, block or change to minimise RAM use without breaking normal functionality?

Thanks!

---

### Post by Locke_99GS on 2011-06-01
Disable or remove GNOME autostart entries that you don't require or use, and consider alternative softwares which may be more lightweight. Examples include Chrome (Chromium) is relatively lightweight yet still full featured, and Midori, which is a featherweight browser.

---

### Post by Smart Viking on 2011-06-01
My suggestion is to not use ubuntu 11.04.

Use debian stable minimal with xfce4 or something similar and you will have more control and less stuff running, or try 10.04 if you really want to use ubuntu. There is lots of stuff out there that an old computer can run fine.

---

### Post by Locke_99GS on 2011-06-01
I agree with Smart Viking. 

A simple alternative, and a personal favourite of mine, is [Lubuntu]("http://lubuntu.net"). Lubuntu 11.04 uses just under 100M RAM idling after login on my laptop, and about 80M on my buddies older PC.

---

### Post by Prosthetic Head on 2011-06-01
Ok, thanks for suggestions - I'll try killing unnecessary services first and if I still get frequent swapping I'll give lubuntu a go. I share the laptop with a non-technical user so usability is important and I don't have much spare time to build up what I want from a debian minimal install.

I've also been recommended crunch-bang. Has anyone tried it?

Cheers!

---

### Post by binkles on 2011-06-01
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

LXDE is a good WM

---

### Post by marios88 on 2011-06-01
I use XFCE on old PCs and an LTS version

---

### Post by binkles on 2011-06-01
> **marios88 said:**
> I use XFCE on old PCs and an LTS version

XFCE isnt particularly light.

---

### Post by claracc on 2011-06-01
I am using lucid lynx in an old pentium III laptop, 512 Mb ram from which 64 Mb go for sis graphics card.

This is not a plane but is usable (more than when it had win xp) for surfing the web, read newspapers and  watch videos with mplayer or flash ( flash videos are the worst part,   the slower ones). Of course I suppose you don't have any visual effect and are using metacity.

I recommend:
As it has een yet recommended quit some apps booting at start which you don't need, i.e.: bluetooth, evolution alarm notifier,  if you don use evolution,...
To reduce swappiness:  vm.swappiness=10 in /etc/sysctl.conf (real ram is faster than swap memory)
Check in reduced_resources key in apps-->metacity--> general, running gconf-editor.
Create a file in /home/name_of_user/ with the name .gtkrc-2.0 and write on it: gtk-menu-popup-delay = 100 (to reduce time for pop menus in gnome)
Use a lighter browser than firefox, i.e. epiphany.

I know that gnome is slower than xcfe but for me is nicer, customizable and have lots of configuration possibilities, and I am comfortale with it.

---

### Post by binkles on 2011-06-01
Another option is to add another 512mb ram stick

---

### Post by ivanovnegro on 2011-06-01
> **Prosthetic Head said:**
> 

I've also been recommended crunch-bang. Has anyone tried it?

Cheers!

Yes, Crucnhbang is really light, and very good, it uses Openbox or Xfce, if you dont want to tinker too much, I would recommend Xfce.

> **binkles said:**
> XFCE isnt particularly light.

It is lightweight, so the Ubuntu version obviously not strictly but also this would work with 500 MB of RAM, so to the OP, if you want to use Xubuntu also Ubuntu, remove Firefox, use Chromium or Midori, remove the big audio players, use Audacious or DeaDBeef, use Abiword instead of LibreOffice. Remove everything you dont need, also the Software Center, use Synaptic, faster. 
In my case Xubuntu runs with about 400 MB with Firefox but that could be the limit for you if you open more things. So, Lubuntu is definiteley worth the try and also Crunchbang. To be more familiar of course Lubuntu, it comes yet with lighter apps on the resources.

---

