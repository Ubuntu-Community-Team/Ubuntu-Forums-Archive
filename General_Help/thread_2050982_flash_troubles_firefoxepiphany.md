---
title: "flash troubles firefox/epiphany"
date: 2012-09-01
forum: General Help
---

### Post by Bikerman114 on 2012-09-01
I had flash working in ff since I installed Ubuntu yesterday and was only able to get in working in Epiphany this morning from one the the older threads here. Now when I go to Youtube or Hulu it just says that I need flash to watch any video's. This is happening in both Firefox and Epiphany.  
I'm a new Linux user so it might be something simple but I"m kind of lost. I did try downloading the different Linux versions, from the adobe sight, but it isn't fixing anything and idk what to put in the terminal to try it that way.

I actually went back to Windows and the problem isn't happening at all there so idk what it is.


NOTE: This morning, after posting again below updates showed up and now Flash appears to be working fine in Firefox but still isn't working in Epiphany

---

### Post by Bachstelze on 2012-09-01
Normally, you install Flash by installing the package adobe-flashplugin (using whatever method you prefer), and that's all. This works in Firefox, but I don't know about Epiphany...

---

### Post by QIII on 2012-09-01
Could you post the link to the "older thread"?

---

### Post by claracc on 2012-09-01
You have to install flashplugin-installer in order to get adobe flashplayer installed. It works for firefox. [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

For epiphany, you have also to install nspluginwrapper which will install also nspluginviewer ( I recommend to use synaptic manager for all the installations). Then you open a xterm and introduce the following command: nspluginwrapper -v -a -n -i

---

### Post by vasa1 on 2012-09-01
> **claracc said:**
> You have to install flashplugin-installer in order to get adobe flashplayer installed. It works for firefox. [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

For epiphany, you have also to install nspluginwrapper which will install also nspluginviewer ( I recommend to use synaptic manager for all the installations). Then you open a xterm and introduce the following command: nspluginwrapper -v -a -n -i

[Seems to be a gtk2 versus gtk3 thing]("https://bugs.launchpad.net/midori/+bug/974775/comments/1").

---

### Post by vasa1 on 2012-09-01
> **Bikerman114 said:**
> ...  
I'm a new Linux user ...
In which case I feel you're better off with Firefox than with Epiphany (now called "Web").
BTW, are you on 32- or 64-bit?

---

### Post by Bikerman114 on 2012-09-01
I'm using 64 bit Ubuntu 12.04. I have the flashplugin installer installed on my laptop now as well as nspluginwrapper. 

Flash was working in both browsers till I closed it. I have my laptop set to turn off whenever I close it so it doesn't overheat in my back pack. SHould restarted of effected anything?

---

