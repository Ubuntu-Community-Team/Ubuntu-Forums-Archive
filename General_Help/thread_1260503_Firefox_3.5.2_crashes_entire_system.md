---
title: "Firefox 3.5.2 crashes entire system"
date: 2009-09-07
forum: General Help
---

### Post by lariosa42 on 2009-09-07
Hello,

I've been dealing with this problem for awhile and I'm finally getting around to posting about it.  Nearly once a day Firefox 3.5.2 will freeze so badly that it doesn't even go grey and the system monitor in my panel freezes.  I can't click anything, and CTRL+ALT+DEL, CTRL+ALT+BKSP, CTRL+ALT+F1 and SysRq+R+E+I+S+U+B do not work.  However, any music I was listening to continues to play uninterrupted.  

I think this is happening when I access Java via Firefox, though the error is not repeatable.  After I do a hard restart, I can have the same programs open, go back to the same page, and click on whatever link froze my system.  This does not seem to happen during the same time of day, nor after the same system up-time (some days I can leave the computer running for days at a time, other days it crashes after a few hours).  

Can anyone help?  I would be interested to know: (a) If you have an idea on how to fix it, or (b) of you know a way to force-quit Firefox when this happens so that I do not have to do a hard restart (remember, mouse and standard keyboard shortcuts do not seem to work).  Thanks ahead of time!

EDIT: I'm running Ubuntu Jaunty 9.04 on an Intel 945GM/PM/GMS graphics card with Compiz in the background.  I never had this had this problem with earlier versions of Firefox or Ubuntu.  Since the crashing seems fairly random, I can't easily test what effect shutting off Compiz, etc. will have.

---

### Post by mike555 on 2009-09-07
There is a fix , I don't remember where , but searching the forums should find it ....... I had that problem a while ago and used it as an excuse to buy a new nvidia video card  :)

(I got a low priced 7300 and it works great)

---

### Post by lovinglinux on 2009-09-07
[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by FunkyRes on 2009-09-07
Similar issue with some users on CentOS 5.3 is believed to actually be a video driver bug. There's a page that demonstrates it.

Works fine on my desktop but same page crashes my laptop.
By crashes I mean kills the X server, kernel still running.

---

### Post by Windows Nerd on 2009-09-07
Hmm...if you could only see what error messages it gave you. Another thing to do would be to start it from the command line by typing "firefox" without the quotes. Then paste the resulting error messages here when the problem happens. Can you alt-tab or change the active window at all? Another thing to do would be to keep a record of what you are doing before the crash and see if there is a pattern.

Scott

---

### Post by lovinglinux on 2009-09-07
> **Windows Nerd said:**
> Hmm...if you could only see what error messages it gave you. Another thing to do would be to start it from the command line by typing "firefox" without the quotes. Then paste the resulting error messages here when the problem happens. Can you alt-tab or change the active window at all? Another thing to do would be to keep a record of what you are doing before the crash and see if there is a pattern.

Scott

Also try creating a new profile from Firefox Profile Manager and then launching Firefox with it. If it doesn't crash, then you will now it's some sort of profile corruption causing the problem, which is pretty easy to fix. To access the profile manager run the following command in a terminal:

```
firefox -P
```

---

### Post by lariosa42 on 2009-09-08
mike555 - 
I only wish I was short on excuses to upgrade my video card!  ;)  Unfortunately, I have a dell laptop and no upgrade is available.

lovinglinux - 
Thanks for the great guide.  I haven't read through the whoole thing yet, but I tried a couple of things.  We'll see if this helps.  I'll try running under a new profile for awhile and see what happens.

Windows Nerd - 
Thanks for the suggestion, but unfortunately I can't tab between windows when it crashes.  Maybe I could make the terminal window "always on top," but I would be surprised if it updated after the crash.

I'll keep working on it.  Thanks for the suggestions so far everyone!

---

### Post by Mariane on 2009-09-10
There is a thread on the same subject here:
[http://ubuntuforums.org/showthread.php?t=1262227&highlight=crashes](http://ubuntuforums.org/showthread.php?t=1262227&highlight=crashes)
So I wonder how many people are having this problem. 

I'll try launching firefox from the terminal. If it writes something on the terminal I won't be able to copy it but if I leave both windows visible at all times, one under the other, maybe I'll see something. It means surfing in a reduced window, but that will do for a while. Then if I see something I'll write it down with pen and paper and then I'll post it here. 

Mariane

---

### Post by dcstar on 2009-09-10
I had found that when FF 3.5 imported my existing FF 3.0 about:config settings (profile) it did it so imperfectly that the memory cache broke on 3.5 (among other things...)

Unfortunately deleting the 3.5 profile did not create a fresh profile because it continually imports any existing 3.0 profiles on your system - you have to rename the 3.0 profiles to allow a totally fresh 3.5 profile to be created (then you can rename them back).

I suggest you try and get a totally fresh 3.5 profile on your system and see if you still have issues, as it may be possible that a similar imperfect profile import could be a factor.

---

### Post by Mariane on 2009-09-13
> **Mariane said:**
> 
I'll try launching firefox from the terminal. If it writes something on the terminal I won't be able to copy it but if I leave both windows visible at all times, one under the other, maybe I'll see something. It means surfing in a reduced window, but that will do for a while. Then if I see something I'll write it down with pen and paper and then I'll post it here. 


And of course, now that I'm waiting for it to happen, it doesn't. 

Mariane

---

