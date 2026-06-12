---
title: "Why are ALL my Search Daemons (Tracker/Beagle/Find/Locate/etc) Dying? What can I do?"
date: 2010-06-26
forum: General Help
---

### Post by OzzyFrank on 2010-06-26
Hmmm... I thought it was just **Tracker** dying on me, forever trying to index, and at best giving me a fraction of the hits I should have gotten (but in the end, **everything** turned up **zero** results: [http://ubuntuforums.org/showthread.php?t=1506968](http://ubuntuforums.org/showthread.php?t=1506968)) but I've since uninstalled it, and my search woes continue. I reinstalled good old **Beagle**, but I keep getting messages that the search daemon isn't running. Using Beagle's own search tool it apparently gives me the option to restart it, but nothing happens (**beagled** is sleeping in System Monitor, just like **trackerd** was).

But before, even with all this, I could use **Catfish**, even though I prefer my results as thumbnails. While you could get it to use any of the daemons like Beagle, I always just left it on **Find**, which you probably know is a basic Linux command, and no doubt why it (via Catfish) was the only thing that worked.

However, **now even Catfish is returning zero results**, whether I use **[COLOR="DarkRed"]find[/COLOR]**, **[COLOR="DarkRed"]locate[/COLOR]**, **[COLOR="DarkRed"]beagle[/COLOR]** or **[COLOR="DarkRed"]strigi[/COLOR]**.

Can anyone please tell me what on earth is going on here? Why all my options for searching, even Linux commands, are just not happening? Is there some kind of database server or something that they all rely on, and it is broken, causing them to fail?

I've obviously tried copious reboots and manual restarts of the search daemons via terminal, but nothing is working. Also tried KDE programs and file managers, since I have Kubuntu in the same system, but still no go. Any light on this would be greatly appreciated.

---

### Post by philinux on 2010-06-26
Maybe something gone wrong with the auto update of updatedb.

Try running it then do a search.

```
sudo updatedb
```

---

### Post by wilee-nilee on 2010-06-26
> **philinux said:**
> Maybe something gone wrong with the auto update of updatedb.

Try running it then do a search.

```
sudo updatedb
```

I just noticed the new avatar can I call you captain philinux.:p

---

### Post by OzzyFrank on 2010-06-28
Well, not sure if that did anything or not, since this situation is somewhat intermittent. Meaning after a while I'll go to do a search and all of a sudden I'll get results popping up (though in a couple of hours could be back to zero or another error message telling me why it could do a search). So, before running that update command, I did a search again and got some results, though noted files I knew should have been listed still weren't (seemed like those recently saved were listed, but ones with similar names I downloaded earlier weren't). When I ran that command nothing seemed to change, as I got exactly the same (incomplete) results afterwards. There is something definitely messing with my search daemons, like turning them off and/or the indexing. Any more suggestions anyone?

---

