---
title: "MacOSX theme for KDE?"
date: 2006-02-02
forum: General Help
---

### Post by erick_p on 2006-02-02
Hi, does anyone know if there is a MacOSX theme for KDE? I mean theme-ing everything like file editor, FTp software, browser etc. Thanks!

---

### Post by firetux on 2006-02-02
[http://kde-look.org/](http://kde-look.org/)

---

### Post by erick_p on 2006-02-02
[QUOTE=firetux][http://kde-look.org/](http://kde-look.org/)[/QUOTE]

Thank you but I am not familiar with Linux (yet). A search for macosx there results in some strange things, and icon sets, and such. I read that KDE is a "themable" desktop, so is there like a file that I can download that will make my entire KDE theme like Macosx in one go, instead of separately downloading icon sets, and windowbar, and shadow, and all of it individually?Thanks!

---

### Post by stuporglue on 2006-02-02
I've never used baghira, but it looks a lot like OSX's aqua. 

[http://baghira.sourceforge.net/screenies.php](http://baghira.sourceforge.net/screenies.php)

> Thank you but I am not familiar with Linux (yet). A search for macosx there results in some strange things, and icon sets, and such. I read that KDE is a "themable" desktop, so is there like a file that I can download that will make my entire KDE theme like Macosx in one go, instead of separately downloading icon sets, and windowbar, and shadow, and all of it individually?Thanks!

You have to realize that most Linux users don't work to make their desktops like OSX, so very few people here are going to have experience doing so. Most people will see an icon set they like, grab that, see a wallpaper they like grab that, and so on. 

Anyways, Baghira is the german spelling of Bagheera, which is the jungle cat from the Jungle book, of course. :-) Hope it works, enjoy!

---

### Post by mips on 2006-02-02
[QUOTE=erick_p]Hi, does anyone know if there is a MacOSX theme for KDE? I mean theme-ing everything like file editor, FTp software, browser etc. Thanks![/QUOTE]

I think what you are looking for is Baghira as mentoned in the post above.

---

### Post by [Nirvana] on 2006-02-02
sudo apt-get install kwin-baghira

it's in the universe repo: [http://packages.ubuntu.com/breezy/kde/kwin-baghira](http://packages.ubuntu.com/breezy/kde/kwin-baghira)

---

### Post by analyticalman on 2006-02-03
Then, after installing - try this
[http://linuxgangster.org/modules.php?name=Content&file=viewarticle&id=15](http://linuxgangster.org/modules.php?name=Content&file=viewarticle&id=15)

or this
[http://baghira.sourceforge.net/OS_Clone-en.php](http://baghira.sourceforge.net/OS_Clone-en.php)

---

### Post by erick_p on 2006-02-04
Wow, thanks so much guys! I checked out kde-look.org and their top rated themes are even better than Macosx! I love lipstik and QTCurve. 

My next question-- both KDE and Gnome I tried on my laptop make the text look blurry, maybe blurry is the wrong word, but it has a non-clear look. In KDE, I unchecked some option called 'Enable anti-aliasing of text' so as to disable it and see clear fonts only but that did not do anything! 

So my questions: 

1. In KDE, how easy is it to get clear looks like in this screenshot from KDE-look: [http://snipurl.com/m82l](http://snipurl.com/m82l)    (the KDE look website's URL is very long, and broke this message, so I have snipped it) 

2. I like some fonts that I have on Windows in TTF files and the OTF format from Adobe Fonts. Can I use those font types on Linux?

Many thanks!

---

### Post by analyticalman on 2006-02-04
I'm a bit suspicious that you have the same problem on KDE and Gnome - could it be your laptop screen refresh rate?  I have antialiasing on and have no problem with sharp fonts.

To install extra fonts try this

[http://ubuntuguide.org/#extrafonts](http://ubuntuguide.org/#extrafonts)

---

### Post by erick_p on 2006-02-04
Thanks analyticalman. Explanation: 

1. About sharp text without any shadows and anti-aliasing: 

GNOME: With Ubuntu live CD I think it was gnome that got installed. I could not find the setting to disable antialiasing anywhere, but their default themes had no sharp text. 

KDE: This I tried with CentOS, which I have now uninstalled but I think KDE should be similar in functionality? It was antialiased in every theme I tried! But I did not have QTCurve theme inbuilt so cannot be sure. On KDE-LOOK website that is the only skin I have seen until now that has a sharp fonts look like in Windows. 

2. About installing my own fonts. Thanks for that link, but it shows me how to install prepackaged fonts from APT-GET. I am still not sure how to install my own OTF and TTF files! Can I not simply copy them into some directory? WHy do I need to install and compile and all that jazz?

---

### Post by analyticalman on 2006-02-04
Truetype fonts are stored in /usr/share/fonts/truetype.  Have you tried adding them there?

Have you checked your screen refresh under Linux?

---

### Post by erick_p on 2006-02-04
Wow, thanks for the truetype pointer. That works!

Screen refresh rate is 70. The only options are 60 and 70, so I choose 70. In Windows it is 'Choose optimal rate for monitor'.

---

