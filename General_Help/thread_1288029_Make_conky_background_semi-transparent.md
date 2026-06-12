---
title: "Make conky background semi-transparent?"
date: 2009-10-10
forum: General Help
---

### Post by josephellengar on 2009-10-10
I love conky and want to keep it, but having the solid background is just plain ugly.  And when I try to change my background, if conky is completely transparent, I have to completely redo the text size and color.  Is there any way to make conky keep a semi-transparent background?  Oh, and how do I change the color of the conky background?  I can't get it to be anything but black.

---

### Post by AppleBonker on 2009-10-10
You should check out the thread [here](http://ubuntuforums.org/showthread.php?t=281865).  Though I must warn you, there are tons of ideas floating around in there that might make you spend more time than you ever imagined tweaking your conky.  There are also plenty of conky experts in there to help with any question you might be able to come up with.

---

### Post by darco on 2009-10-10
I think the command would be "own_window_transparent yes" but the best thing to do is go to the thread mentioned above. Find a posted conky file and run it on you own pc. Then copy over the commands to your own file...have fun tweakin!

darco

---

### Post by labinnsw on 2011-01-01
> **AppleBonker said:**
> You should check out the thread [here](http://ubuntuforums.org/showthread.php?t=281865).  Though I must warn you, there are tons of ideas floating around in there that might make you spend more time than you ever imagined tweaking your conky.  There are also plenty of conky experts in there to help with any question you might be able to come up with.

As much as I want to, I cannot afford to read through 101 pages. Are you able to say, with any more accuracy, where the solution can be found?

---

### Post by stinkeye on 2011-01-01
You can use a lua script to draw a semi-transparent background.(Pic 1)
See here: [**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10283374&postcount=15524[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10283374&postcount=15524")
This will draw a semi-transparent background with rounded corners to the size of your conky window.
To adjust the radius of the corners and colour, read the first part of the script.



or 

you can use conky's argb transparency.(Pic 2)
eg use these settings in your conky config.
```
own_window_argb_visual yes
own_window_argb_value 180
```

**[COLOR="Red"]Note:[/COLOR]**you must also have 
```
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints undecorated,below,skip_taskbar,skip_pager
```
in your config.

From man conky
> **own_window_argb_visual** 
Boolean, use ARGB visual? ARGB can be used for real transparency, note that a composite manager is required for real transparency. This option will not work as desired (in most cases) in conjunction with 'own_window_type override'. 

**own_window_argb_value **
When ARGB visuals are enabled, use this to modify the alpha value used. Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity. Note that if own_window_transparent is enabled, this value has no effect.

---

### Post by labinnsw on 2011-01-01
> **stinkeye said:**
> You can use a lua script to draw a semi-transparent background.(Pic 1)
See here: [**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10283374&postcount=15524[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10283374&postcount=15524")
This will draw a semi-transparent background with rounded corners to the size of your conky window.
To adjust the radius of the corners and colour, read the first part of the script.



or 

you can use conky's argb transparency.(Pic 2)
eg use these settings in your conky config.
```
own_window_argb_visual yes
own_window_argb_value 180
```

**[COLOR="Red"]Note:[/COLOR]**you must also have 
```
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints undecorated,below,skip_taskbar,skip_pager
```
in your config.

From man conky

Thanks, I found your other post (about the lua script) and was about to post the link here. It works great and was the only one I found clear enough to follow.

---

### Post by jcolyn on 2011-01-01
Here's what it took to make mine semi-transparent.

Note these 2 extra lines ```
own_window_argb_visual yes
own_window_argb_value 95
``````
own_window yes
own_window_transparent no
own_window_argb_visual yes
own_window_argb_value 95
own_window_class Conky
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background yes
```

---

