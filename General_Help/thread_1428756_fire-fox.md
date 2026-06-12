---
title: "fire-fox"
date: 2010-03-13
forum: General Help
---

### Post by nischalinn on 2010-03-13
I am using fire-fox 3.0.18. I want to **upgrade it to 3.6**.I've downloaded the fire-fox 3.6 file.But how to** install **it?

---

### Post by msidhard on 2010-03-13
i think there is some command like "./configure". just try it 
1.enter the folder where you stored firefox through terminal using cd command eg: "cd /home/desktop/firefox"
2.then type "./configure" 
i think this will work reply if it works

---

### Post by crichard on 2010-03-13
Have a look at this [post]("http://surferzworld.com/?p=193") to install Firefox / Thunderbird in Ubuntu.

Firefox optimization and troubleshooting [thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Uncle Spellbinder on 2010-03-13
@ crichard

Looking at that PPA, it's for 3.5, not 3.6. The others are non-stable builds it seems.

For those wanting the latest, current stable builds of Firefox, Thunderbird or SeaMonkey, use [Ubuntuzilla](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation). 


Works perfectly for my 32 bit install. My Ubuntuzilla repo looks like this:

```
#### Ubuntuzilla
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

Once you're repo is added and sources updated, to install the current stable release of SeaMonkey, Thunderbird or Firefox, use the following in terminal:

sudo apt-get install firefox-mozilla-build
sudo apt-get install thunderbird-mozilla-build
sudo apt-get install seamonkey-mozilla-build

---

### Post by lovinglinux on 2010-03-13
See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

