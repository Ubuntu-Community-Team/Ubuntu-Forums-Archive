---
title: "VLC works in XP but not Ubuntu."
date: 2010-02-04
forum: General Help
---

### Post by zozza on 2010-02-04
I have an external CD drive.  When I run put a CD in and close the drive in XP, VLC loads the movie.

In Ubuntu when I close the drive the CD icon with the name of the movie appears on the Desktop, the file information appears in the file browser, and "encouraging" noises are made by the CD player.  VLC however will not load the CD whether through this way or through loading it then selecting the CD.  After 30 seconds the CD stops running and nothing is loaded.

Any ideas?

What is irritating is that this works perfectly in XP but not in Ubuntu which is always touted as being better than XP.  Thanks.

---

### Post by oldos2er on 2010-02-04
When you say "loading it then selecting the CD" do you mean loading it through vlc's menu, or the desktop icon? Have you set your preferences to open a CD with vlc?

Which version of Ubuntu, and which version of vlc are you using?

---

### Post by zozza on 2010-02-06
> When you say "loading it then selecting the CD" do you mean loading it through vlc's menu, or the desktop icon? Have you set your preferences to open a CD with vlc?

I have tried by putting the DVD in the drive which automatically loads VLC and selecting the DVD from the VLC menu.

> Which version of Ubuntu, and which version of vlc are you using?

9.10 and VLC 1.02 Goldeneye.


Thanks.

---

### Post by 23dornot23d on 2010-02-06
I prefer to use Mplayer ...... have you tried it at all ............

[http://www.mplayerhq.hu/design7/screen.html](http://www.mplayerhq.hu/design7/screen.html)

sudo apt-get install mplayer

sometimes in linux it is quicker to install and use another app .......

but if you prefer VLC ..... then try to make sure the codecs you need are loaded in .........

mplayer is pretty good though and I rarely have any problems ....

xine is another .... that works well .... 

but if these do not work - it may just be that you need extra codecs ..... libavcodec-extra-52 ....

.............. Synaptic Package Manager ....... search for it .... and then load it in ......

hope this is of some help ...........

---

### Post by stoneage on 2010-02-06
Have you installed libdvdcss2 ?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by oldos2er on 2010-02-06
I'm not sure what the problem is, but if you want to upgrade vlc to 1.0.5, you can do so here: [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

---

