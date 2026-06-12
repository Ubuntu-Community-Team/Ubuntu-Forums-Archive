---
title: "Auto-login at boot with locked screen?"
date: 2010-01-30
forum: General Help
---

### Post by Ck.asdf on 2010-01-30
I'm not sure if this is possible, but if it's not, it should be. :)

I think it would be neat for single users of a computer to be able to turn their computer on, go do something like visit the kitchen, and when they come back their account will already be logged in, but the screen will be locked, and all they have to do is put in their password.

I'm not sure what kind of security issues would be raised by this, because for it to be effective, the screen would have to be locked for the entire duration of the login process, in case someone else came along to try to use the computer.

Is there something like this implemented already, or maybe an add-on package I can download from Synaptic?

---

### Post by Barriehie on 2010-01-30
Have you tried running **gnome-screensaver-command -l** (that's a lowercase L) at the start of the session?  That will lock the screen immediately.

Barrie

---

### Post by Ck.asdf on 2010-01-30
Okay, I set it so that I auto-login, which works, but when I went to System -> Preferences -> Startup Applications, then clicked "Add" I put the command you mentioned in the command spot.

I restarted the computer, it logged in, but the screensaver did not kick in.  I tried putting the command into an executable file (/home/ck/.lock) and referred the command to /home/ck/.lock and yet it still didn't lock the screen when I restarted the computer.

For verification, I ran "gnome-screensaver-command -l" (lowercase L) in the "Run Application" box (alt+F2) which worked, and when I ran my executable file (/home/ck/.lock) it also works.  But running it upon startup does not.

Suggestions?
Thanks for the help so far! :)

---

### Post by Barriehie on 2010-01-30
This should do it, put this in for your startup application.

```

gnome-terminal -e 'gnome-screensaver-command -l'

```

Don't know if the terminal will be persistent...

Barrie

---

### Post by Ck.asdf on 2010-01-30
Haha, yet again, the command you gave me works while I'm already logged in, but sticking it into the "command" box in the "Startup Applications" program doesn't seem to be helping.

---

### Post by Barriehie on 2010-01-30
> **Ck.asdf said:**
> Haha, yet again, the command you gave me works while I'm already logged in, but sticking it into the "command" box in the "Startup Applications" program doesn't seem to be helping.

Last ditch effort...
```

#!/bin/bash
sleep 12             # I'm just picking a number here.
gnome-terminal -e 'gnome-screensaver-command -l' &
exit 0

```

Save as whatever.sh and chmod +x and add to startup.

Edit: If still issues then -maybe- xscreensaver will do it, although what's been posted so far should work.  Of course my speakers should've worked too after my install... ;)


Barrie

---

### Post by Barriehie on 2010-01-30
Hmm, didn't work on my end either. Going to try something different... back in a min.

---

### Post by Barriehie on 2010-01-30
This worked!  I put this line as the last line of my .bashrc file.
```

sleep 10 && gnome-screensaver-command -l  # Might try with sleep 0 if works with 10

```

Barrie

Edit: We know that .bashrc is loaded on each instance so this SHOULD work on your end.

---

### Post by Ck.asdf on 2010-01-30
bah ... my computer's crazy, that's what I think.  Which by the way, I'm running 9.04, i don't think I mentioned that.  My signature says 9.10, but that's my laptop, and I'm on my desktop right now.

Anyway, I'm assuming that you mean my /home/ck/.bashrc or is there another location that I'm supposed to use?

I added the command you listed at the end of the bashrc and then restarted.  When I got back in, I saw the command window pop open & then close, but nothing happened for the screensaver.

I tried opening a console and at one point in time got a message saying something about how the screensaver was not running.


*sigh*
sorry this is being so crazy, but I appreciate your efforts.

---

### Post by Barriehie on 2010-01-30
k, at the end of ~/.bashrc
```

gnome-screensaver-command -l &

```

I think we can remove the sleep part.  The **&** should fork it to the background.

---

### Post by Ck.asdf on 2010-01-30
Errrrrrrrg.
I think I've just about given up on this project.  I modified it how you suggested, getting rid of the sleep stuff, adding the single ampersand at the end of the line, and when I opened a console just after logging in, it says:

```

** Message: Screensaver is not running!
ck@ck-desktop:~$ 

```

---

### Post by Barriehie on 2010-01-30
May be a dumb ?, do you have the screensaver enabled in your preferences???

---

### Post by Ck.asdf on 2010-01-30
My screensaver settings:

> 
Screensaver theme: Blank screen
Regard the computer as idle after: 5 minutes
[checked] Activate screensaver when computer is idle
[not checked] Lock screen when screensaver is active



An interesting note ... whenever the screensaver comes on after the 5 minutes, instead of going to a blank BLACK screen, it goes to a blank WHITE screen.  Then a minute after that it goes black, as I have the setting "put display to sleep when inactive for: 6 minutes"

---

### Post by Barriehie on 2010-01-30
Well, I'm out of ideas on this one.

---

### Post by Ck.asdf on 2010-01-30
Okay, well I thank you for your time in trying to help me with this.  You'd mentioned that you had it working on your end? What version of Ubuntu are you running? Maybe I just need to upgrade to the newest or something.

---

### Post by Barriehie on 2010-01-30
> **Ck.asdf said:**
> Okay, well I thank you for your time in trying to help me with this.  You'd mentioned that you had it working on your end? What version of Ubuntu are you running? Maybe I just need to upgrade to the newest or something.

I'm running 8.04.3 and one of these days I'm going to go back to 8.04.1 and disable the updates.  I seem to have more headaches with higher release #'s.

8.04.1 ran flawlessly for almost 2 years, it works on this box.

Barrie

---

### Post by Ck.asdf on 2010-01-30
**Here's a fun turn of events: now, when I open a terminal, the screensaver kicks in.**

I'm sure I can turn that off easily, but that's an odd thing.

hmmm ... I'm running 7.10 on my server. haha

---

### Post by Barriehie on 2010-01-30
> **Ck.asdf said:**
> **Here's a fun turn of events: now, when I open a terminal, the screensaver kicks in.**

I'm sure I can turn that off easily, but that's an odd thing.

hmmm ... I'm running 7.10 on my server. haha

Now mine was turning on the SS too and I couldn't find where it was starting from????  I ended up restarting and choosing a new session and all is well.  Screwy machine.

---

### Post by SFSDCris on 2010-05-06
This is working for me, except... on startup my computer is available for a few seconds, I can started doing commands, but then the screen saver kicks in.

Is there any way to completely prevent an user interaction? I want to create a turnkey system, but not one that unauthorized users can modify the computer.

Thanks!

-cris


----


[QUOTE=Barriehie;8750593]k, at the end of ~/.bashrc
```

gnome-screensaver-command -l &

```

---

