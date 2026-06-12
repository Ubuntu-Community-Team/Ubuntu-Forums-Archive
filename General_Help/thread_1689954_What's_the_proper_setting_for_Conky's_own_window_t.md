---
title: "What's the proper setting for Conky's own_window_type?"
date: 2011-02-17
forum: General Help
---

### Post by ethan1701 on 2011-02-17
Hi,
I'm using the[ most popular Conky configuration on Gnome-art]("http://gnome-look.org/content/show.php?content=134705"), as well as Compiz.

The problem I have is that when I minimize all windows, the Conky display also gets minimized and does not appear anymore.

The settings within Conky are:```

own_window_class Conky
own_window yes
own_window_type normal
own_window_argb_visual yes
own_window_argb_value 180
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

I've tried replacing
```
own_window_type normal
```
with
```
own_window_type desktop
```
and sure enough, it no longer gets minimized. However, if I then go and touch any item on the desktop, Conky disappears.

I've found plenty of threads dealing with either one of these problems or the other, but none that address the fact that switching from one causes the other...

Surely there's a setting that makes conky stay visible on the desktop at all times...

Thanks for your help!
-Ethan

---

### Post by ajgreeny on 2011-02-17
The only three window lines I have are:-
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
# If own_window is yes, you may use type normal, desktop or override
own_window_type normal
# Use pseudo transparency with own_window?
own_window_transparent yes
```so perhaps you could try commenting out the other lines you have with a # at the line start and see if it gets rid of the problem.

EDIT:  I have only just noticed that if I use Ctrl+Alt+D to minimise all windows, my conky display also disappears, just like yours, however when I repeat the Ctrl+Alt+D it comes back along with all other windows that were minimised.

---

### Post by Quackers on 2011-02-17
In my .conkyrc I have
```
own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type override
```

---

### Post by ethan1701 on 2011-02-17
@Quackers, your solution does in fact keep Conky on the desktop. However, it then introduces another issue: as pointed out in
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html), own_window_argb_visual does not work with own_window_type override, and the particular Conky setup I'm using requires real transparency (provided by own_window_argb_visual).

So now, I can chose any of these THREE problems:
1. Conky gets minimizes with all other windows
2. Conky disappears when the desktop is touched
3. Conky does not support transparency

Is there any way we can have conky work without having to chose one of these problems?

-Ethan

---

### Post by Dondermans on 2011-03-21
> **ethan1701 said:**
> @Quackers, your solution does in fact keep Conky on the desktop. However, it then introduces another issue: as pointed out in
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html), own_window_argb_visual does not work with own_window_type override, and the particular Conky setup I'm using requires real transparency (provided by own_window_argb_visual).

So now, I can chose any of these THREE problems:
1. Conky gets minimizes with all other windows
2. Conky disappears when the desktop is touched
3. Conky does not support transparency

Is there any way we can have conky work without having to chose one of these problems?

-Ethan

I am a novice user who experienced the same problem. I would like to share my solution with you:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes #when set to 'no' conky appears against a black background
own_window_type dock
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#These values set true transparancy
own_window_argb_visual yes
own_window_argb_value 100
```For some reason, this code appears to overwrite the value for ```
alignment top_right
```but you can set the position of Conky with the use of gap_x and gap_y. For my 1920x1080 panel the figures are:

```
## Use these values to position conky.
gap_x 1650
gap_y 20
```I have checked for the three problems you described in your message and this code seems to be the solution to all of them.

---

### Post by ethan1701 on 2011-03-22
That appeared to do the trick, thanks!!
The only downside I've found to this is that icons can't be placed under (or over) the part of the screen that conky is using, but I can totally live with that.

Thanks again!
-Ethan

---

### Post by Dondermans on 2011-03-23
> **ethan1701 said:**
> That appeared to do the trick, thanks!!
The only downside I've found to this is that icons can't be placed under (or over) the part of the screen that conky is using, but I can totally live with that.

Thanks again!
-Ethan

No problem. Glad to help.

---

### Post by nierdillapozi on 2012-09-23
> **Dondermans said:**
> I am a novice user who experienced the same problem. I would like to share my solution with you:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes #when set to 'no' conky appears against a black background
own_window_type dock
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#These values set true transparancy
own_window_argb_visual yes
own_window_argb_value 100
```For some reason, this code appears to overwrite the value for ```
alignment top_right
```but you can set the position of Conky with the use of gap_x and gap_y. For my 1920x1080 panel the figures are:

```
## Use these values to position conky.
gap_x 1650
gap_y 20
```I have checked for the three problems you described in your message and this code seems to be the solution to all of them.

Thanks. I was searching a real solution to fix these problems and  I didn't found anything that helped me... until this trick.

Very grateful.

---

### Post by davidedepau1996 on 2012-09-25
If I use
```
own_window_type panel
```
it works with Compiz (Unity).

---

### Post by hollerith on 2013-01-16
omfg don't do this! own_window_type panel puts everything below the bottom edge of conky in ringtail 13.04, it does stop it disappearing when you click the desktop though...

---

### Post by hollerith on 2013-01-16
own_window_type dock works for me, panel V. BAD.

---

