---
title: "Really strange things started happening this morning"
date: 2010-02-26
forum: General Help
---

### Post by Carlo1973 on 2010-02-26
Hey all I've got a really REALLY bizzare issue. Last night everything was working fine. I shut down my computer after I was done what I needed to do like I do every other night. This morning I boot up, and in Gnome all the titlebars are missing from every program. I also can't change the dimensions of the windows for each of the programs that open up. Another thing I noticed is that my workspace was 2 yesterday, and only 1 today

I had installed KDE as a backup just incase something should happen to gnome. Those same issues are not present in KDE at all. However, in KDE I'm getting massive artifacting when I change windows. It actually looks like an issue caused by Beryl/Compiz. As its only happening when it does those fancy animations. Also at random points it looks like it's caused by SLI freaking out (Like its trying to flip between the cards, but I'm only getting half the screen showing durring the freak out, lots of flashing, etc) . I had everything configured and working properly for the last 2 or 3 weeks, not sure why it chose now to freak out lol Was there any updates that could have caused this?

Thanks in advance

Carlo

---

### Post by skymera on 2010-02-26
Sounds like GTK-Window-Decorator is failing to start, assuming you don't use Emerald.

Happens to me every now and again.

I usually kill X (ALT + SYSRQ + K)
Log back in and it's fine.

Can you press ALT+F2 (Should get a run box) and type
```
 gtk-window-decorator 
```

---

### Post by Carlo1973 on 2010-02-26
> gtk-window-decorator:8354): gtk-warning **: cannot open display:

Also note, when I tried to disable compiz from the Window configuration application,  I get an error saying that it can't detect my window manager - which when I last checked would have been GDM.

Could GDM have somehow gotten screwed up?

Carlo


EDIT:

Issue is fixed. I had one of our senior IT memebers at work tunnel into my machine and see what was going on. Fixed it by enabling Fusion-Icon, selecting Metacity, then Compiz. then selecting the GTK Window Decorator. He mentioned I should use Emerald, so we switched it to that after. Next he reloaded the Window Manger. Everything seems to be working again in gnome <YAY!> Thanks for the advice :)

---

