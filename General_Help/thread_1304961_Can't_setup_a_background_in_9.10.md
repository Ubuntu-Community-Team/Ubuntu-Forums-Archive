---
title: "Can't setup a background in 9.10"
date: 2009-10-29
forum: General Help
---

### Post by Naminator_X_ on 2009-10-29
Hello there and congratulation to everybody for the release of Ubuntu 9.10 :) I just came back from work and installed it and i must say WOW i'm amazed !!! Everything works perfectly out of the box..but one thing is bugging me :S i click with the right mouse button on the desktop then select change desktop background from the context menu...i choose a background but nothing happens :S I drag icons but they doesn't show up :( it feels like my desktop is locked (is there such thing) and when i restart i see the wallpaper for a second or so. Tried few things but nothing helped :( Any ideas around that? 

And something alternative..at 9.04 my video card was working better than 9.10 (ATI Sapphire Radeon 9250 128mb - yeah i know it's ancient) but in the package manager it says that I have installed drivers and Hardware Drivers in preferences doesn't show anything to install :/ Q_Q

---

### Post by Naminator_X_ on 2009-10-29
I also noticed that the default movie player hangs when i use subtitles. I've configured everything utf-encodings fonts etc...it just hangs :S and btw my background is black only atm

---

### Post by Naminator_X_ on 2009-10-30
*BUMP* is it just me with this problem :OOO

---

### Post by P4man on 2009-10-30
try  gconf-editor
Then go to apps > nautilus > preferences. Make sure show_desktop is set.

As for movieplayer, try launching it from a terminal, see if you catch any errors.

---

### Post by Naminator_X_ on 2009-10-30
Running totem as sudo seem to fixed the problem. There was warning but now no matter if i run it as sudo or not it does play subtitles aswell as the movie :) thank you for that. Although can't tell the same for the desktop :( The thing you said was clicked. Here is a screen shot 

[ATTACH]133735[/ATTACH]

As you can see the desktop is empty but the folder in nautilos have 2 icons and should be showing my windows partition since i mounted it already. The checkbox is checked i didn't changed that. Though i can not use right mouse click on the desktop now...i could yesterday

---

### Post by P4man on 2009-10-30
You should NOT have to run movieplayer as root, and even if you would you should use **gksudo** not sudo. sudo is for terminal applications, gksudo for graphical. Doing it the wrong way can mess up permissions which may well be causing the problems you are currently having.

Try this. Create a new user and log in with that user:
```
sudo adduser testuser
sudo passwd testuser
```

log out, log in with testuser.

---

### Post by Naminator_X_ on 2009-10-30
I created 2 new users none of them worked. Then i tried the live cd...guess what...no wallpaper in there too. Then i booted back in Ubuntu 9.10 (installed one) logged in the main account i was going to log out and try the others once again but something made me to press Guest session. I clicked it it did what it did and i got logged with quest session with WORKING DESKTOP. Then i switched back to the main account and once again blank :( logged out then logged in...still bugged...after that i restarted...still nothing. But everytime i go Guest Session i get fully operational desktop :/ Maybe possible kernel bug ? I already bug posted at launchpad but it was like 10 hours ago and the current information is not there :S

PS: Thanks for the help so far. My thread is loosing popularity too fast because of the other bug reports. Thank you for looking into

PS2: I just noticed. When i use "Lock screen" and when i come back...i see the mouse pointer to change when i rollover the input field but i don't really see where is the input field :X it's all by luck

---

### Post by P4man on 2009-10-30
> **Naminator_X_ said:**
> I created 2 new users none of them worked. 

Worked in what sense? You couldnt log in with them, or you had the same issues?

> Then i tried the live cd...guess what...no wallpaper in there too.

Well, then it looks not so well. Your videocard is no longer supported by ATI, so you dont get to install restricted drivers from ATI, you are limited to the opensource ati/radeon drivers (as you where on jaunty). Im afraid I dont know those very well, but I bet your problem is related with it somehow.

Have a look here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
and perhaps here:
[https://wiki.ubuntu.com/X/Quirks#ATI%20Radeon%20Driver%20Quirks](https://wiki.ubuntu.com/X/Quirks#ATI%20Radeon%20Driver%20Quirks)

---

### Post by Himself2007 on 2009-10-30
Naminator

Hey I got the same problem as yours.
But I found a solution...try it.
Right click on desktop for appearance.
Go to visual effects and change for "NONE". 
Bang!
If you stick to Normal or Extra...problem comes back!
It must be a kind of bug in this release!

Himself2007

---

### Post by ajgreeny on 2009-10-30
> **Himself2007 said:**
> Naminator

Hey I got the same problem as yours.
But I found a solution...try it.
Right click on desktop for appearance.
Go to visual effects and change for "NONE". 
Bang!
If you stick to Normal or Extra...problem comes back!
It must be a kind of bug in this release!

Himself2007
+1

I have the ati 9200SE card and if I try to use compiz which worked great in 9.04, I have the same problem as you, with a black screen, no icons or anything else though it is possible to see the panels, rather corrupt, but they are there.

I'm going to try using cssm to see if I can find a configuration which works, and will report back.

---

### Post by Himself2007 on 2009-10-30
I have the ATI 9000 Pro.
...must be an ATI problem, I guess.
As you have one!

H2007

---

### Post by P4man on 2009-10-30
> **ajgreeny said:**
> +1

I have the ati 9200SE card and if I try to use compiz which worked great in 9.04, I have the same problem as you, with a black screen, no icons or anything else though it is possible to see the panels, rather corrupt, but they are there.

I'm going to try using cssm to see if I can find a configuration which works, and will report back.

dont search in cssm, that wont cure it, search in the links I gave above how to tweak the driver in xorg.

---

### Post by Naminator_X_ on 2009-10-30
Holy crap this crazy thing actually worked :O So my problem was only that damn setting. Ima go cry...

PS: I don't need vga drivers this is more of a dev pc...but i liked the looks of a fresh wallpaper and OK ordered icons don't you think :)

---

### Post by giosoftware on 2009-11-12
I have the same problem in my new migrated ubuntu 9.04>9.10 
and the solution of change de visual effects to NONE works for me too.
Maybe a bug?

---

### Post by Himself2007 on 2009-11-12
> **giosoftware said:**
> I have the same problem in my new migrated ubuntu 9.04>9.10 
and the solution of change de visual effects to NONE works for me too.
Maybe a bug?

Yes and this solution has an handicap actually, if you try to come back to the others positions on visual effects.
A permanent solution that I applied and worked great.
Consider post #6, here:

[http://ubuntuforums.org/showthread.php?t=1305306](http://ubuntuforums.org/showthread.php?t=1305306)

Himself

---

### Post by MemoriesOfMotion on 2009-11-13
I had a problem like this.  It was a hardware thing.  The hardware I had would not run all the fancy things in 9.10.  You have to go to system > preferences > appearance preferences > the the Visual effects tab then and set it to None.  After I did this, I could set backgrounds and add folders to the desktop.

---

### Post by MemoriesOfMotion on 2009-11-13
I had a problem like this.  The hardware would not run all the pretty things in 9.10.  Go to system > pref. > appearance  and then the visual effects tab.  Select none.  When i did this, it let me set the background and add icons.

---

### Post by Himself2007 on 2009-11-13
> **MemoriesOfMotion said:**
> I had a problem like this.  The hardware would not run all the pretty things in 9.10.  Go to system > pref. > appearance  and then the visual effects tab.  Select none.  When i did this, it let me set the background and add icons.

OK, changing to "NONE" solves the problem at first but you still can't adjust visual effects to normal or extra after again.
It's not that you ultimately need the feature but it more shows that there is something going wrond with video.
Try it. look in my previous post #15 and apply the sloution at the end of this post.
It works and solves the problem.
By the way this is not mine but brought by "REDNZL".

Luc

---

