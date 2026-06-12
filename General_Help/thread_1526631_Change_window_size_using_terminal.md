---
title: "Change window size using terminal"
date: 2010-07-08
forum: General Help
---

### Post by hellocatfood on 2010-07-08
Is there anyway to change the size of a window that's already open to a specific value? For example, I want to resize the size of an instance of gedit to exactly 100x200. Is there any way to do this?

---

### Post by AlphaLexman on 2010-07-08
Check out the man page for 'XResizeWindow'

I've never done it but it looks like your solution.

---

### Post by theneoindian on 2010-07-08
> **AlphaLexman said:**
> Check out the man page for 'XResizeWindow'

I've never done it but it looks like your solution.

it's a function , not a command rite ?

---

### Post by AlphaLexman on 2010-07-08
> **theneoindian said:**
> it's a function , not a command rite ?

Yes, it is a function, not exactly a command line answer to the op's question. But trying to point the op in a new direction for the solution.

---

### Post by stinkeye on 2010-07-08
Using wmctrl
```
wmctrl -r [COLOR="Purple"]gedit[/COLOR] -e 0,-1,-1,100,200
```
[COLOR="#800080"]use anything that's unique to the window's title[/COLOR]
eg if the title bar shows **conkyvnstat (~/conky)-gedit**
I would just use [COLOR="#800080"]conkyv[/COLOR]


You can also make a bash script set up to a keyboard shortcut
that will resize the active window I use this to resize and move 
my active window to the screen centre.
```
wmctrl -r :ACTIVE: -e 0,400,275,875,550
```



To install wmctrl
```
sudo apt-get install wmctrl
```


From man wmctrl
```
A move and resize argument has the format 'g,x,y,w,h'.  All five
              components are integers. The first value, g, is the  gravity  of
              the  window,  with  0  being  the most common value (the default
              value for the window). Please see  the  EWMH  specification  for
              other values.

              The four remaining values are a standard geometry specification:
              x,y is the position of the top left corner of  the  window,  and
              w,h  is  the  width and height of the window, with the exception
              that the value of -1 in any position is interpreted to mean that
              the current geometry value should not be modified.


```

---

### Post by eudennis on 2012-04-27
That's great. It's just what I was looking for. But it didn't work with Google Chrome yet, but still cool

---

### Post by DarkBowser on 2012-06-26
I have a question related to this: I can't open Assaultcube because of my resolution.

I try to open it from the terminal and here is what I get:

```
ryard@ryard-Latitude-2100:~$ assaultcube
Using home directory: /home/ryard/.assaultcube_v1.104
current locale: en_US.UTF-8
init: sdl
init: net
init: world
init: video: sdl
init: video: mode
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 55
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 56
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 59
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 58
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x194
  Serial number of failed request:  131
  Current serial number in output stream:  133
ryard@ryard-Latitude-2100:~$ 

```

I want to set the window to 800x600, help?

---

### Post by Elfy on 2012-06-26
Tagging on to the end of a 2 year old thread is nto a good idea.

Please start your own thread.

Closed.

---

