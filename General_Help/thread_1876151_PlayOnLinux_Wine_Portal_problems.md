---
title: "PlayOnLinux Wine Portal problems"
date: 2011-11-05
forum: General Help
---

### Post by eboyle12 on 2011-11-05
I just downloaded playonlinux and have been trying to run portal.  It works and i can play but my video is horrendous.  When i walk and move the mouse the screen splits and portions flash different colors while other show the actual portal gameplay.  Any advice on how to get this working correctly?

---

### Post by flipper T on 2011-11-05
have you installed the driver for your graphics card?

---

### Post by llamabr on 2011-11-05
What's portal?  And why are you playing videos in a windows environment inside of linux?  Doesn't linux include video players natively?

---

### Post by llamabr on 2011-11-05
Ha, portal is pretty fun.  And, of course, there's no reason to run it inside of wine.  As you'll come to learn, nearly everything you used to like to do with your windows box you can do natively in linux.  You'll also learn that wine usually sucks, and is a poor substitute for whatever you're trying to do.

---

### Post by eboyle12 on 2011-11-05
My graphics driver is installed.  Playonlinux says that there is an update available but i have no way to update it sudo apt-get update doesnt do anything

---

### Post by eboyle12 on 2011-11-05
I've been missing my steam games so installed play on linux.  Is there a linux bases steam alternative i can use instead?

---

### Post by eboyle12 on 2011-11-05
I have portal on my steam account. I've been trying to play it with playonlinux and wine.  I can get it running but its slow and the graphics are so choppy its unplayable.  Is there an alternative to wine that i can use to run steam or play portal

---

### Post by llamabr on 2011-11-05
Best not to start new threads for the same question, as it just mixes things up, clogs the forums, and risks you missing solutions, and causes us to act redundantly.  Try:

[http://portal.wecreatestuff.com/](http://portal.wecreatestuff.com/)

And please give up on wine.  It's almost never the appropriate solution.

---

### Post by lovinglinux on 2011-11-05
> **eboyle12 said:**
> I've been missing my steam games so installed play on linux.  Is there a linux bases steam alternative i can use instead?

There is a promising alternative under development, that will run natively. However, it is for indie games and  I doubt Portal will be included. Search for *Desura* in the forums. Keep in mind  they didn't release a beta version publicly yet. You need to subscribe to get an invite. I haven't received mine yet.

Anyway, Steam is running weird here as well. I guess we need to wait for updates with fixes. But there are some things you can try. For instance, try logging into Ubuntu with Unity 2D instead of 3D. Games play better on it for me. Another option, is to tweak Compiz settings. To do that see [http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

Another option is to install an older video driver, if you are using nVidia  card. For me version 173 works better than new ones. However I have received a complain from an user that version 173 made things a lot worse. Perhaps is because my card is old (7300GT).

Anyway, whichever method you choose, don't forget to set dxlevel for each game. See [http://ubuntuforums.org/showpost.php?p=11359133&postcount=3](http://ubuntuforums.org/showpost.php?p=11359133&postcount=3)

---

