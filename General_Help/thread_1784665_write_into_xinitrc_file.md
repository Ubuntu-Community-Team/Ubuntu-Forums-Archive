---
title: "write into xinitrc file"
date: 2011-06-17
forum: General Help
---

### Post by sureshms on 2011-06-17
What is the format to write into the xinitrc file? i want the code "xset -dpms" and "xset s off" to be inserted into the file. How do i do so?

```


#!/bin/sh

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession


```Where do i insert the above commands into the file??

---

### Post by regala on 2011-06-17
> **sureshms said:**
> What is the format to write into the xinitrc file? i want the code "xset -dpms" and "xset s off" to be inserted into the file. How do i do so?

```


#!/bin/sh

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession


```Where do i insert the above commands into the file??

xinitrc is bash script. it loads /etc/X11/Xsession, so the answer lies in this file, depending upon what it effectively does -- it may never give back the hand to xinitrc after loading (if it execs another script for example). so there is no simple answer...

by the way why do you have to use xinitrc ? are you using startx ? in 2011 ?

br,

Mathieu

---

