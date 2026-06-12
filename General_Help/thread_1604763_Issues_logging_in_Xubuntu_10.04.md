---
title: "Issues logging in Xubuntu 10.04"
date: 2010-10-24
forum: General Help
---

### Post by PruritusAni on 2010-10-24
[SIZE=2]I am quite new to this ubuntu business, but i like what I'm seeing so far. Well, almost everything that I'm seeing. I seem to have run into a tricky problem with xubuntu 10.04.

I was in the process of customizing my desktop appearance (via Xfce4 Settings manager), and I found a nice theme to go with (dusk I think it was called). I then went on to change the window settings and starting from the bottom most option i browsed the various styles. After a few of these my computer decided to log me out quite suddenly, and I was prompted to login.

This is where the problem is: I type in my password and it logs me in for maybe a half a second only to log me out again. no matter how many times i put in the password i keep getting logged out. So now I'm running xubuntu 10.04 off a pendrive that was used in its initial installation. Is there any way to log back in and stay logged in long enough to undo the window styling at fault? I had put in quite a bit of work migrating files, installing all sorts of things and setting up fancy launchers, and I would prefer not to have to redo it again.[/SIZE]

---

### Post by katykat on 2010-10-24
I am havign a similar prolem with Meerkat. 

If I try to log in as a regular user it kicks me out. 
Some type of problem with PAM. 

I can log in fine as root however, so it is not a high priority for me at the moment, especially as I am still configuring the system. 

CTRL-ALT-F1 and when logging in - note and post the error messages.

Then see if logging in as root helps.

---

### Post by PruritusAni on 2010-10-24
ok so ctrl+alt+f1 got me to a console like login screen. I logged in just fine, and no errors occurred. I was then stuck in that console with not too much of an idea as to what to do next. Well I think the idea is that I want to change the window settings back to default from this console and then see if that fixes things, but i don't know where to even start doing that.

Oh, and I have no idea how to log in as root. I may not have stressed my lack of ubuntu wherewith-all enough.

EDIT: I did manage to figure out the login as root thing, and it did indeed let me log in.


EDIT2: I have become legendary! I managed to get the same issue as root! So now it keeps logging me out of root as well. :facepalm:

It turns out that the window manager style wildbush is the one causing the problem. So I recommend no one use that particular style as it is problematic.


EDIT3: I gave up, and am in the process of reinstalling xubuntu. I absolutely hate my stupidity ...

---

### Post by liatodua on 2011-04-20
I am having the same problem with Xubuntu 10.10. After selecting wildbush I was thrown out of the system and could not log in anymore. I could find no other solution but to to reinstall xubuntu.

Will anybody please remove this damned **wildbush **from the window manager themes of xfce?

---

