---
title: "Theme manager has gone Loco after upgrade!"
date: 2010-11-03
forum: General Help
---

### Post by 1984dc on 2010-11-03
Dear all.

After upgrading to 10.10 amongst other glitches i have been having a problem whereby my theme manager seems to have gone completely mental on me!! Every other time i boot up instead of being presented with my tailored theme (based around the impression theme) i am getting a horrible grey theme that as far as i am aware i have never used and isn't the standard ubuntu theme.

If anyone has had similar problems or knows of a possible solution i would be hugely grateful.

Many thanks in advance.

Dc

---

### Post by dimeotane on 2010-11-04
I have a similar problem.  I did an update yesterday, and upon reboot the Ambiance theme is all messed up. My desktop bars were light grey with the original gnome icons.  Nautilus looks like the classic linux KDE interface.   I went to appearance and re selecting Ambiance returned the desktop bars back to normal.  
Nautilus is still not being themed properly. 
:confused:

---

### Post by 1984dc on 2010-11-05
now all the gnome architecture (along with all of my other window managers seems to have crashed leaving nme in a *login of death *scenario (where ebvery ime i try to login it asks me for my password again and again ad infinitum)! 

For the time being i'm just backing up my data using windows (as i dual boot) and i suppose i'll reinstall ubuntu maybe formating the drive again, but this will all go in a new post once i've recovered all my data.
 
all the best
 
dc

---

### Post by 1984dc on 2010-11-23
Ubuntu back up and running :guitar:
I had ran out of space on my hard drive.

But the problem with the theme manager is still unresolved  :?:

---

### Post by 1984dc on 2010-11-24
Bump

---

### Post by 1984dc on 2010-12-01
Bump

---

### Post by 1984dc on 2010-12-07
I have noticed that whilst the theme manager is changed to the ugly grey theme most of my keyboard shortcuts don't seem to be working??

---

### Post by 1984dc on 2010-12-08
bump

---

### Post by 1984dc on 2010-12-17
bump

---

### Post by 1984dc on 2010-12-20
Still without an answer if anyone would like to "chip-in" :)

---

### Post by stinkeye on 2010-12-20
Happens to me and a lot of other users.
When it happens try alt+F2(or in the terminal) and run...
```
gnome-settings-daemon
```

If the theme still doesn't look right, run...
```
pkill nautilus
```

---

### Post by Frogs Hair on 2010-12-20
This seems to be happening to others see this thread. [http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

---

### Post by oarion7 on 2010-12-20
Make sure you run your Update Manager; I *think* this issue may have been resolved in an update for gnome-settings-daemon.

---

### Post by stinkeye on 2010-12-20
> **oarion7 said:**
> Make sure you run your Update Manager; I *think* this issue may have been resolved in an update for gnome-settings-daemon.
I'm up to date and still hapenning on nearly every boot.

---

### Post by 1984dc on 2010-12-21
I am also up to date and the problem still remains, though this does seem to be a fix for most users. All of the other fixes on the other thread seem like temporary fixes or work-arounds that have been proved to not work later on in the thread after a testing period. 

Many thanks

Dc

---

### Post by oarion7 on 2010-12-21
Hmm..

For what it's worth, my GTK theme has reset to the "ugly" gray theme as well, any time updates were run in Update Manager. Everything would be normal while downloading updates, but at some point during installation, everything would turn to the olds school gray theme; I would reboot and then it would be okay until next updates.

This all happened around November. I haven't had any updates in a while, I'll try to note if it happens again. For me the problem has never occurred on boot up, or in any other situation than running Update Manager.

---

### Post by 1984dc on 2010-12-21
I'm not sure if this has any connection but does everybody here have the emerald theme manager app installed?

---

### Post by freddybob on 2010-12-30
I have this problem on my netbook (running desktop Ubuntu 10.10).

I do not have Emerald Theme Manager.

I once used Ubuntu Tweak to change the window button position, could that be it?

---

### Post by 1984dc on 2011-01-01
I do have ubuntu tweak installed but as far as i know i have never used it to change any preferences. 
In the last week or two my theme manager has not been playing up. I'm not sure if that's chance or whether one of the updates has rectified the problem. 

Cheers 

Dc

---

### Post by 1984dc on 2011-01-11
Just had this problem again for the first time in a couple of weeks. Seems as though this is still an unresolved issue :(

---

### Post by 1984dc on 2011-03-07
Okay so i think that this probllem may be finallly fixed from an update or something. I haven't had the same problem for a goood few weeks now. I will mark this thread solved in a week or so if it doesn't start playing up again.

---

### Post by 1984dc on 2011-03-12
Spoke too soon, i think this issue will never be fixed. I&#7743; thinking of going over to mint and trying that as i have heard good things.

---

### Post by 1984dc on 2011-04-14
I have now officially left ubuntu on my laptop(in favour of LInux mint), but it lives on through the new powerpc install I did on my G5 last weekend, with so far no problems with a sketchy theme manager. Anyone who finds a fix for this please feel free to post itand let me know and i will mark the thread solved.
 
All the best.
 
Dc

---

### Post by 1984dc on 2011-04-15
Okay So now on my G5 Powermac (a totally different computer) I pressed ctrl+mute and the same grey style theme manager seems to have taken over again!!! How random & frustrating!
 
I suppose this must be a problem with gnome then as the computers couldn't be more different.
 
Any suggestions people?
 
Dc

I have also launched a new thread for my problems with my G5 [here]("http://ubuntuforums.org/showthread.php?t=1732697")

---

