---
title: "annoying GIMP program reaction"
date: 2010-01-10
forum: General Help
---

### Post by garfieldwasacat on 2010-01-10
Whenever I minimize GIMP and bring up another program such as Firefox, the GIMP toolbox always shows up on the sides of my screen.

Albeit underneath Firefox, but it is still annoying to have GIMP constantly popping up underneath

I do not have it set to "Always on top"

Is there a simple feature I am missing here to keep GIMP minimized?

Thanks

---

### Post by blazemore on 2010-01-11
Unfortunately, the GIMP is a multi-windowed application. That's not a bug; it's a feature!
New versions of GIMP will feature a single-windowed mode, due to popular demand.
There's an article here with instructions on how to try it out:
[http://www.learningubuntu.com/software/trying-out-single-window-mode-gimp-27](http://www.learningubuntu.com/software/trying-out-single-window-mode-gimp-27)

I'll put the instructions here as well on another post.

---

### Post by blazemore on 2010-01-11
1. Open a Terminal (Applications -> Accessories -> Terminal)
2. Type the following commands, followed by pressing Enter:
```
sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn
```
```
sudo apt-get update
```
```
sudo apt-get upgrade -y
```
3. Open GIMP
4. In GIMP, right-click "Windows" and click "single-window mode"

---

### Post by llawwehttam on 2010-01-11
> **blazemore said:**
> 1. Open a Terminal (Applications -> Accessories -> Terminal)
2. Type the following commands, followed by pressing Enter:
```
sudo add-apt-repository ppa:matthaeus123/mrw-gimp-svn
``````
sudo apt-get update
``````
sudo apt-get upgrade -y
```3. Open GIMP
4. In GIMP, right-click "Windows" and click "single-window mode"

Thanks for that. I've been wondering if this was possible for years!!

---

### Post by blazemore on 2010-01-11
Did it work? I haven't tried it.
It hasn't been possible for years, only very recently.

---

