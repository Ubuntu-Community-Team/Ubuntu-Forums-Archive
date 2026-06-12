---
title: "Old Gnome background appears when coming out of screensaver"
date: 2011-05-25
forum: General Help
---

### Post by iclestu on 2011-05-25
Everytime I unlock my screen in KDE from the screensaver the background for the Gnome interface momentarily appears before the KDE plasma workspace returns.

It only appears for a second and, sure, I can live with it but I wondered if there is a way to fix it and why it is happening in the first place? 

I initially installed ubuntu 10.4 then installed kubuntu through the package manager and have since upgraded to 10.10 and now 11.4. I think this problem has been here since install of kubuntu

---

### Post by ankspo71 on 2011-05-25
Hi,
The only thing I can think of is that there is a Gnome service or application running in the background automatically setting the Gnome wallpaper. Gnome and KDE use different methods to set the wallpaper, so whatever it is setting the Gnome wallpaper is probably setting wallpaper underneath KDE's wallpaper and you only see it when you unlock the desktop. If you use Nautilus (Gnome's file manager) in KDE, I believe it will try to set Gnome's wallpaper.

---

### Post by iclestu on 2011-05-25
Thanks for the reply.

Ooooo - krunner tells me nautilus IS running (scrnshot attached). why would that be? what can i do to fix it? Plasma (the kde equivalent??) is running too. Is this eating up loads of system resource?

---

### Post by iclestu on 2011-05-26
added Nautilus tag and bumped.

Anyone got any ideas here? Might it be as simple to just remove Nautilus? - I never use gnome anymore anyway.

Also - had an afterthought.... I thought it was weird that when the screen was locked and you move the mouse no 'unlock' dialogue box appears. I can still enter my password and it unlocks but no actual box.... Got so used to it that I guess i just forgot about it when posting yesterday but i assume its related?

All help gratefully received! :)

---

### Post by mastablasta on 2011-05-26
you instaleld KDE after GNOME and this duplicated all programmes as well as as these things usually running in background. the option would be to remove the gnome desktop.
have a look here (only this user installed LXDE): [http://ubuntuforums.org/showthread.php?t=1452359](http://ubuntuforums.org/showthread.php?t=1452359)
 
otherwise you will have too many things duplicated.
 
it's kind of stupid actually since if you choose to run KDE then it should only load KDE stuff but i guess it also loads all the GNOME stuff as well while it's already loading...

---

### Post by iclestu on 2011-05-26
Thanks for your reply MastaBlasta but unfortunately that big command didn't do the trick:

I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'compiz-wrapper' can't be removed
Virtual packages like 'devicekit-power' can't be removed
Note, selecting 'empathy-common' instead of 'empathy-doc'
Note, selecting 'evolution-common' instead of 'evolution-documentation-en'
Virtual packages like 'gnometris' can't be removed
Virtual packages like 'libcouchdb-glib-1.0-1' can't be removed
Virtual packages like 'libdbusmenu-glib0' can't be removed
Note, selecting 'empathy-common' instead of 'libempathy-common'
Note, selecting 'empathy-common' instead of 'libempathy-gtk-common'
Virtual packages like 'libesd-alsa0' can't be removed
Virtual packages like 'libgmime2.2a-cil' can't be removed
Virtual packages like 'libmetacity0' can't be removed
Virtual packages like 'libtotem-plparser12' can't be removed
Virtual packages like 'libwebkit-1.0-common' can't be removed
Note, selecting 'pulseaudio' instead of 'pulseaudio-module-udev'
Virtual packages like 'python-sexy' can't be removed
Virtual packages like 'same-gnome' can't be removed
Virtual packages like 'xulrunner-1.9.1' can't be removed
E: Unable to locate package firefox-3.5
E: Couldn't find any package by regex 'firefox-3.5'
E: Unable to locate package firefox-3.5-branding
E: Couldn't find any package by regex 'firefox-3.5-branding'
E: Unable to locate package firefox-3.5-gnome-support
E: Couldn't find any package by regex 'firefox-3.5-gnome-support'
E: Unable to locate package gnome-blackjack
E: Unable to locate package libcdio7
E: Unable to locate package libdbusmenu-gtk0
E: Unable to locate package libempathy-gtk28
E: Unable to locate package libempathy30
E: Unable to locate package libevdocument1
E: Unable to locate package libevview1
E: Unable to locate package libgdata5
E: Unable to locate package libgnome-desktop-2-11
E: Unable to locate package libgnomekbdui4
E: Unable to locate package libgssdp-1.0-1
E: Couldn't find any package by regex 'libgssdp-1.0-1'
E: Unable to locate package libgupnp-1.0-2
E: Couldn't find any package by regex 'libgupnp-1.0-2'
E: Unable to locate package libindicate-gtk1
E: Unable to locate package libkpathsea4
E: Unable to locate package libprotobuf3
E: Unable to locate package libtrackerclient0
E: Unable to locate package openoffice.org-style-human
E: Couldn't find any package by regex 'openoffice.org-style-human'
E: Unable to locate package xulrunner-1.9.1-gnome-support
E: Couldn't find any package by regex 'xulrunner-1.9.1-gnome-support'
```

and Nautilus is still running and I still get the original issue.

---

### Post by iclestu on 2011-05-26
hmmm - did some googling and found this:
[URL="http://www.psychocats.net/ubuntu/purekde"]
http://www.psychocats.net/ubuntu/purekde[/URL]

Im nervous of trying it tho because, essentially, there is nothing wrong with my system now, its just a bit untidy...

Perhaps I will try it on my netbook 1st (which has went through a similar installation/upgrade route) and see how it goes. Can always do a fresh install on that if needs be....

Thanks for your input guys, will post results here in case its of use to someone else....

---

### Post by iclestu on 2011-05-26
uuurrrm - its unintalled texlive and kile - not sure why? No mention of them on original command!

No matter, i suppose I can always re-install. Hope my settings remain.....

Hmmm - seemed to work flawlessly other than that (TOUCH WOOD)... May give it a bash on desktop computer after all

---

### Post by iclestu on 2011-05-26
AAARRRGH.

Works for netbook but have lost my desktop system! Cannot boot into it.

Goes to Kubuntu splashscreen then screen goes blank. Can get to 'recovery' and tried repairing proken packages and fsck but nothing! 

Please help!

---

