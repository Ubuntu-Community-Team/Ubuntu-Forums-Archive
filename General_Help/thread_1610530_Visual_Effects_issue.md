---
title: "Visual Effects issue"
date: 2010-10-31
forum: General Help
---

### Post by pwolfinger on 2010-10-31
I'm having some serious trouble with visual effects in 10.10. If I set it to None, my window borders and the buttons on the bottom panel disappear (which also was a problem for me in 10.04). If I set it to Normal, the shadows have incorrect transparency. And I also have a weird issue with Terminal as well, but that's less important.
[IMG]http://img97.imageshack.us/img97/7074/screenshot1wy.png

Before you ask about Compiz, it's pretty much always off. Although the problem did start after I started using it.

(no screenshot of the None issue because for some reason it won't let me. sorry. use your imagination to picture the same shot as above, but with no borders or shadows)

---

### Post by 73ckn797 on 2010-10-31
See if this will help.
[https://help.ubuntu.com/community/Metacity](https://help.ubuntu.com/community/Metacity)

---

### Post by pwolfinger on 2010-10-31
I don't really see anything pertaining to my situation or any instructions that might help, if I missed something please point it out to me.

---

### Post by trikster_x on 2010-10-31
> Before you ask about Compiz, it's pretty much always off. Although the problem did start after I started using it.

The shadows that are around your windows mean that compiz is indeed running.  Try typing this into a terminal:
```
metacity --replace
```
If that fixes your appearance problems, then type this into terminal:
```
compiz --version
```
Then post the results.  If the version is higher than 0.8.6, then that is where your problem is.  Newer versions have some stability issues.  If you would like to play with the stable version, then go [HERE]("http://ubuntuforums.org/showpost.php?p=9964610&postcount=2%20_") and there are instructions on how to properly downgrade compiz.

Speaking of the terminal, what is the problem you are having with that?  Sometimes you can kill two bugss with one thread.

---

### Post by pwolfinger on 2010-11-03
Thanks, Trikster_x (ps: ever thought of using Trixter? brought back memories of childhood. just a thought). I've used metacity --replace before and it popped up some strange error message I didn't recognize, going to find out my version and fix whatever I can with the coding provided in that thread if possible. I say "if possible" because now I'm running into two new issues: 1. switching effects from None to Normal or Extra no longer changes anything, and for some reason Ubuntu no longer sees my network (luckily I gave Windows 7 50gb of my hard drive when I installed Ubuntu juuust in case, that's how I've been getting here).

If I encounter any more issues I'll write them down on a piece of paper and post them here.

**EDIT: **Good news, everyone!

I've discovered the following very strange things:
1. Immediately after plugging the netbook in (it hadn't been all morning) it temporarily reverted to the default GNOME theme, connected to WiFi, and let me use Normal effects. Crazy, huh? Only it only sortof let me use Normal effects - the border appeared on Appearance, etc. but not for anything else.
2. After that I hit the Desktop button to get a very interesting message something like this: "Your window manager does not support the Desktop button, or you do not have a window manager." Aha, that would explain a LOT - it does not appear to actually be an Effect issue, but a window manager issue, as if my memory serves me right, window borders are turned over from Metacity to Compiz with Normal/Extra effects. :)
3. I'm on 0.8.6. Before that, I wrote down the error message I got with metacity --replace. It is as follows: ```
**
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL)
Aborted
```
Workspace? I wouldn't have ever suspected Workspaces of being an issue (especially since I only use one and don't even include it in my panel), but I suppose it's worth a look. :\

Also, I think it bears mentioning that I didn't have any of these issues before installing Compiz Fusion, and I had a few issues with that, so it may be involved in some way or another. Just a thought, I don't really know where to look for any issues with that, but maybe you have an idea?

---

### Post by trikster_x on 2010-11-03
Try purging compiz completely and reinstalling metacity.  I would like to tell you purge metacity before the reinstall, but that is linked to the ubuntu-desktop package and should something go wrong, It will cause far more problems than it would solve.  
To purge compiz:
```
sudo apt-get purge compiz-core
```
To reinstall all the metacity packages:
```
sudo apt-get install --reinstall metacity metacity-common libmetacity-private0
```  

Alternately you can go into synaptic package manager, type "compiz", then find compiz-core and mark for complete removal.  That package will cause the rest of the compiz suite to be removed as well.  For "metacity", just mark the packages in the command above for reinstallation.  

Also, what make and model is your comp?

---

