---
title: "What is the difference between Totem and Totem-xine?"
date: 2006-06-05
forum: General Help
---

### Post by tommcd on 2006-06-05
Is there any difference between Totem and Totem-xine? Do they support different codecs or different types of multimedia files? Or is it just a different skin for totem?
Also, in the Dapper guide:

[http://doc.gwos.org/index.php/DapperGuide#How_to_install_Multimedia_Codecs](http://doc.gwos.org/index.php/DapperGuide#How_to_install_Multimedia_Codecs)

it says to associate xine to play multimedia files by typing this in terminal:

gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "xine dvd://" sudo rm -f /usr/share/applnk/Multimedia/xine.desktop sudo ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/ sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup sudo sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list sudo mv /tmp/defaults.list /usr/share/applications/defaults.list

Can all that be undone if you want to use a different media player? What does all that do anyway? Any advice appreciated, thanks!!

---

### Post by magnusbb on 2006-06-05
The difference is the enigne used in Totem; in the standard package the gstreamer-0.10 engine will be used, while the xine engine will be used in the other.

I would reccommend you to go with the first one - gstreamer, as it is very impressive in this latest release. It's faster and more reliable than ever.

---

### Post by thasheep on 2006-06-05
Totem can run with two backends, gstreamer or xine. If you use totem-gstreamer, you'll use the gstreamer plugins (codecs) you have installed. If you use totem-xine, you'll use the xine ones. You can swap between the two quite easily.
You could consider totem-xine to be the totem frontend (gui) to xine. Other frontends include xine-ui and kaffeine-xine.
As for setting the default media player, I find it easiest just to right-click on a media file, select properties and under "open with", choose the player. To set the player for inserted dvds, you can use system>preferences>removable drives and media. This can also be done with gconf but is more difficult imo.

---

### Post by tommcd on 2006-06-05
Thanks Magnusbb, in Breezy I used Xine, but the regual Totem does seem better in Dapper. I guess I'll stick with it for now anyway.

---

### Post by tommcd on 2006-06-05
And thanks Thasheep, one question Thasheep:
As for switching between the two, synaptic says they conflict, ie, if you install xine it removes gstreamer plugin and firefox plugin. Is one any better than the other?

---

### Post by thasheep on 2006-06-06
xine is a bit lighter and used to give better performance (at least on my computer) but the 0.10 version of gstreamer in dapper is a big improvement on the 0.8 that was in breezy. I'd probably go for the new gstreamer as that's the 'standard' but by all means, try them both. As you said, installing one removes the other so swapping between them can be done via apt/synaptic.
Personally, I much rather mplayer to totem. The xv video output (select in preferences and then re-open mplayer) gets the video card to do the work rather than the cpu. It produces a smoother picture and the best zoom on my computer. To get the w32codecs package (windows codecs), which allows support for more formats than xine or gstreamer, add this line to /etc/apt/sources.list```
deb http://seveas.theplayboymansion.net/seveas dapper-seveas extras
```There's also mozilla-mplayer, a plugin that embeds videos in firefox.

---

