---
title: "Spooky Ubuntu Studio usplash problems."
date: 2009-07-24
forum: General Help
---

### Post by BslBryan on 2009-07-24
Hello, everyone.  :-)

I've uninstalled everything that is related to Ubuntu Studio in terms of packages.  

For some reason, the splash screen was still the Ubuntu Studio splash after that.  

"Hmm...  Well, let's remove the word "quiet" in every instance in menu.lst.  

*Restarts computer.*  Damn.  No dice.

Well, I never cared for usplash anyway.  I'll just remove it.  *Removes usplash.  Restarts computer.  Jaw hits floor.* "

That's right, the Ubuntu Studio usplash is still displayed, even though technically *neither it nor its helper application exist.*

I've researched and have come to the conclusion that my problem is either unique, or has so far been unreported.  I'll try anything at this point, within reason.  

Any suggestions?

---

### Post by Johnny B on 2009-07-24
can you change the uspash with startupmanager?
# sudo apt-get install startupmanager
# sudo startupmanager   # or system -> administration -> startup-manager
 Appearance tab -> manage uspalsh themes

---

### Post by BslBryan on 2009-07-24
Not anymore, as usplash does not exist.  

However, that was the first thing I tried.  It correctly displayed the splash I wanted at shutdown, but not at boot.

---

### Post by philcamlin on 2009-07-24
[http://ubuntuforums.org/showthread.php?t=428061](http://ubuntuforums.org/showthread.php?t=428061)

look at post #6 

isthis what your looking for

---

### Post by Johnny B on 2009-07-24
ok how about
# sudo apt-get install usplash-theme-ubuntu

---

### Post by BslBryan on 2009-07-24
> **philcamlin said:**
> [http://ubuntuforums.org/showthread.php?t=428061](http://ubuntuforums.org/showthread.php?t=428061)

look at post #6 

isthis what your looking for
Didn't work, but now I have to reinstall OOo3.0 :roll:  

Thanks, though! :-)

> **Johnny B said:**
> ok how about
# sudo apt-get install usplash-theme-ubuntu
Thanks, Johnny B, but I've already tried all of the easy stuff.  If I hadn't, I wouldn't have posted about it on the forums.  :-P

Any other ideas, guys?

---

### Post by philcamlin on 2009-07-24
im so sorry !
i didnt know it would hurt your machine :(
stupid move on my part

---

### Post by BslBryan on 2009-07-24
> **philcamlin said:**
> im so sorry !
i didnt know it would hurt your machine :(
stupid move on my part

Haha, don't worry about it. :-)  It's really not a big deal.

---

### Post by Johnny B on 2009-07-24
now that you have usplash-theme-ubuntu
check if its there:    /usr/lib/usplash/usplash-theme-ubuntu.so
and overwrite the link to your current usplash:
#   sudo ln /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-artwork.so

that should do it.

---

### Post by BslBryan on 2009-07-25
> **Johnny B said:**
> now that you have usplash-theme-ubuntu
check if its there:    /usr/lib/usplash/usplash-theme-ubuntu.so
and overwrite the link to your current usplash:
#   sudo ln /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-artwork.so

that should do it.

Johnny B, I have already stated that [I]I do not currently have usplash installed.
[/I]  But, to follow your instructions, I reinstalled it, but it still didn't help.  I'm sorry, but I don't think it's a problem with my usplash artwork considering I don't use usplash.

Thanks, though! :-)  

Any other ideas, anyone? :-P

---

### Post by Johnny B on 2009-07-25
sorry, i thought you were trying to remove the ubuntu studio usplash,
somehow i got the idea replacing it with the default usplash would solve the problem

---

### Post by BslBryan on 2009-07-25
> **Johnny B said:**
> sorry, i thought you were trying to remove the ubuntu studio usplash,
somehow i got the idea replacing it with the default usplash would solve the problem

Ah, sorry.  It's sound logic, but apparently my machine is not logical. :-)

---

### Post by BslBryan on 2009-07-25
[img]http://www.cemphotos.com/tx/tx-hawley/BUMP_Charles_B.jpg[/img]

---

### Post by zacinator on 2009-11-02
Bump.... I am having the same issue. I have tried everything, although I didn't go as far as removing usplash. Still the Ubuntu Studio ghost appears on every boot. The shutdown usplash has been fixed, but the opening has not!

---

### Post by Pelonchas on 2009-11-04
remove usplash, and purge package also. after that you need to update-grub. or update-grub2 depends of what you have.

---

