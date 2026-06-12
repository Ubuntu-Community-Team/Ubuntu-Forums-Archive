---
title: "NetBeans IDE 6.7.1 - Run Java Applet?"
date: 2010-03-04
forum: General Help
---

### Post by manco on 2010-03-04
I'm not sure if this is the place to post this, but I'm having trouble with NetBeans.

I'm trying to run a Java applet.

My code (provided by my Java instructor):

```
import java.awt.*;
import java.applet.*;
//import java.awt.event.*;

public class Pac extends Applet {
    int dx = 0;

    public void init() {
        setBackground(Color.lightGray);
    }

    public void paint(Graphics g) {
        dx = dx + 2;

        if (dx > 163) dx = -437;
        g.setColor(Color.yellow);

        g.fillArc(337 + dx,350,100,100,40,280);
        g.setColor(Color.black);
        g.fillOval(385+ dx,364,10,10);

        try {Thread.sleep(50);} catch (Exception e) {}
        dx = dx + 7; if (dx > 163) dx = -340;

        g.setColor(Color.lightGray);
        g.fillArc(337+ dx,350,100,100,-15,30);
        g.setColor(Color.yellow);
        g.fillArc(337+ dx,350,100,100,15,330);
        g.setColor(Color.black);
        g.fillOval(385+ dx,364,10,10);

        try {Thread.sleep(50);} catch (Exception e) {}
        repaint();
    }
}
```

I get 1 of 2 errors, depending on my config:

1) If I run it with *<default config>*

[IMG]http://i56.photobucket.com/albums/g198/yellowsnow4free/Computer%20Stuff/NetBeans_Run_Project_defaultconfig.png[/IMG]

2) If I run it with *Web Start*

[IMG]http://i56.photobucket.com/albums/g198/yellowsnow4free/Computer%20Stuff/NetBeans_Run_Project_Web_Start.png[/IMG]

Any help would be great.  I need NetBeans to work with applets for my Java class.

Thanks!

---

### Post by kracekumar on 2010-05-05
try shift+f6,applet will be running. . . .

---

