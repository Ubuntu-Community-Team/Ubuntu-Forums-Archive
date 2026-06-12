---
title: "Flash 10 &amp; Firefox 3.6.12"
date: 2010-12-06
forum: General Help
---

### Post by steveredshaw on 2010-12-06
:eek:

there seems to be several references to problems with Flash on the forum, but I can't find a specific thread about this;

Ubuntu 10.10 - Flash 10 plugin - Firefox 3.6.12 (all latest versions of their kind)

when I try to play programmes from BBC iPlayer website, the message on the screen informs me that I don't have the correct Flash plug-in, I follow the links to download this, but of course my computer does have Flash 10 plug-in already installed

I have tried removing this and reinstalling both from the website link and from Ubuntu repository, but still cannot convince Firefox that I do indeed have the necessary Flash plug-in

where can I go from here? thanks...

---

### Post by tredegar on 2010-12-06
BBC iPlayer works fine for me with:
Ubuntu 10.04LTS (Lucid)
FF 3.6.12
**about:plugins** in FF tells me "Flash 10.1r102" is being used.

---

### Post by Thras0 on 2010-12-06
i had the same problem after installing ubuntu 10.04. here are the steps i took and all work out fine for me :

1. remove any installation of adobe flash

2. remove gnash and swfdec from synaptic package manager (from all the threads i read these two players don't go well with adobe flash for some reason)

3. install flashplugin-nonfree - again from synaptic

4. install adobe flash - from synaptic

*i have tried BBC iplayer on both firefox and chrome and it works

*hope you find this info helpful

**NOTE :  i do not take credit for this, since its a collection of info i took from many threads

---

### Post by steveredshaw on 2010-12-07
;)

thanks Thras0, that did it - I thought it strange because BBCiPlayer was working a little while ago, but then I installed some other plugins to view content on some webpage I was looking at - it must have been then that Flash got knocked off its perch

---

### Post by Thras0 on 2010-12-08
glad everything works fine now

---

