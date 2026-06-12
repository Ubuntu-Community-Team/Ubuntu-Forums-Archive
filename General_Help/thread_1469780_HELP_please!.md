---
title: "HELP please!"
date: 2010-05-02
forum: General Help
---

### Post by toxic9813 on 2010-05-02
My power button on the top right of the top panel is GONE (ubuntu 10.04) instead, it's been replaced with the MeMenu label. (My physical power button is broken) I might post a screenshot.

How do I reset the panel to default?

---

### Post by Seal Daemon on 2010-05-02
I believe it's just an applet so .. add it ?

```
sudo shutdown -h now
```

---

### Post by toxic9813 on 2010-05-02
Well this is what that did... :(

---

### Post by toxic9813 on 2010-05-02
I remedied this by deleting those "Panels". Back to square one

---

### Post by spiky001 on 2010-05-02
right click panel add to panel,   add the indicator applet sesion

---

### Post by sunk8 on 2010-05-02
Add an Indicator Applet to the panel.

---

### Post by Seal Daemon on 2010-05-02
> **toxic9813 said:**
> Well this is what that did... :(

lmfao, how did you get the panel background images on both sides of your screen ? :-s

---

### Post by toxic9813 on 2010-05-02
I have no Idea

---

### Post by toxic9813 on 2010-05-02
This is what I get.

---

### Post by spiky001 on 2010-05-02
just next to the other applets theres a line  drag it to the left

---

### Post by toxic9813 on 2010-05-02
I already tried that. It didnt work so I deleted the line. Some invisible force stopping me from dragging that little icon anywhere except right.

---

### Post by toxic9813 on 2010-05-02
Whatever. I'm rebooting again to see if it fixes itself.

---

### Post by spiky001 on 2010-05-02
if you right click there is an option to _MOVE_ the time/calender applet

---

### Post by Seal Daemon on 2010-05-02
There's really an invisible force called [COLOR=Green]Lock To Panel[/COLOR] - unlock everything to the right from the applet you are trying to move .. profit!

---

### Post by WorMzy on 2010-05-02
To reset the panels, in a terminal write:

```
mkdir ~/.oldpanel
```
then
```
mv ~/.gconf/apps/panel ~/.oldpanel
```
then
```
*gconftool-2 --shutdown*
```
finally
```
pkill gnome-panel
```

---

### Post by toxic9813 on 2010-05-02
Okay guys, I'm sorry for the trouble. It wasn't locked to panel, I fixed it by rebooting, then it allowed my to move the line, and move it to the left and move the rest back into place. Thanks for the help.

---

### Post by toxic9813 on 2010-05-02
> **WorMzy said:**
> To reset the panels, in a terminal write:

```
mkdir ~/.oldpanel
```then
```
mv ~/.gconf/apps/panel ~/.oldpanel
```then
```
*gconftool-2 --shutdown*
```finally
```
pkill gnome-panel
```


That's what I was looking for, I'll take a screenshot of that for future reference. Thanks!

---

### Post by Paulplex on 2010-05-02
To add your 'shutdown' applet:[LIST=1]
[*]Right-click on the top panel and choose **Add to Panel...**
[*]Look down the list and you should find *Indicator Applet Session* - single left-click this to highlight it and choose **Add**
[*]When added, you might want to move it to the far right; to do so, right-click on the new applet and choose **Move**
[*]Drag to where you want and click the left mouse button when in position - you can right-click the applet and **Lock** it if you're happy with the location
[/LIST]
If you want to move the applet but 'other' applets are in the way, right-click on each one, uncheck **Lock**, move your indicator applet and then re-lock the applets you unlocked.

-----
*Opps - look like I took too long composing my rather fine reply there :)*

---

