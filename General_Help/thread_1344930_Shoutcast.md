---
title: "Shoutcast"
date: 2009-12-03
forum: General Help
---

### Post by dln9 on 2009-12-03
I am running Ubuntu 9.10.  

How do I play a Shoutcast station from the Shoutcast web site using the Shoutcast player?  When I click on the "Tune In" button, it behaves as if something is happening, but I hear nothing.  

Related question:  How do I play a Shoutcast station using Rhythmbox?  When I select the option to play using my own player, that doesn't work either.  

Thanks.

---

### Post by claracc on 2009-12-03
There is a radio browser plugin for rhythmbox which allows you to play shoutcast radio directly from it. The plugin can be installed from [http://live.gnome.org/RhythmboxPlugins/ThirdParty](http://live.gnome.org/RhythmboxPlugins/ThirdParty)

---

### Post by dln9 on 2009-12-03
Say, that's pretty nifty - thainks!  

You know, I'm really liking the creativity and diversity of "stuff" available in the Linux world.  I'm starting to think Linux beats the snot out of Microsoft.  

What about my other question:  Why can't I hear anything when I attempt to play something directly on Shoutcast's web site?

---

### Post by totheleft on 2009-12-03
i just tried it and it worked for me, have you installed the restricted extras package as theres no mp3 codec installed by default.

---

### Post by dln9 on 2009-12-04
I'm sorry - I don't know what the "restricted extras package" is.  Will I find that in Synaptic?  Is it a single "thing" called exactly that - "Restricted Extras Package"?  Do I need to add a special repository to obtain it?

---

### Post by KeLa on 2009-12-04
Start ubuntu software center and type restricted to search field and there you have it

---

### Post by dln9 on 2009-12-04
Thank you.  

It turned out I already had the restricted stuff installed.  

Possibly other ideas why the Shoutcast site won't work for me?

---

### Post by claracc on 2009-12-05
> There is a radio browser plugin for rhythmbox which allows you to play shoutcast radio directly from it. The plugin can be installed from [http://live.gnome.org/RhythmboxPlugins/ThirdParty](http://live.gnome.org/RhythmboxPlugins/ThirdParty)

If you have installed this plugin in rhythmbox and configure it, now run rhythmbox, in the left panel it appears an icon with the name Radio browser, you click on it and in the right panel it appears various options, select shoutcast (in the end), select one of the categories (double click) 24h for example, and appears the fisrt choice blauFM, double click or right click on it and select play. This is what works for me.

The http you have to insert to play this radiostation is  [http://85.25.71.198:13280](http://85.25.71.198:13280) (no the url oh the station homepage), which is the url of the stream. If it doesn't work, perhaps you don't have the suitable codec or pulseaudio is not correctly configured.

Regards

---

