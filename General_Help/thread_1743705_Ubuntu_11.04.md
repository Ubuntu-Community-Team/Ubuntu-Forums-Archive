---
title: "Ubuntu 11.04"
date: 2011-04-29
forum: General Help
---

### Post by vikrantalmelkar on 2011-04-29
Hi All,

i have just upgraded to 11.04 and enjoying it very much. 
but i clicked on something and now i do not have anything on the desktop. 
there are no toolbars on the top and the side. so cannot access anything at all.

can you please let me know how i can get it back to the original state.

Thanks very much for all the help

Vik

---

### Post by KegHead on 2011-04-29
Hi!

When you reboot you should be able to choose.

Choose classic to get into your system and then make changes.

KegHead

---

### Post by vikrantalmelkar on 2011-04-29
I have only 2 options on the reboot. 
1 - current version
2 - recovery mode

Thanks
Vik

---

### Post by howefield on 2011-04-29
Try pressing Alt + F2 and type in the run box

```
unity --reset
```

or try the hints and tips here..

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by vikrantalmelkar on 2011-04-29
Hi Howfield,

thanks for that. i am looking on the blog link that you gave and the problem was created due to my old compiz configuration.
can this be fixed
Thanks
Vik

---

### Post by mewroo on 2011-04-30
I am having a similar problem in Ubuntu 11.04 (guest OS) running virtual box where there is no menu bar and Unity does not display.  To resolve this I enter the following 
```
unity --reset
```
I'm grateful for the resolution but I must reset unity every time I log in.  Does anyone have any solutions to short of running a shell script to reset Unity upon login?

---

### Post by sikander3786 on 2011-04-30
> **mewroo said:**
> I am having a similar problem in Ubuntu 11.04 (guest OS) running virtual box where there is no menu bar and Unity does not display.  To resolve this I enter the following 
```
unity --reset
```
I'm grateful for the resolution but I must reset unity every time I log in.  Does anyone have any solutions to short of running a shell script to reset Unity upon login?
Do you mean Unity doesn't remember the configuration on reboot? Did you try resetting Compiz?

```
gconftool-2 --recursive-unset /apps/compiz
```

Log out and back in and see if it helps.

---

### Post by vikrantalmelkar on 2011-04-30
Hi All,

I finally got Unity to work by resetting CCSM.
Thanks very much for all your help/
Much appreciated

Thanks very much
Vik

---

