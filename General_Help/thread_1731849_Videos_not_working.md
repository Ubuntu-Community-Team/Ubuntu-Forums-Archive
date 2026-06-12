---
title: "Videos not working"
date: 2011-04-17
forum: General Help
---

### Post by THR33 on 2011-04-17
Absolute beginner talk.



I can't watch any videos outside of Youtube (Though it lags and jumps if I even move my mouse on youtube). 

For example at [http://www.bbc.co.uk/news/world-us-canada-13052948](http://www.bbc.co.uk/news/world-us-canada-13052948)

the message I  get below the video is

> 
**Cannot play media.**You do not have the correct version of the flash player.  [Download the correct version]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")
I am pretty sure I have downloaded and installed the correct version several times, yet I still cannot play the damn video.

---

### Post by sanderj on 2011-04-17
Which browser do you use?

In the browser's addres bar, type "about:plugins", and in the resulting screen, look up "Shockwave Flash": what does it say. Mine says:

Flash - Version: 10.2.153
Shockwave Flash 10.2 r153

BTW: in my experience, it's best to only install via the Ubuntu Software Center, not via other, direct links on webpages.

---

### Post by THR33 on 2011-04-17
> **sanderj said:**
> Which browser do you use?

In the browser's addres bar, type "about:plugins", and in the resulting screen, look up "Shockwave Flash": what does it say. Mine says:

Flash - Version: 10.2.153
Shockwave Flash 10.2 r153

BTW: in my experience, it's best to only install via the Ubuntu Software Center, not via other, direct links on webpages.
Firefox 4.0


**Shockwave Flash**

 File:  libgnashplugin.soVersion:   Shockwave Flash 10.1 r999.
Gnash 0.8.8, the GNU SWF Player.   Copyright (C) 2006, 2007, 2008, 2009, 2010   [Free   Software Foundation]("http://www.fsf.org/"), Inc. 
   Gnash comes with NO WARRANTY, to the extent permitted by law.   You  may redistribute copies of Gnash under the terms of the   [GNU General Public   License]("http://www.gnu.org/licenses/gpl.html"). For more information about Gnash, see [   http://www.gnu.org/software/gnash]("http://www.gnu.org/software/gnash/").   
  Compatible Shockwave Flash 10.1 r999.

---

### Post by Dutch70 on 2011-04-17
Hi and welcome to UF

Have you installed the ubuntu-restricted-extras? If not, either go to software center and install it. Or run this command in a terminal.
```
sudo apt-get install ubuntu-restricted-extras
```
And try them again.

---

### Post by THR33 on 2011-04-17
> **Dutch70 said:**
> Hi and welcome to UF

Have you installed the ubuntu-restricted-extras? If not, either go to software center and install it. Or run this command in a terminal.
```
sudo apt-get install ubuntu-restricted-extras
```And try them again.
Ran that command. Waited for it to download and install. Videos still not working.

---

### Post by Dutch70 on 2011-04-17
Try updating your system now that it's installed
```
sudo apt-get update && sudo apt-get upgrade
```
and also restart firefox. 

You may also want to try [[COLOR="RoyalBlue"]Flash Aid[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")
That's all I got.

---

### Post by THR33 on 2011-04-17
> **Dutch70 said:**
> Try updating your system now that it's installed
```
sudo apt-get update && sudo apt-get upgrade
```and also restart firefox. 

You may also want to try [[COLOR=RoyalBlue]Flash Aid[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")
That's all I got.
Yeah, still not working. :(

---

### Post by themusicalduck on 2011-04-17
Open Synaptic package manager under System > Administration.

Search for gnash and uninstall anything relating to it. Then if you have the restricted extras installed, it should start using flash instead of gnash.

If flash still doesn't work after doing that, try installing package flashplugin-installer.

---

### Post by THR33 on 2011-04-17
> **themusicalduck said:**
> Open Synaptic package manager under System > Administration.

Search for gnash and uninstall anything relating to it. Then if you have the restricted extras installed, it should start using flash instead of gnash.

If flash still doesn't work after doing that, try installing package flashplugin-installer.
Uninstalling gnash seems to have fixed it. Thanks. :)

---

