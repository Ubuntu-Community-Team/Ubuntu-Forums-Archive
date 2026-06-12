---
title: "Can't log in!!!!"
date: 2010-05-29
forum: General Help
---

### Post by LePresident on 2010-05-29
I can't log in ubuntu!!!!

Everytime I try to introduce my password the OS takes every single letter as an 'intro'.  If I want to type, for example, 'batman', it will take every single character as an intro and therefore I can't get access to the OS.... what can I do?

Btw, all of this began when I was trying to write something in a console.  When I tried to type anything in the console was like If I was clicking on the 'close window' button, so I though I was a little bug and I had to restart.

HELP! :(

---

### Post by LePresident on 2010-05-29
Please anyone! I'm seriously thinking about reinstalling ubuntu....

---

### Post by CharlesA on 2010-05-29
Sounds like a problem with the keyboard. Does it work fine if you boot off a livecd?

---

### Post by WorMzy on 2010-05-29
Do you mean that every time you type a letter, it replaces the previously typed letter? So if you typed "batman" you'd be left with a "n"?

What command were you running when the problem started?


A reinstall would fix it, but if you know the command that caused the problem, it may be possible to undo the effects.

---

### Post by LePresident on 2010-05-29
> **CharlesA said:**
> Sounds like a problem with the keyboard. Does it work fine if you boot off a livecd?

No problems with the keyboard.  I've just made a test with the live cd and everything worked fine!.  I've even moved some important files from the ubuntu partition to the windows one.

---

### Post by LePresident on 2010-05-29
> **WorMzy said:**
> Do you mean that every time you type a letter, it replaces the previously typed letter? So if you typed "batman" you'd be left with a "n"?

What command were you running when the problem started?


A reinstall would fix it, but if you know the command that caused the problem, it may be possible to undo the effects.

Not exactly that way... let's put it this way: restart ubuntu.  Once you are in the log in screen -where you are asked for your password- then you try to introduce it, but when you type the very first letter of your password, the window starts again and erase anything you had typed.  In other words, is like if you where just pushing the intro button instead of your password! :confused:

And no, is not a hardware issue.  I've tested my keyboard starting ubuntu from a live cd and everything worked fine.

Command? are you talking about a program?  If so, I wasn't executing anything special: mozilla firefox and... that's it.  I was also going to test google earth starting it as a root user because I reinstalled it because an issue with streetview.

---

### Post by WorMzy on 2010-05-29
Did you recently upgrade, enable, or change your video driver?

Try booting into recovery mode (you may need to press Esc or hold Shift during boot, depending on which grub you're using, to access the boot menu), and letting it run any checks you think might help (I can't remember what the recovery options are right now)

---

### Post by LePresident on 2010-05-29
> **WorMzy said:**
> 
What command were you running when the problem started?



Wait a minute! I was doing something else!  I had mounted the Version 2 rosetta stone iso for the Danish language and tried to install it on the version 3 rosetta stone program at wine.  However, I couldn't succeed because the V2 iso's aren't compatible with the V3 rosetta stone program.  Then I explored the .iso and tried to erase a little .exe application to automatically mount the iso in a computer with daemon tools.  However, I couldn't do that either and then all the problems began...

I mounted the .iso in a program called acetone iso 2 or something like that... the icon is like a molecule with 3 purple spheres and a white one.

---

### Post by WorMzy on 2010-05-29
Were you running Daemon tools with Wine too, or did you switch to Windows? :confused:

EDIT: After rereading your post, I think I understand. But I can't see why messing with isos would cause your keyboard or your graphics driver to malfunction, and I think the problem lies in one of these two areas.

---

### Post by LePresident on 2010-05-29
> **WorMzy said:**
> Were you running Daemon tools with Wine too, or did you switch to Windows? :confused:


No no, this little application was inside of the .iso.  I wasn't executing it but however I though maybe it was interfering with acetone iso during the installation of the danish level in rosetta stone, so I tried to delete this little .exe application to see what happened.  Nothing happened but maybe a huge failure... :(

---

### Post by WorMzy on 2010-05-29
I've edited my post, sorry, I'm a little sluggish tonight. I'm not reading things right. :p

Like I said (in my updated post) I believe the problem is with either they keyboard, or more likely, the graphics driver.

Can you tell me if you can press Ctrl+Alt+F1 at the login window, to switch to a tty? If you can, see if you can login and then run "startx" (no quotes). If it works correctly, Ubuntu should bypass the login screen and present you with a usable gnome session. If it doesn't, it'll spurt out an error. Post that here if that's the case.

---

### Post by LePresident on 2010-05-29
> **WorMzy said:**
> I've edited my post, sorry, I'm a little sluggish tonight. I'm not reading things right. :p

Like I said (in my updated post) I believe the problem is with either they keyboard, or more likely, the graphics driver.

Can you tell me if you can press Ctrl+Alt+F1 at the login window, to switch to a tty? If you can, see if you can login and then run "startx" (no quotes). If it works correctly, Ubuntu should bypass the login screen and present you with a usable gnome session. If it doesn't, it'll spurt out an error. Post that here if that's the case.

Ok, I can get into the tty.  Also I can log in, but when I run 'startx' I get the following error:

```
Fatal server error
Server is already active for display 0
     If this server is no longer running, remove  /tmp/.X0-lock

Please, consult the X.Org foundation support at http://wiki.x.org
for help

ddxSigGiveUp: Closing log
Invalid MIT-MAGIC-COOKIE-1 keygivingup

x init: Resource temporarily unavailable (errno11): unable to connect to x server
x init: No such process (errno3): Server error

```

---

### Post by LePresident on 2010-05-29
shall I rm /tmp/.X0-lock ????

---

### Post by WorMzy on 2010-05-30
No, sorry, I forgot to tell you to run 'sudo stop gdm' first.

---

