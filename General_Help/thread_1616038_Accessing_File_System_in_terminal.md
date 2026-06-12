---
title: "Accessing File System in terminal??"
date: 2010-11-07
forum: General Help
---

### Post by 3nriched on 2010-11-07
hey, i just installed ubuntu on my old dell inspiron 4000 laptop. I have a problem with my screen though thats making ubuntu split in half makign it nearly impossible to use..

i found the possible solution at [http://ubuntuforums.org/showthread.php?t=187687](http://ubuntuforums.org/showthread.php?t=187687)
but im havin g trouble accessing File System where the document i need is located

The solution states to open etc/X11 then to do some other line and change something in a text but i have no idea how to access File System using terminal????

---

### Post by Karakh on 2010-11-07
Once the machine boots and you see your garbled display, press "ctrl+alt+F1".

It should allow you to login and edit etc/X11 from there.

If it wont work. You can use a live-CD, mount your HDD and edit it from there.

---

### Post by 3nriched on 2010-11-07
nice, that helps the visual aspect, now i just gotta try to figure out this etc/x11 thing
thanks

---

### Post by Karakh on 2010-11-07
Glad to help. 

Just be sure that you backup X11 before editing. I've lost count of how many times I've fubard X11.

---

### Post by 3nriched on 2010-11-07
k so now i can use the terminal without half the screen,

now my problem is that in the posting [http://ubuntuforums.org/showthread.php?t=187687](http://ubuntuforums.org/showthread.php?t=187687)
it states a fix to the split screen, but it tells me to su lkjhjh xorg.conf but it wont find it using terminal. yet when i search for it with the half screen desktop (non terminal) the file shows, I also tried just opening that file to make the changes but the file dosnt contain the same information as stated...

basically my ubuntu is broken unless anyone knows how to fix the half screen bug...

---

### Post by Karakh on 2010-11-07
If you're trying to edit the xorg.conf, use this command:

```
sudo nano /etc/X11/xorg.conf
```


EDIT: found this: [http://ubuntuforums.org/showthread.php?t=1267299](http://ubuntuforums.org/showthread.php?t=1267299)
      which led me to this: [http://ubuntuforums.org/archive/index.php/t-772462.html](http://ubuntuforums.org/archive/index.php/t-772462.html)

EDIT AGAIN: Someone with the same problem said that this worked: [http://www.allquests.com/question/3471480/](http://www.allquests.com/question/3471480/)[ubuntu]-HOW-TO-Fix-video-problem-on-Dell-Latitude-C600-C500.html

---

