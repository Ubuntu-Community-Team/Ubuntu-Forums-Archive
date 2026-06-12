---
title: "Transparent bar at the top and bottom"
date: 2011-02-25
forum: General Help
---

### Post by mac4rfree on 2011-02-25
Hi Guys,

I like to have a transparent bar at the top and bottom. When i right click and select transparency or any colour,, it is present only in the center , but at the right and left corner there is no transparency..

Can somebody guide me in this..

Cheers!!!

---

### Post by DanneStrat on 2011-02-25
> **mac4rfree said:**
> Hi Guys,

I like to have a transparent bar at the top and bottom. When i right click and select transparency or any colour,, it is present only in the center , but at the right and left corner there is no transparency..

Can somebody guide me in this..

Cheers!!!

It has also happened to me.

If you have applets on the panel when

your try to change colour, adjust opacity etc.

then the panel will only change in the blank areas.

To solve it, right-click the panel and remove it.

Add a new panel and select the colour and

how transparent you want it to be.

Then you can add your applets back to the panel.

Good luck!

---

### Post by mac4rfree on 2011-02-25
how to select the color when adding the panel,, it is not giving me that option..

---

### Post by DanneStrat on 2011-02-25
> **mac4rfree said:**
> how to select the color when adding the panel,, it is not giving me that option..

When you've added the panel, right-click the new panel 

and select "properties". On the "background" tab you 

can set colour and transparency.

---

### Post by Frogs Hair on 2011-02-25
Panel Properties > Background > Check Solid Color > click on the color box and a color chooser will open.

---

### Post by mac4rfree on 2011-02-25
yeah guys, i tried that, but when i add applets, the applets are still having only theme background.. is there no way to change the background of the applets...

---

### Post by WorMzy on 2011-02-25
Have a look at this: [http://www.installing-linux.com/TB/?P=269](http://www.installing-linux.com/TB/?P=269)

---

### Post by nikefalcon on 2011-02-25
Try using compiz.
Install CompizConfig Settings Manager, and use the Opacity, Brightness and saturation options to set desired opacity for your gnome-panel.
(sorry for the shabby screenshot- am in a mighty hurry- just ignore the top window)

Hope this solves your problem, good luck!

---

### Post by mac4rfree on 2011-02-28
i like to make the area marked in red as transparent.. can anyone help me now.. i hope now i am clear...

---

### Post by WorMzy on 2011-02-28
I don't think it's possible to make just those specific parts transparent. It's either all or nothing.

Unless you download, modify, and compile the sourcecode for the applets in question. I can't really help you with that.

---

### Post by DanneStrat on 2011-02-28
> **mac4rfree said:**
> i like to make the area marked in red as transparent.. can anyone help me now.. i hope now i am clear...

What you're seeing is a known problem with the

"ambiance" and "radiance" themes and it's

caused by a setting in the themes themselves.

Do the following to fix them:

Open a terminal and do

```
[SIZE=3]gksudo nautilus /usr/share/themes[/SIZE]
```Now when you are in the themes folder with elevated

permissions to edit the files in question, look for the "ambiance"

and "radiance" folders. Inside each one of them you will have a folder

called "gtkrc-2.0*". *Get inside that folder and edit the file called* "*gtkrc".

Look for this line:

```
[SIZE=3]bg_pixmap[NORMAL] = "panel_bg.png"[/SIZE]
```and put a "#" in front of the line so it looks like this:

```
#bg_pixmap[NORMAL] = "panel_bg.png"
```And then save the file.(file > save)

Do the same procedure for

both themes.

Now it should be fixed.

Log out and back in again to

apply the changes or reboot.

Good luck.

---

### Post by mac4rfree on 2011-03-01
I am fine if we can make the whole thing transparent.. i was not able to do that also by following the above the mentioned answers... i jus want a transparent bar on the top and bottom

---

### Post by mac4rfree on 2011-03-01
i am not able to find the line
bg_pixmap[NORMAL]...

---

### Post by WorMzy on 2011-03-01
That's because DanneStrat's instructions are for Lucid, and (presumably) you're using Maverick. The link I posted has instructions for Maverick, but here they are again:

For Ambiance:
```
gksu gedit /usr/share/themes/Ambiance/gtk-2.0/apps/gnome-panel.rc
```
For Radiance:
```
gksu gedit /usr/share/themes/Radiance/gtk-2.0/apps/gnome-panel.rc
```

In both (or either) files, comment out line 10, like so:
```
#bg_pixmap[NORMAL] = "img/panel.png"
```

Save the file(s), then log out and back in.

---

### Post by mac4rfree on 2011-03-02
finally guys.. i made it... thanks guys...

---

