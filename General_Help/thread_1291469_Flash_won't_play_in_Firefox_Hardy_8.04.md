---
title: "Flash won't play in Firefox Hardy 8.04"
date: 2009-10-14
forum: General Help
---

### Post by charonred on 2009-10-14
I'm using Hardy 8.04.3
I've removed all packages I could find for Flash in Synaptic and added the restricted extras via apt-get, but I still can't get Flash to play in Firefox 3.0.14 - keep getting message I need to download latest player, but after downloading the  relevant .deb, it won't install cause I already have a later version ?

---

### Post by lastoneleft07 on 2009-10-14
did yo utry uninstalling plugin or unisntalling firefox itself?

---

### Post by charonred on 2009-10-14
uninstalling plugins via synaptic

---

### Post by charonred on 2009-10-14
I removed everything I could find related to Flash in Synaptic, went back to terminal and ran ```
sudo apt-get install ubuntu-restricted-extras
``` again and was prompted to autoremove a couple of libraries - did that and it still wouldn't work.

So went to Adobe site and downloaded .deb for 8.04 and when I ran the installer, it advised a later version was available from Ubuntu's software channel, but I ignored that, and installed the one I downloaded from Adobe.

Flash finally works !

---

### Post by Johnny B on 2009-10-14
to remove all flash/plugins
> sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

---

### Post by charonred on 2009-10-14
thanks for that script; I've saved it to my Linux fixes folder for future reference.

I've converted 6 friends to Ubuntu in the past year, so short term, I get their pleas for help, and my fixes folder is quick problem sorter (I'm even starting to remember some of them).

---

### Post by tuxxy on 2009-10-14
I'm not sure which you have installed now but you should try the 64-bit Adobe Flash plugin its much better than the one provided in the repos.  Its available here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) simply extract to /usr/lib/mozilla/plugins and restart firefox :D

---

### Post by charonred on 2009-10-14
I'm still using 32 bit 8.04.3 as my main OS at the moment, so would flash 64 bit work?

I plan on going 64 bit next month for my OS anyhow; I'm just waiting for 9.10 (64 bit) to be released at end of month, and will compare with 8.04 (64 bit) I have installed on another drive.

---

### Post by tuxxy on 2009-10-14
oh sorry I must have misread with another thread.  No you stick with 32-bit bud hehehe :D

---

### Post by charonred on 2009-10-14
no probs, but I'll try it when I do the 64 bit OS :)

---

### Post by tuxxy on 2009-10-14
Good stuff bud, I'm sure you will love 64-bit! nice systems btw  :D

---

