---
title: "gksu nautilus changes desktop"
date: 2009-06-26
forum: General Help
---

### Post by measekite on 2009-06-26
OS = Jaunty Gnome

Situation:
I logon as reguser,  I need to make a change or view files in the file manager so I
launch terminal and

```
gksu nautilus
```

and provide the proper password.  Nautilus comes up and I do my thing as root.  Then I close nautilus and return to terminal.  I then close terminal.

Problem:

After terminal is closed I then see the reguser panels and menu system but with the root desktop icons and desktop colors etc.

Question:
1.  Why does this happen

2.  How can I avoid this from happening

3.  What do I have to do to return to the original reguser desktop and colors without haveing to log off and back on?


Thanks in advance

---

### Post by fragos on 2009-06-26
Try "gksudo nautilus"

---

### Post by measekite on 2009-07-06
> **fragos said:**
> Try "gksudo nautilus"

Same results.  The prompt is for reguser but the color background and desktop are from the root users.

---

### Post by drs305 on 2009-07-06
I've run into the same problem from time to time. When I've had this problem I just made a *shortcut* with the following command and it seemed to work.
```
gnome-terminal -x gksudo nautilus
```

I suppose it has something to do with nautilus is both a file manager and also controls desktop functions.

---

### Post by mc4man on 2009-07-06
I can't really help cause I don't use jaunty but happened to notice the same thing while using a jaunty livecd to build someone a few packages.

To clear some  room I needed to delete the packages in var/cache... and used gksudo nautilus.
Afterwards I noticed the one folder I'd had on the desktop had disappeared, logging out and in restored me to the user desktop w/ folder.

Thought it was strange, chalked it up to a livecd 'issue'

If you go Alt+F2 and run gksudo nautilus from there (don't check the 'run in terminal' box), does it behave better?

---

### Post by CatKiller on 2009-07-07
I've never come across this, but one option would be to run ```
gksu nautilus --no-desktop
``` instead. It's a bit of a handful, but you'll only need to type it once.

---

### Post by sdlynx on 2009-07-07
maybe just run ```
sudo nautilus
``` from the terminal, works fine for me...

---

### Post by fragos on 2009-07-07
> **measekite said:**
> Same results.  The prompt is for reguser but the color background and desktop are from the root users.

In my system only the windows colors and background changes to those of root. The desktop maintains the user's theme and colors. It sounds like you started X with gksudo.

---

### Post by abhilashm86 on 2009-07-07
if so much problem use midnight commander in terminal,
```

sudo apt-get install mc

```
its too easy to handle without affecting GUI.........

---

### Post by measekite on 2009-07-07
> **drs305 said:**
> I've run into the same problem from time to time. When I've had this problem I just made a *shortcut* with the following command and it seemed to work.
```
gnome-terminal -x gksudo nautilus
```I suppose it has something to do with nautilus is both a file manager and also controls desktop functions.

I have found the very best solution.

Here it is!!:popcorn:

```
sudo apt-get install nautilus-gksu
```**[SIZE=3][COLOR=Red]Works Great[/COLOR][/SIZE]**
[B]
after it installs[/B], log out and back in again to see the change.
then open your home folder and right click on a folder....
you should see [COLOR=Red]*"open as administrator" *[/COLOR]as an option now.
Last edited by fooman; May 12th, 2009 at 11:58 AM.. 

***And fooman gets the credit.  I am just passing it on to help others.***

---

