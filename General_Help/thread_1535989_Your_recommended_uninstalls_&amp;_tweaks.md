---
title: "Your recommended uninstalls &amp; tweaks"
date: 2010-07-21
forum: General Help
---

### Post by darkmaxa on 2010-07-21
I'm using Windows many years now, and always after fresh install I prefer do uninstall some useless apps and to disable useless services.

I'm new to Ubuntu, so I'm not sure what can be safely unistalled & disabled to free some disk space and speedup the system.

For now, I've unistalled UbuntuOne and disabled some (obviously) useless apps (**for me**), for example "bluetooth manager" and "remote desktop".

I've saw in the syslog that "modem-manager" loading some plug-ins during system startup. I'm not using modem, so I'm wondering is it safe to remove "modem-manager" via Synaptic?

Also, I'm interested in your suggestions in terms of system optimization. :)

---

### Post by scouser73 on 2010-07-21
> **darkmaxa said:**
> I'm using Windows many years now, and always after fresh install I prefer do uninstall some useless apps and to disable useless services.

I'm new to Ubuntu, so I'm not sure what can be safely unistalled & disabled to free some disk space and speedup the system.

For now, I've unistalled UbuntuOne and disabled some (obviously) useless apps (**for me**), for example "bluetooth manager" and "remote desktop".

I've saw in the syslog that "modem-manager" loading some plug-ins during system startup. I'm not using modem, so I'm wondering is it safe to remove "modem-manager" via Synaptic?

Also, I'm interested in your suggestions in terms of system optimization. :)

Well as you would already see, Ubuntu is faster compared to Windows so you wouldn't have to speed it up as unlike Windows where it slows down over time; Ubuntu will not.

_Product to leave well alone:_ **Computer Janitor**

Reason I say this is because the name of the program is misleading, it will not only get rid of non-essential software but it will eradicate other things that you will need.

If you don't use games, then you can get rid of those via the Synaptic Package Manager.

Install Bleachbit via the Synaptic Manager, this will help rid some of the crap you accumulate as you surf the web, but be careful as it also can remove your passwords and cookies; so have a good look first and make sure you know what you want to keep and what you wish to get rid of.

I'd also suggest that you install Ubuntu Tweak, which in my opinion should come as standard with Ubuntu, filled with all sorts of software that you may use: [[COLOR="Red"]**Ubuntu Tweak**[/COLOR]]("http://ubuntu-tweak.com/")

---

### Post by endotherm on 2010-07-21
my best advice is not to deviate too far from the defaults in terms of desktop integrated packages, until you are very familliar with ubuntu. those that are not familliar with the repo system don't often realize that uninstalling one desktop package could remove the desktop completely (never uninstall python...) .

if you don't want to see the app in your menus, I would just hide it there. unlike windows, having a huge number of pointless task tray icons isn't a significant source of slowness.

---

### Post by ajgreeny on 2010-07-21
In Windows, every time you install anything, a lot of additional lines of information are added to the registry file which can end up as a huge, monolithic lump, the searching of which can slow down the system very badly.  Linux does not suffer in the same way as it has no registry, putting application configuration in your home folder, mainly, so in all honesty there is no real need to remove any packages in the hope that your system will become faster, because it will not.

You can remove some of the applications in Startup Applications, by all means, but be careful what you take from there, and add then back again if you find something useful missing in the system workings.

---

### Post by Muscovy on 2010-07-21
I would uninstall the Movie Player and install VLC. VLC can play music and movies, and has a much more compact window.

---

### Post by endotherm on 2010-07-21
> **Muscovy said:**
> I would uninstall the Movie Player and install VLC. VLC can play music and movies, and has a much more compact window.
see, I use a number of media players as some do some things better. vlc will play almost anything but the quality is low. totem is the best integrated but has trouble with 1080p over the network, and langague/subtiutle track issues on some files. mplayer is the best running backend wiht the best codec integration, but has a terrible interface. smplayer is my fav, as it has most of the benifets of mplayer, but lacks the integration totem has.

---

