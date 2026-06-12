---
title: "Firefox 3.5 and Flash"
date: 2009-08-07
forum: General Help
---

### Post by SpitfireSMS on 2009-08-07
I cannot by any means seem to get flash to work after updating to firefox 3.5 via this guide:
[http://blog.kidkonia.com/2009/07/09/roll-your-own-firefox-35-package/](http://blog.kidkonia.com/2009/07/09/roll-your-own-firefox-35-package/)

I would like at all costs to stay with 3.5, because it uses way less RAM on my system than 3.0 did, so I only want that to be a last resort.

I have apt-get updated and apt-get upgraded, which told me in the output that it was uninstalled and reinstalling the newest flash plugin, but it still didnt work on restart.

From the flash player website, i cannot find anywhere to get the amd64 version of the plugin.

So I got the i386 verion, and tried "sudo dpkg -i --force-architecture install_flash_player_10_linux.deb", and that told me there was dependency issues.

I also tried installing via synaptic. The install went fine, no errors, but still no flash.

Someone please help!

---

### Post by Bigtime_Scrub on 2009-08-08
Check out the link here [http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490")

It includes scripts for 64-bit flash and Java. It worked well for me. It comes with a how to on the link.

---

### Post by Loosewheel on 2009-08-08
Is 'Shockwave Flash' enabled under 'Tools>Add-ons'?
I run AMD 64, and version 10.2 r22 Flash, which I installed via Firefox 3.5 add-ons.
I have no problems.

---

### Post by SpitfireSMS on 2009-08-08
@Big:
Didnt work either :(

Everything installed fine without error, but no flash still.


@Loose:
The only plugin on the list is default plugin.
Nothing for flash or shockwave

---

### Post by Loosewheel on 2009-08-08
Try,  Synaptic>flashplugin-installer

---

### Post by SpitfireSMS on 2009-08-08
Already did, didnt work.

Im thinking that apt doesnt know that i installed the newer firefox, and I have been updating and installing flash over and over again on my older(partially non-existant) firefox 3.0 install.

How would I discern whether this is taking place?

---

### Post by Loosewheel on 2009-08-08
Spitfire,
I don't know, but 'man apt-get' might get you there.

---

### Post by speedwell68 on 2009-08-08
Try...

```
sudo apt-get install flash-plugin-nonfree
```

---

### Post by SpitfireSMS on 2009-08-08
Iv already tried that package through synaptic, and it didnt work.

I guess Ill just continue using 3.0.x

How do I downgrade it?

Synaptic seems to think I have 3.0.12 installed, im really not sure whats going on.

How do I go about completely removing the installation, preferably without losing my profile?



EDIT
/
Forget that last question, I was able to do everything with synaptic and apt

---

### Post by Mayfairy on 2009-08-13
I got the same thing happening here. 

Flash works on my old 3.0 Firefox but not with 3.5.
Few days ago I managed to make flash work but Youtube videos and such would instantly crash my browser. Fiddled around a bit and now everything that's supposed to have flash in it shows only blank.

---

