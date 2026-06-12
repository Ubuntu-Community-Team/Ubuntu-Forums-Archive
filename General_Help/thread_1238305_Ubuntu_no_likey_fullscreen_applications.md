---
title: "Ubuntu no likey fullscreen applications?"
date: 2009-08-12
forum: General Help
---

### Post by Wilbefast on 2009-08-12
Hi all,

Got Ubuntu just a couple of weeks ago (standard release, all up to date, etc, etc), been trying to get some games working on it and a strange thing keeps happening whenever I run a full-screen application: every 10-15 minutes, without fail, I'm flicked out of fullscreen mode and loose control - I have to click on the tab at the bottom of the screen twice (first one minimizes) to bring it back to fullscreen, and meanwhile I loose control, which can be really inconvenient at times.

I thought this was a problem with ReMood/freedoom only it's happening with all fullscreen applications. Another thing that's wierd is that the power-saver kicks in a dims my screen after 2 minutes of playing a game in fullscreen (unless I turn it off): now I have no problem with power-savers, in fact I'd like to lower the delay below the arbitrary 11 minutes (anyone got a fix?) but somehow the OS is not registring that I'm using the computer - I think this is why it windows the application too: it's getting ready for power-saver.

Any help would be most welcome :)


William

---

### Post by P4man on 2009-08-12
Can't think of a workaround, but this sounds like a bug worthy of reporting on launchpad. Dont hold your breath for a fix, but if no one reports it, then no one will fix it :)

---

### Post by Wilbefast on 2009-09-04
Ah - sorry about not replying, my hard disk fried itself - only just got it replaced.

For certain fullscreen applications this bug basically forces me to pull the plug on the whole computer, because I have no mouse any more and can't do anything. Is there a sort of ctrl-alt-delete function for Ubuntu? 
In other words, how can I bring up a System Monitor and kill a program that's got its knickers in a twist? Perhaps I should be running these things from a terminal, though I'm not sure what difference that would make...


Also, where do I go to report my bug?


William

---

### Post by feelshift on 2009-09-04
Maybe is the screensaver. Set it to start after 2 hour or so.
Alt - SysRq (Print Screen) - K  should restart put you in the login menu.

---

### Post by Wilbefast on 2009-09-04
> **feelshift said:**
> Maybe is the screensaver. Set it to start after 2 hour or so.
Alt - SysRq (Print Screen) - K  should restart put you in the login menu.

It probably_ is_ the screensaver, but it would be good to be able to have a screen saver - would suck to have to turn it off :(

Still, I'll give it a try just to make sure that's what's causing the problem.


Thanks for the command - sure it'll come in handy :D

---

### Post by ad_267 on 2009-09-04
It's most likely this bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/157759](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/157759)

The easiest work around is to disable Compiz (which gives you fancy visual effects) by going to System - Preferences - Appearance - Visual Effects - None.

Edit: Sorry that ones a duplicate, the correct bug should be this one: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/155263](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/155263)

---

### Post by 3rdalbum on 2009-09-04
You can press Control-Alt-F1 to get to a terminal, and then use the "killall" command to kill the program:

```
killall sauerbraten
```

Or you can kill the entire X server and all running graphical programs, by pressing Alt-PrintScreen-K.

But the problem is caused by Compiz; turn it off before playing full-screen games.

---

### Post by ad_267 on 2009-09-04
You can install the fusion icon to easily switch from Compiz to Metacity when playing games.

I also wrote a script a while ago which switched to metacity when running a game: [http://ubuntuforums.org/showthread.php?t=867562](http://ubuntuforums.org/showthread.php?t=867562)

If you don't use the screensaver you can probably try turning that off instead. I like to keep my screensaver though.

---

### Post by Wilbefast on 2009-09-04
> **3rdalbum said:**
> You can press Control-Alt-F1 to get to a terminal, and then use the "killall" command to kill the program:

```
killall sauerbraten
```Or you can kill the entire X server and all running graphical programs, by pressing Alt-PrintScreen-K.

But the problem is caused by Compiz; turn it off before playing full-screen games.

How did you know it was sauerbraten? Are you psychic or something!?

Unfortunately having gotten into the fullscreen terminal (Ctrl Alt F4) I didn't know how to get back out :-S "exit" returns you to a logon screen so I used "sudo shutdown 0" and rebooted it...

If it's the pretty visual effects that are doing it then I'll just turn them off for good (I don't need a pretty desktop) rather than the screensaver (save the planet maaaaan).

Thanks for the help guys - actually, I might try that script of yours ad...

---

### Post by 3rdalbum on 2009-09-04
> **Wilbefast said:**
> How did you know it was sauerbraten? Are you psychic or something!?

That was the first game where I noticed the problem originally :-)

> Unfortunately having gotten into the fullscreen terminal (Ctrl Alt F4) I didn't know how to get back out :-S "exit" returns you to a logon screen so I used "sudo shutdown 0" and rebooted it...

Oh I am sorry; I should have mentioned that the X server runs under Control-Alt-F7 (sometimes Control-Alt-F8). I apologise for this oversight of mine.

---

### Post by Wilbefast on 2009-09-06
Ah - now that is handy: I can get back out again :D

The screen still dims after a few minutes but at least it doesn't crash anymore... it is strange that it should not register that I'm touching the keyboard/mouse...

---

### Post by Wilbefast on 2009-10-31
Might bump this - still having problems with fullscreen applications: apart from them losing focus when compiz is activated they will dim if "dim screen when inactive" is set and I've now realised that the volume can't be adjusted (with the laptop volume buttons) while in a full screen application, which at times means having to close it, readjust the volume and open it again :(

I've just heard about something called the "100 papercuts" - this is definately a paper cut for me: constantly mildly annoying if not actually properly impeding anything :o

---

### Post by ad_267 on 2009-10-31
The papercuts were for Karmic and are finished now. I doubt this would qualify anyways because a papercut also has to be simple to fix.

---

### Post by Wilbefast on 2009-11-01
That's I shame... guess you're right too. Ah well, nevermind :-S

---

### Post by ad_267 on 2009-11-01
Sorry I can't be more helpful. I've given up on Compiz a long time ago now though. Metacity with compositing enabled gives me window shadows which keeps me happy enough :)

---

