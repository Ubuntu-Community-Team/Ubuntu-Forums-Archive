---
title: "wine and ie"
date: 2006-02-15
forum: General Help
---

### Post by nanotube on 2006-02-15
hey
so... i have a winxp partition, ntfs, mounted readonly.
i wonder, if i install wine, would it be possible to just run the iexplore.exe that is located on the readonly ntfs partition, and if so, how?

if not, then what's the best way to get an IE going under ubuntu? preferably with proper security, and chrooting, and all the good stuff to make sure it doesnt screw anything up? :)

some websites i need to use just really require ie, no getting around it... very unfortunate.

would appreciate some help on this one. :)

---

### Post by Qrk on 2006-02-15
IE works very well in wine. (or at least as well as IE can work)

You can install it through in winetools which automates much of wine's setup. It also runs from an ntfs partition; but possibly not as well. 

The installation process requires going to microsoft's website and downloading the installer, running that in wine, having the installer download IE, and install that.

---

### Post by handy on 2006-02-15
If you do install IE, don't try to install & run DVDshrink, 'cause the IE, under wine, will cause the DVDshrink display to be distorted quite badly.

---

### Post by magomago on 2006-02-15
Lol Random....

---

### Post by gsuveg on 2006-02-15
where is the ie6setup ? I have download one, but it cant look out from my computer to internet :( instane :)

Anyone can help what i wrong ?

---

### Post by dunnerz on 2006-02-15
Try this

[http://tatanka.com.br/ies4linux/](http://tatanka.com.br/ies4linux/)

it works very well for me (I need ie for web development)

---

### Post by nandasunu on 2006-02-15
[QUOTE=dunnerz]Try this

[http://tatanka.com.br/ies4linux/](http://tatanka.com.br/ies4linux/)

it works very well for me (I need ie for web development)[/QUOTE]

ditto that. 

I found with this script it works best if you install one version at a time (if you need multiple versions). I couldn't get ie6 to install when doing them all at once.

---

### Post by kenweill on 2006-02-15
[QUOTE=gsuveg]where is the ie6setup ? I have download one, but it cant look out from my computer to internet :( instane :)

Anyone can help what i wrong ?[/QUOTE]

Just install WINETOOLS and run it from the terminal.

From there, you can install Internet Explorer 6 SP1. It works on my system, execpt for the Windows Update found in the menu of IE.

---

### Post by gsuveg on 2006-02-15
thanks.

---

### Post by kenweill on 2006-02-15
no probs

---

### Post by Nandro2 on 2006-02-15
Is there a repository with winetools?

---

### Post by nanotube on 2006-02-15
so my question was, is it possible to run the **already installed** ie, that is located in my windows partition, from wine. without running an ie installer and installing a "second copy" of ie under wine?

---

### Post by dcstar on 2006-02-15
[QUOTE=nanotube]so my question was, is it possible to run the **already installed** ie, that is located in my windows partition, from wine. without running an ie installer and installing a "second copy" of ie under wine?[/QUOTE]
Probably not.

Wine requires DLLs and Registry entries in it's own space, it cannot really use the ones in a real Windows installation.

---

### Post by nanotube on 2006-02-15
ok, thanks dcstar. :) guess i will have to play with winetools and friends...

---

### Post by 2tim3_16 on 2006-02-17
I'm trying to install wine on Breezy following the tutorial at [http://www.ubuntuforums.org/showthread.php?t=29996](http://www.ubuntuforums.org/showthread.php?t=29996). I do fine until I get to downloading the winetools. The link given no longer works, and I can't find anything but a German version when I search online. So repeating Nandro2's question, is there a repository with winetools?:confused:

---

### Post by Robor on 2006-02-17
I couldn't find 'winetools' either but then I remembered when I installed Automatix and let it install WINE that it recommended running 'winecfg' after the installer finished working.  If you used Automatix to install WINE try using winecfg and see if you've got it.  If not maybe uninstall WINE, delete the ~/.wine directory, and reinstall WINE through Automatix.  

I got IE6 installed on my system but mostly just to see IE6 & Windows Media Player under Ubuntu.  I still use Firefox as my primary browser.  :)

**NOTE:**  I had to set my IE Internet Security setting to the lowest possible in order for Windows Media Player to download new codecs.  Not sure if there's another or a better way to do it but that worked for me.

---

### Post by dcstar on 2006-02-17
[QUOTE=2tim3_16]I'm trying to install wine on Breezy following the tutorial at [http://www.ubuntuforums.org/showthread.php?t=29996](http://www.ubuntuforums.org/showthread.php?t=29996). I do fine until I get to downloading the winetools. The link given no longer works, and I can't find anything but a German version when I search online. So repeating Nandro2's question, is there a repository with winetools?:confused:[/QUOTE]
Apparently not any more, it has to be downloaded and installed manually.

---

### Post by handy on 2006-02-18
[QUOTE=handy]If you do install IE, don't try to install & run DVDshrink, 'cause the IE, under wine, will cause the DVDshrink display to be distorted quite badly.[/QUOTE]

I used WineTools to install Internet Explorer.

I'm not sure now, but it was probably on their site that I was told that having IE installed actually screws up DVDshrink's display.

I installed it anyway, ('cause I do the occasional web site) & DVDshrink, & guess what?  DVDshrink was basically useless!!

So, I uninstalled Wine completely, (not seeing any other way!) & reinstalled Wine, used WineTools to finish off, due to it's setup advantages, then installed DVDshrink!

Guess what, DVDshrink works as fast as it did in windoze...:KS

I somehow think that M$ had an unintentional victory here... :rolleyes:

I will boot to windoze, the once or twice a year that I use Dreamweaver, np.

**[Edit:]** WineTools here:  **[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)**

---

