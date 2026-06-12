---
title: "Borked up unity/compiz... again"
date: 2011-10-22
forum: General Help
---

### Post by moorhead98 on 2011-10-22
This time I tried to activate some compiz effect via ccsm (I  think wobbly windows) and compiz crashed and froze up the screen. So I  used the Control+Alt+Backspace keystroke to force logout. Then I logged  back in.


  Unity wasn't there, just a (non-unity) panel at the top with file,  edit, and the like. I was able to pull up a terminal and launch ccsm,  only to find almost all settings wiped out.
  I turned everything back on that I thought should be on, but I don't  know if I got everything. Also, now whenever I open up a non-maximized  window, it opens up in the top left corner with the title bar behind the  unity panel. So yeah thats VERY annoying


  So what I need is a list of everything that needs to be on in ccsm, and a way to get windows to NOT open in the corner.
  And all that without having to reset unity or compiz

---

### Post by clappboard on 2011-10-22
Try booting into recovery mode, then typing:
```
sudo apt-get remove compizconfig-settings-manager
```
then
```
unity --reset
```

This should solve your problems.  Or just log into Ubuntu Unity 2D then do the same ;)

---

### Post by moorhead98 on 2011-10-22
I sort of don't want to reset unity. Are there any ways without doing so?

---

### Post by clappboard on 2011-10-23
Not to my knowledge.  I had the exact same problem, and this was the only thing that had any effect.  You can try uninstalling ALL compiz related packages, but that didn't work for me either :(

---

### Post by stinkeye on 2011-10-23
You can reset compiz to defaults with the command
```
gconftool-2 --recursive-unset /apps/compiz-1
```

After this you will need to run ccsm and enable the Unity plugin.
you will get a window asking to resolve conflicts....click yes.
Then click every button on the far right of every subsequent window.

Wait a while and if you have no panel run
```
compiz --replace
```

I've attached 2 launchers 
 * One to load a terminal
 * and one to run compiz --replace

Extract and place in the bottom right of your desktop.
Comes in handy when messing with ccsm.

As for windows opening in the top right look in
ccsm > Window management > place windows 
and change to centered.

---

### Post by moorhead98 on 2011-10-23
> **stinkeye said:**
> You can reset compiz to defaults with the command
```
gconftool-2 --recursive-unset /apps/compiz-1
```After this you will need to run ccsm and enable the Unity plugin.
you will get a window asking to resolve conflicts....click yes.
Then click every button on the far right of every subsequent window.

Wait a while and if you have no panel run
```
compiz --replace
```I've attached 2 launchers 
One to load a terminal
and one to run compiz --replace

Extract and place in the bottom right of your desktop.
Comes in handy when messing with ccsm.

As for windows opening in the top right look in
ccsm > Window management > place windows 
and change to centered.

-_- 

Please read the original post. 
I do not want to reset compiz or unity unless I have to.
I will reset unity/compiz if I absolutely have to, but since unity/compiz are working now, I just want a list of everything that needs to be on in ccsm so I can make sure that everything that should be on is on.

But thank you so much for telling me how to get windows to not open in the corner!

---

### Post by stinkeye on 2011-10-23
> **moorhead98 said:**
> -_- 

Please read the original post. 
I do not want to reset compiz or unity unless I have to.
I will reset unity/compiz if I absolutely have to, but since unity/compiz are working now, I just want a list of everything that needs to be on in ccsm so I can make sure that everything that should be on is on.

But thank you so much for telling me how to get windows to not open in the corner!
Make a new account login and take a look.
ccsm > preferences

Sheest, I don't know why I bother.
:roll:

---

