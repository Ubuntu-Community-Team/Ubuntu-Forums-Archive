---
title: "windows snap feature for ubuntu?"
date: 2010-01-21
forum: General Help
---

### Post by princeofnam on 2010-01-21
i will often have to work with two windows at the same time.  unfortunately i lack another monitor and having two workspaces doesn't necessarily allow you to view two things at the same time.  is there a way to snap windows in the way windows 7 does when you drag it to the edge?

---

### Post by princeofnam on 2010-01-21
or even better. a keyboard shortcut.

---

### Post by Rob_H on 2010-01-21
If you use Compiz (desktop effects), then this feature is available through the "Snapping Windows" and "Wobbly Windows" plugins.

---

### Post by princeofnam on 2010-01-21
oh i see. but it doesn't automatically resize the window to half the screen.  am i missing that feature?

---

### Post by princeofnam on 2010-01-21
oh. i noticed this functionality was in the grid function. but, what is the kp5 button?

---

### Post by dmillerct on 2010-01-21
I would also like to know if this is possible. I am not sure it can be used with the "Desktop Cube" option enabled however.

---

### Post by princeofnam on 2010-01-21
it's definitely easily doable with the Grid function within Compiz.  most of the default key settings i'd like to use utilize buttons KP1-9.  i'm not sure what KP even stands for or which keyset its associated with.

---

### Post by dmillerct on 2010-01-21
> **princeofnam said:**
> it's definitely easily doable with the Grid function within Compiz.  most of the default key settings i'd like to use utilize buttons KP1-9.  i'm not sure what KP even stands for or which keyset its associated with.

It stands for Key Pad? anyway its the number pad 1-9. sucks if your on a laptop without one however.

---

### Post by dmillerct on 2010-01-21
FYI this appears to only work for the active window. If this worked for all windows in the current workspace I would be doing a jig right now.

---

### Post by stinkeye on 2010-01-21
You can have aero snap in ubuntu
[_**[COLOR="DarkRed"]http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html[/COLOR]**_]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html")

---

### Post by DanPiazza on 2010-02-25
> **stinkeye said:**
> You can have aero snap in ubuntu
[_**[COLOR="DarkRed"]http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html[/COLOR]**_]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html")

Thank you! Works perfectly.

---

### Post by wilee-nilee on 2010-02-25
> **stinkeye said:**
> You can have aero snap in ubuntu
[_**[COLOR="DarkRed"]http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html[/COLOR]**_]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html")


Dr. frankenstien "It's alive" yes this works.

---

### Post by Artiom.Fiodorov on 2010-05-06
the command 0 and command 1 in above mentioned guide dont work in Lucid

---

### Post by stinkeye on 2010-05-07
> **Artiom.Fiodorov said:**
> the command 0 and command 1 in above mentioned guide dont work in Lucid
They do for me.
Did you install wmctrl ?
```
sudo apt-get install wmctrl
```

---

### Post by Artiom.Fiodorov on 2010-05-07
I did. I think the problem is that I have 2 displays. It fails to get the width.

---

### Post by stinkeye on 2010-05-07
> **Artiom.Fiodorov said:**
> I did. I think the problem is that I have 2 displays. It fails to get the width.

Set up your own shortcuts using
```
wmctrl -r :ACTIVE: -e g,x,y,w,h
```

```
A  move  and  resize  argument  has  the  format
              'g,x,y,w,h'.   All five components are integers.
              The first  value,  g,  is  the  gravity  of  the
              window,  with 0 being the most common value (the
              default value for the window).  Please  see  the
              EWMH specification for other values.

              The   four   remaining  values  are  a  standard
              geometry specification: x,y is the  position  of
              the  top  left  corner of the window, and w,h is
              the width and height of  the  window,  with  the
              exception  that  the value of -1 in any position
              is interpreted to mean that the current geometry
              value should not be modified.
```

eg for my screen resolution of 1680 x 1050, to get half screen tiling on the left I would use
```
wmctrl -r :ACTIVE: -e 0,0,0,840,1050
```

and you could also install easystroke and assign your wmctrl commands to a mouse gesture.
```
sudo apt-get install easystroke
```

---

### Post by Artiom.Fiodorov on 2010-05-07
thanks, I didn't follow the advice but you gave me an idea simply put my width in WIDTH= in commands 0 and 1 :)

---

### Post by Riotact747 on 2010-10-31
Hey, I would like to get the snap feature, but the link is down. I have 10.10. Can anyone point me in the right direction?

---

### Post by stinkeye on 2010-11-01
> **Riotact747 said:**
> Hey, I would like to get the snap feature, but the link is down. I have 10.10. Can anyone point me in the right direction?
I think omgubuntu changed servers and I can't find old posts even searching the site.

Try this method....
[**_[COLOR="DarkRed"]http://wwww.ubuntuforums.org/showpost.php?p=9190800&postcount=45[/COLOR]_**]("http://wwww.ubuntuforums.org/showpost.php?p=9190800&postcount=45")

You will need to install **wmctrl** for the above to work.
```
sudo apt-get install wmctrl
```

---

### Post by HiImTye on 2010-11-01
Maximumize [http://www.youtube.com/watch?v=j_CJhdynfTE](http://www.youtube.com/watch?v=j_CJhdynfTE)
put [http://www.youtube.com/watch?v=h00CMkiWDGU](http://www.youtube.com/watch?v=h00CMkiWDGU)
etc

there's many useful plugins for compiz that you can access via ccsm

if you dont have it installed
```
sudo apt-get install compizconfig-settings-manager
```
then it will be in system > preferences

---

