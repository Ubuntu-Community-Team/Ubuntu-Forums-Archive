---
title: "Installing Wine"
date: 2006-05-14
forum: General Help
---

### Post by johnno56 on 2006-05-14
I'm wondering how to install Wine. Would I have to have both Windblows and Linux installed?

Can I install Wine onto a "Linux only" machine? If so, how?

I am relatively new to Linux and would appreciate any responses to be kept fairly simple.

Regards

J

---

### Post by meng on 2006-05-14
You don't need Windows, wine does it all. Having said that, wine is imperfect, so doen't expect 100% compatibility. For this reason, some folks run two machines or else dual boot. Go to [www.winehq.com](www.winehq.com) for more information on installing/downloading.

---

### Post by darknightuk on 2006-05-14
you can install it by adding the lines below to your sources list presuming you haven't already?
you can also use wine tools to make the set-up easier, i believe you have to install this thru console but im sure we can help you with that!

## Wine latest
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by johnno56 on 2006-05-15
Thankyou guys.

I have successfully installed Wine, on a "Linux only" box, and it works fine.

Two things:

a) I do not know how to "add to the source list"
b) Activex. From other threads I am lead to believe that activex is "Windblows only". If so, is there a work-around?

Again thankyou for you help.

Regards

J

---

### Post by meng on 2006-05-15
[QUOTE=johnno56]Thankyou guys.

I have successfully installed Wine, on a "Linux only" box, and it works fine.

Two things:

a) I do not know how to "add to the source list"
b) Activex. From other threads I am lead to believe that activex is "Windblows only". If so, is there a work-around?

Again thankyou for you help.

Regards

J[/QUOTE]

If you use the GUI (synaptic), then go to menu option Repositories and then Add custom repositories. Otherwise you can change the /etc/apt/sources.list to include the extra repositories (by the way, apparently the ones quoted by darknight are out of date, see [http://www.ubuntuforums.org/showthread.php?t=172648](http://www.ubuntuforums.org/showthread.php?t=172648)) and then sudo apt-get update.

---

### Post by JimS on 2006-05-15
...
For some info on Wine and WineTools see

[http://www.ubuntuforums.org/showthread.php?t=103117&highlight=winetools](http://www.ubuntuforums.org/showthread.php?t=103117&highlight=winetools)

Ubuntu Forum's "Search" may also yield good results.

[COLOR="Red"]JimS[/COLOR]
[COLOR="Blue"]Prostate Cancer Aware[/COLOR]

,,,

---

