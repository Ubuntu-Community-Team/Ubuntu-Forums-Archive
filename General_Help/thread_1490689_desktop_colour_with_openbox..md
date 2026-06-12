---
title: "desktop colour with openbox."
date: 2010-05-22
forum: General Help
---

### Post by ppkombo on 2010-05-22
Hi:
Sorry about my english.
I am using ubuntu + openbox.
Openbox does not use any program to managed the desktop,so I only could see a black screen.
What file do i have to edit for change the colour?
I don't want to use a program (like nitrogen to select a background image etc).
Thanks a lot.

---

### Post by m_duck on 2010-05-22
You can use ***xsetroot*** to change the background colour. It can either be used with a named colour or a colour's hex value, so to set the background to blue, you can use either of the following:
```
xsetroot -solid blue
```
```
xsetroot -solid "#0000ff"
```

---

### Post by ppkombo on 2010-05-23
thanks a lot about the answer.
I would like to make a gradient colour.
I was reading the man but i don't know how to make a comand and there is not many information at the web.
It's possible?
using the x y parametres?
Thanks

---

### Post by m_duck on 2010-05-23
I don't think it's possible to set a gradient background with xsetroot, though I wouldn't mind being proved wrong.

The x and y parameters will allow you to create a sort of "textured" background by adding a small blocked pattern though needs to be used with the ***-bg*** switch rather than the ***-solid*** switch, i.e.
```
xsetroot -bg "#392841" -mod 3 3
```From a a quick search for "xsetroot gradient" a number of places suggest that the gradient is not possible with xsetroot alone. There do seem to be some options for creating a gradient but all require additional programs, without the use of xsetroot. [This site]("http://fixunix.com/xwindows/91124-drop-replacement-xsetroot.html") seems to have some interesting suggestions, though I have not tried them (and they require extra programs).

---

### Post by ppkombo on 2010-05-23
thanks a lot again.

---

### Post by kerry_s on 2010-05-23
you can install "nitrogen" to do your background image.
or
use pcmanfm for your file manager, which also does backgrounds.

i'm using pcmanfm on mine.

---

