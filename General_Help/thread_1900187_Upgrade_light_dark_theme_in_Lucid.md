---
title: "Upgrade light dark theme in Lucid?"
date: 2011-12-25
forum: General Help
---

### Post by yertalert on 2011-12-25
I'm on lucid, but I much prefer the default light/dark themes for the later releases.

I found some dead links to .debs and the updated themes. As well as a "dead" ppa.

I'm found this question asked quite a few times, but I can't find an up to date answer, it's just a lot of painful work looking through dozens of threads that are full of dead ends.

So my question is, how can I download the new Ambiance/Radiance themes for lucid?

---

### Post by Frogs Hair on 2011-12-25
The Ambiance and Radiance themes are part of light themes package . The  themes for all versions are at the link , but be sure to download the correct theme engines if needed . The 11.10 and 12.04 versions are GTK 3 but you should be able to use the 10.10 or 11.04 versions . [http://packages.ubuntu.com/natty/light-themes](http://packages.ubuntu.com/natty/light-themes)

---

### Post by yertalert on 2011-12-25
I downloaded it, opened it and it said it requires gconf2, so then I went down dependency hell until I got "Error: Breaks existing package 'gconf-defaults-service' dependency gconf2-common (< 2.29)" at the bottom of the can of woims...

Not sure where to go from here? I guess I could find what the alternative packages names would be (if any) then modify the .deb... But I seems unnecessary and I think I went down the wrong road anyway?

---

### Post by hhh on 2011-12-25
[http://packages.ubuntu.com/lucid/light-themes](http://packages.ubuntu.com/lucid/light-themes)

I wouldn't think you actually have to install it, just download the deb, extract it, navigate to /usr/share/themes and move the two folders to .themes in your home folder (create .themes if you don't have it).

---

### Post by yertalert on 2011-12-25
Finally got it working! Now I've got the best of both worlds, a beautiful theme and a mature, advanced OS.

But, you can't just drop those themes in from that .deb, you have to update the murrine theme engine. I figured this out from here: [http://ubuntuforums.org/showthread.php?t=1785600](http://ubuntuforums.org/showthread.php?t=1785600) I'm not sure the ppa the guy provided is still 100% there, with my extremely shotty research I think this one is the same? [http://www.ubuntuupdates.org/ppa/murrine_daily?dist=lucid](http://www.ubuntuupdates.org/ppa/murrine_daily?dist=lucid) If so, then they deleted the most recent version for some reason? Either way, the guy provided the .debs and I just installed them without a hitch.

Where would the ppa for murrine (lucid) be? Or was that all there was?

---

