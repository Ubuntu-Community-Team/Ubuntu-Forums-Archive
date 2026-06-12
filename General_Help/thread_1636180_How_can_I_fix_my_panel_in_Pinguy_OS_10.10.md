---
title: "How can I fix my panel in Pinguy OS 10.10?"
date: 2010-12-02
forum: General Help
---

### Post by lokote123 on 2010-12-02
I am using Pinguy OS 10.10 and I would like to know how can I set my panel to default or at least to put my control volume and mail into the panel?  I sue to have those feature before, but I accidentally delete them.  I been trying to figure it out but I do not know how to put them back, I put the sound iconin the panel but it used to be different before.  I would post two picture of how I would like it and how it is now.

---

### Post by alberto_m on 2011-02-15
Have you solved it? I guess you need to substitute the existing panel folder in '~/.gconf/apps/panel' with a copy of the original one (maybe extracting it from the dvd).
Am I right? Anyone can confirm?

A.

---

### Post by Frogs Hair on 2011-02-15
You could also post at the pinguy os forum  . [http://forum.pinguyos.com/](http://forum.pinguyos.com/)

---

### Post by teklife on 2011-05-17
you right click the panel>add to panel>notification applet

---

### Post by yugnip on 2011-12-31
If you haven't already, check this [post]("http://forum.pinguyos.com/Thread-Restarted-computer-and-lost-wireless?pid=1645#pid1645") at the Pinguy OS forums.

```
sudo rm -r ~/.gconf/apps/panel
sudo cp -R /etc/skel/.gconf/apps/panel ~/.gconf/apps
sudo chmod -R a+rw ~/.gconf/apps
sudo chmod -R 777 ~/.gconf/apps
```

---

