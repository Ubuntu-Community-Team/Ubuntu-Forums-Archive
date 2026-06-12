---
title: "Compiz not working at all!"
date: 2011-04-13
forum: General Help
---

### Post by joelstitch on 2011-04-13
So I installed Compiz because theres a lot of effects that I like that I can only get trough this application. It was working excelent but I did something that completely screwed ir up. I think I was trying to ennable the Gnome Vidual Effects (when I click on Extra effects it ask me if I want to keep the settings but if I close it and open it again it goes back to None effects) and somehow Compiz stopped working. I keep trying effects on it but they just don't work.

---

### Post by earthpigg on 2011-04-13
hi,

go to places -> home

view -> check the "show hidden files" option

find the .compiz folder

delete everything in it

log out and log back in

compiz should now be entirely restored to default settings like it was onthe day you installed ubuntu.

---

### Post by joelstitch on 2011-04-13
> **earthpigg said:**
> hi,

go to places -> home

view -> check the "show hidden files" option

find the .compiz folder

delete everything in it

log out and log back in

compiz should now be entirely restored to default settings like it was onthe day you installed ubuntu.

Its still not doing any of the effects

---

### Post by wilee-nilee on 2011-04-13
In the terminal run
compiz --replace

---

### Post by joelstitch on 2011-04-13
> **wilee-nilee said:**
> In the terminal run
compiz --replace

I get this message:

> Launching fallback window manager

But still not doing the effects

---

### Post by joelstitch on 2011-04-13
Here is an example video:

[http://www.youtube.com/watch?v=nnHPdLotm_s]("http://www.youtube.com/watch?v=m0-wtZNAC2s")

And here is one of what it should be doing:

[http://www.youtube.com/watch?v=nbCg9_YgKgM](http://www.youtube.com/watch?v=nbCg9_YgKgM)

---

### Post by Dutch70 on 2011-04-13
There is nothing but a blank green screen in your video.

Have you ever had Compiz/WobblyWindows working correctly? 
Please post the output of...
```
lspci | grep VGA
```

---

### Post by robertcoulson on 2011-04-13
Dutch70...The gentleman is offline, but I have the same problem...Here is my post, maybe you could help me.
Robert

---

### Post by Dutch70 on 2011-04-13
I'd be more than happy to try & help you, but it's important that you start your own thread and describe your problem in your own words, with some details. It makes it much easier to give you both the attention you need and doesn't confuse the OP of this thread.

Give this a quick read...
[http://ubuntuforums.org/showthread.php?t=1422475]("http://ubuntuforums.org/showthread.php?t=1422475")

Edit:
Also, I'm not sure if I can help the OP or not, I just asked for his graphics card because it will be needed for anyone that can help him.

---

### Post by robertcoulson on 2011-04-13
10/4...Thanks
Robert

---

### Post by joelstitch on 2011-04-14
> **Dutch70 said:**
> There is nothing but a blank green screen in your video.

Have you ever had Compiz/WobblyWindows working correctly? 
Please post the output of...
```
lspci | grep VGA
```

Yes I've had Wobbly Windows working earlier today. I have no idea what happen that made any kind of effect on my computer not work. This is what I get on the terminal:

> pag@pag-laptop:~$ lspci | grep VGA
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)

P.S. I also fixed the video link

---

### Post by joelstitch on 2011-04-14
I also tried the **compiz --replace** command and installing **fusion-icon** to be able to switch back to **metacity** but still nothing.

Would reinstalling ubuntu fix the issue? Would it mess things up if I do that?

---

### Post by joelstitch on 2011-04-15
I ended up downgrading to Lynx again cause I think the problem was with maverick. Now everything is working fine.

---

### Post by twtgd09 on 2011-04-15
I've been having a similar problem, when i check ccsm all of compiz's effects are disabled, when i do the replace thing it just removes the title bar from my windows. any ideas?

---

