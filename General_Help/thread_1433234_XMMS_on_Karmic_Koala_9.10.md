---
title: "XMMS on Karmic Koala 9.10 ?"
date: 2010-03-18
forum: General Help
---

### Post by WarrenSH on 2010-03-18
[FONT=Comic Sans MS][SIZE=2][COLOR=Black]I see that there is  a source list for* ubuntu 9.04.*[/COLOR][/SIZE][/FONT]  [FONT=Comic Sans MS][SIZE=2][COLOR=Black]deb http:[COLOR=#000000]**//**[/COLOR]www.pvv.ntnu.no[COLOR=#000000]**/**[/COLOR]~knuta[COLOR=#000000]**/**[/COLOR]xmms[COLOR=#000000]**/**[/COLOR]jaunty .[COLOR=#000000]**/**[/COLOR]
deb-src http:[COLOR=#000000]**//**[/COLOR]www.pvv.ntnu.no[COLOR=#000000]**/**[/COLOR]~knuta[COLOR=#000000]**/**[/COLOR]xmms[COLOR=#000000]**/**[/COLOR]jaunty .[COLOR=#000000]**/**[/COLOR][/COLOR][/SIZE][/FONT]

[FONT=Comic Sans MS][SIZE=2][COLOR=Black]
But is there away to get this running on Karmic Koala 9.10 with out having errors?

Can I add this list to my source.list & then install like this with out having any problems? 

[/COLOR][/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]**gedit [COLOR=#000000][B]/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]apt[COLOR=#000000]**/**[/COLOR]sources.list[/B]

(add these 2 lines in my source list & save)
[B]
deb http:[COLOR=#000000]**//**[/COLOR]www.pvv.ntnu.no[COLOR=#000000]**/**[/COLOR]~knuta[COLOR=#000000]**/**[/COLOR]xmms[COLOR=#000000]**/**[/COLOR]jaunty .[COLOR=#000000]**/**[/COLOR]
deb-src http:[COLOR=#000000]**//**[/COLOR]www.pvv.ntnu.no[COLOR=#000000]**/**[/COLOR]~knuta[COLOR=#000000]**/**[/COLOR]xmms[COLOR=#000000]**/**[/COLOR]jaunty .[COLOR=#000000]**/**[/COLOR][/B]
[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2][COLOR=Black]
Then to install I would do this.

**sudo apt-get **[/COLOR][/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]**update**
[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=2]**sudo apt-get install xmms**[/SIZE][/FONT]




[FONT=Comic Sans MS][SIZE=2]Feedback is highly welcome I would like to know if anyone is running XMMS on Karmic Koala *9.10*
[/SIZE][/FONT]

---

### Post by zvacet on 2010-03-18
I think you will find solution [here.]("http://ubuntuforums.org/showthread.php?t=1312757&page=2")

---

### Post by WarrenSH on 2010-03-18
> **zvacet said:**
> I think you will find solution [here.]("http://ubuntuforums.org/showthread.php?t=1312757&page=2")


I got errors when installing :( 
```

E: Unable to find a source package for libglib1.2-dev
```

---

