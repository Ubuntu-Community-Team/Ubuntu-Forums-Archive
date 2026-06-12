---
title: "tried to edit log in screen, boots into terminal"
date: 2010-03-01
forum: General Help
---

### Post by gofudgeyourselfx on 2010-03-01
i read this article, [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)

after doing this i restarted and my computer goes through the normal stuff but when its supposed to load my desktop it loads terminal. its a small terminal box in the upper left corner, only like 1/4 of the screen...theres a pointer, but its always 'busy' when its not inside the terminal box....i have no idea what i just did that could have got my screen here and would love some help : |

this would be the 6th time ive had to reinstall ubuntu because of graphical issues...

---

### Post by fub4r on 2010-03-20
Well, it's to bad noone has respnded because I have THE EXACT SAME PROBLEM!  Down top the fact that I will probably end up reinstalling for, geez, more than the sixth time due to graphical issues.  Completely out of left field, right?  The only somewhat odd thing I did was on my last, very recent reinstall I used the old /home dir.  Maybe a conflict of commands? Anyway, curse the name of xorg and all things related to it!

---

### Post by audiomick on 2010-03-20
> **fub4r said:**
>  The only somewhat odd thing I did was on my last, very recent reinstall I used the old /home dir.  Maybe a conflict of commands?
If you retain an old /home from an install with a messed up GUI, I think it will retain the messed up GUI...

---

### Post by nikhil1989k on 2010-03-20
Hey I am nikhil I am new to this forum but i will try to help you.
[B]U can start your gui by issuing command
startx or xinit [/B]
after that u restart your gdm 
_/etc/init.d gdm restart_
sure this should work

---

### Post by wojox on 2010-03-20
> **nikhil1989k said:**
> 
_/etc/init.d gdm restart_
sure this should work

9.10 uses:

```
sudo service gdm start
```

To the other posters when you get to the GDM select sessions and make sure gnome is selected.

---

### Post by fub4r on 2010-03-26
Forgive me, but this is not simply an issue of restarting x.  After my last post I did reinstall... again.  This time fresh, replaced /home.  Installed the fglrx driver and made the nominal offered updates and restarted. Remember I have done this many times, with 9.10, with nothing like this.  That same crap happened, just as gofudgeyourselfx.  When I try startx it reports that a session is already active.  This makes sense with the waiting, sort of flickering black background.[FONT=monospace][/FONT]  I have tried at least four other distros and unbelievably they are worse than ubuntu.  This is supposed to be the good one?  I apologize if I sound pissed, but I am.  I have great faith in open source, but it is being greatly tested, by x.  Not gnome, not even ubuntu, just x.org's "server"  I am not a n00b.  I have been using linux, namely ubuntu, for years and strangely graphical errors only seem to increase.  What am I to do? I'm typing this in god-forsaken Windoze! How lame is that!  Sorry for the rant.  I'll search the interwebs for help, but with every install I feel more defeated...  Thanks to all that try to help.  Good Luck.

---

