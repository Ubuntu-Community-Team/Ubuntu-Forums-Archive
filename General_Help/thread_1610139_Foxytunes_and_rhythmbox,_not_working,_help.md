---
title: "Foxytunes and rhythmbox, not working, help"
date: 2010-10-31
forum: General Help
---

### Post by Lancro on 2010-10-31
I install foxytunes, if you look at their supported players page you will see a list of windows players, that we dont care, a list of linux players, and cross platform players...

[http://www.foxytunes.com/firefox/supportedPlayers.html](http://www.foxytunes.com/firefox/supportedPlayers.html)

Ok, I install it, like in windows, pressing install, like all firefox add-ons, It restarts firefox, and I only see the cross plataforms player, no linux player is at the list, and a message in the top of the cross plataforms players "No player modules found, check installation", Im translating spanish to english, so in english it can be something similar.

So how can I fix this, is there anything I  should install so foxytunes works with linux players?, help will be appreciated.

Thanks.

---

### Post by Lancro on 2010-11-01
Anyone?

---

### Post by Swagman on 2010-11-01
Which player did you choose ?

---

### Post by Lancro on 2010-11-01
> **Swagman said:**
> Which player did you choose ?

There are only cross platforms players, as youtube, so I didnt choose anyone, because none of the players it offers is a linux one, It sont shows all linux players, thats the problem.

Thanks.

---

### Post by Lancro on 2010-11-02
Last try, bump.

---

### Post by Flame_Phoenix on 2010-11-21
I have the exact same problem you have. 
I made a search and I found some posts from 2006 and 2007 stating that FoxyTunes is in fact bugged and that it doesn't work for Linux players such as Rhythmbox. 

4 years (almost 5) have past since those posts were made, so I don't know if the problem got solved, however judging by the facts, I think that FoxyTunes project was abandoned and I don't think there is ever going to be a fix for Linux.

Sources:
[http://ubuntuforums.org/showthread.php?t=232083](http://ubuntuforums.org/showthread.php?t=232083)
[http://www.uluga.ubuntuforums.org/showthread.php?p=8558308](http://www.uluga.ubuntuforums.org/showthread.php?p=8558308)
[http://art.ubuntuforums.org/showthread.php?p=8572928](http://art.ubuntuforums.org/showthread.php?p=8572928)

---

### Post by wathompson on 2010-11-29
Running: Ubuntu 10.10, Firefox 3.6.12 (updated from ubuntu repositories), Foxytunes 4.2i

Here is the solution: Foxytunes is dependent on libstdc++5 which you have to get and install  yourself.

All I had to do was open a terminal and type

```
sudo apt-get install libstdc++5
```but you may need to follow some of these threads to get the right repository:

[http://ubuntuforums.org/showthread.php?t=1507043](http://ubuntuforums.org/showthread.php?t=1507043)

[http://ubuntuforums.org/showthread.php?t=1406616](http://ubuntuforums.org/showthread.php?t=1406616)

[http://ubuntuforums.org/showthread.php?t=1395980](http://ubuntuforums.org/showthread.php?t=1395980)

also this made for some interesting related reading:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091)

Hope this helps, installing this library was all I needed to do!


---------------- Now playing: [Trans-Siberian Orchestra - The Prince of Peace]("http://www.foxytunes.com/artist/trans-siberian+orchestra/track/the+prince+of+peace?locale=chrome://global/locale/intl.properties") via [FoxyTunes]("http://www.foxytunes.com/signatunes/")

---

