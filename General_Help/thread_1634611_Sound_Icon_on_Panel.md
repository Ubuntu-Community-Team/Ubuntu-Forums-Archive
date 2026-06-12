---
title: "Sound Icon on Panel"
date: 2010-11-30
forum: General Help
---

### Post by evworld on 2010-11-30
Ubuntu 10.10

I was having problem with veetle sound sinc.  I was instructed on their forum to do this.

sudo apt-get autoremove pulseaudio

I did that and I lost the sound icon on the panel along with the rythymbox thing.

So I did this thinking it would bring the panel icon back.

sudo apt-get install pulseaudio                 Teminal installed pulseaudio but the icon never came back.

Any ideas how to get the icon back??

---

### Post by 0N3 on 2010-11-30
Right click your panel and add indicator-applet

---

### Post by Frogs Hair on 2010-11-30
Right click the panel select add to panel and add indicator applet.

---

### Post by evworld on 2010-11-30
When I do that all I get is a envelope looking icon.

---

### Post by 0N3 on 2010-11-30
open a terminal and type

sudo apt-get install indicator-sound

---

### Post by evworld on 2010-11-30
> **0N3 said:**
> open a terminal and type

sudo apt-get install indicator-sound


That did it..... Now I have my panels screwed up so I deleted them and adding the applets back in.  What the one with the user name in the right hand corner.   Is there a way to put the bottom panel and the top back to default?

I found it indicator-applet session

---

### Post by Liverbones on 2010-11-30
The "user name" indicator would be indicator-session. It should show up in your panel applets as Indicator Applet Session. If you no longer have that applet, you can simply sudo apt-get install indicator-session to get it back.

As for restoring the default panels... unfortunately, there's really no way that I know of to get them back besides recreating them yourself.

---

### Post by 0N3 on 2010-11-30
the other thing you need to do is right click panel and add Indicator Applet Session
By right clicking each item you added you can move them around as to best suit you

---

### Post by evworld on 2010-11-30
I was able to figure out all the applets.. 

Thanks for everyones help..

---

### Post by uriel1998 on 2010-11-30
Just so you know, once you've got your panels the way you like them, you can back them up with this command:
```

gconftool-2 --dump /apps/panel > /PATH/TO/SAVE/panel_backup.xml

```

Using the appropriate path and filename, of course.  You can then restore a saved configuration by running:

```

gconftool-2 --load /PATH/TO/SAVE/panel_backup.xml

```

I usually save a "last known good" configuration when I start tinkering...

---

### Post by Liverbones on 2010-11-30
This is very useful. Thank you for the backup hint!

---

### Post by rick_d on 2010-12-02
[0N3]("http://www.uluga.ubuntuforums.org/member.php?u=956284") I love you dude, really
I've spent the whole night trying to make de sound indicator appear, but you made me realise it wasn't installed

Thank you so much

---

