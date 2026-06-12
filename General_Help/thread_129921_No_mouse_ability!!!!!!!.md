---
title: "No mouse ability!!!!!!!"
date: 2006-02-14
forum: General Help
---

### Post by winkerbean on 2006-02-14
I have no mouse ability.  It is stuck in the upper right hand corner.  I checked for /dev/mouse.  No dice.  Any ideas?  Thanks.

---

### Post by RAOF on 2006-02-14
Well, some more information would be nice.  Such as:
1) What **sort** of mouse?
2) Was it working before, and has now stopped working, or has it never worked?
3) What does Xorg.0.log have to say about your mouse?  If I run
```
grep -i mouse /var/log/Xorg.0.log
``` I get
```
(**) |-->Input Device "Configured Mouse"
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
(==) NVIDIA(0): Silken mouse enabled
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Configured Mouse: Core Pointer
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 11
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```
How about you?

---

### Post by anirban.sam on 2006-02-14
restart and see the bootstrap for error msgs

---

### Post by winkerbean on 2006-02-14
Of course, how silly of me.  (To make matters worse, I work in Tech. Support and should know enough to provide details.)  Sorry.

The mouse I am using is a Micro Innovations one.  It never did work with Ubuntu (I just installed it.) but did work under Debian (although the scroll wheel did not).  As far as the log goes, I'll have to get back to you on that.  Thanks.

---

### Post by winkerbean on 2006-02-14
[QUOTE=anirban.sam]restart and see the bootstrap for error msgs[/QUOTE]

Forgive my ignorance, but how do I do that?

---

### Post by winkerbean on 2006-02-15
Hello,

Here is the 'mouse' related contents of the file:

(**) |-->Input Device "Configured Mouse"
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
(==) R128(0): Silken mouse enabled
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Configured Mouse: Core Pointer
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

Does it mean anything to you?  'Cuz it don't mean squat to me (I'm a software tech, not hardware.)

Thanks.

---

### Post by RAOF on 2006-02-15
Hmm... That makes it look like it should be working :)

I presume the mouse actually works (as in it works on another computer/in windows/ whatever)?

---

### Post by winkerbean on 2006-02-15
[QUOTE=RAOF]Hmm... That makes it look like it should be working :)

I presume the mouse actually works (as in it works on another computer/in windows/ whatever)?[/QUOTE]


Yes.  Sorry about that.

---

### Post by RAOF on 2006-02-15
Doesn't hurt to check.

Have you tried it in another mouse port?  Other than that, it looks like it's correctly configured - I'm not sure what the problem is.

---

### Post by winkerbean on 2006-02-15
[QUOTE=RAOF]Doesn't hurt to check.

Have you tried it in another mouse port?  Other than that, it looks like it's correctly configured - I'm not sure what the problem is.[/QUOTE]

i only have the one.

---

### Post by nanotube on 2006-02-15
hey
try this page:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Five_.285.29_Button_mouse](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Five_.285.29_Button_mouse)

specifically... replace imps/2 with explorerps/2, to see if that gets it working.
(the instructions on the page also show you how to enable extra buttons, if you have them...).

---

