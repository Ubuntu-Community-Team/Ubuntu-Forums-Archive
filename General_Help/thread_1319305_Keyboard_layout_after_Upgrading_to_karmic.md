---
title: "Keyboard layout after Upgrading to karmic"
date: 2009-11-08
forum: General Help
---

### Post by orduek on 2009-11-08
Hi,
I had a nice working installation of Ubuntu 9.04.
I use two languages in my keyboard and after upgrading to 9.10 a need to reset the default settings if my keyboard every startup in order to have two languages.
Its weird because it seems as if the default settings are good, but for some reason, every login uses only the US keyboard.

---

### Post by Osama3bbas on 2009-11-10
Same here!

I have upgraded Ubuntu 9.04 to 9.10

I have 4 accounts in the system. Only my account has this problem!

What is the solution?

---

### Post by Dale Gerdemann on 2009-11-10
I have the same problem. Maybe there's a solution with setxkbmap or xmodmap, but I haven't found it yet.

---

### Post by Osama3bbas on 2009-11-11
Is there any solution?

---

### Post by orduek on 2009-11-23
up.

---

### Post by Ludachrispeed on 2009-11-23
Are you asking about how to get several layouts on your computer?  I have QWERTY, Dvorak, and German layouts installed, and I can toggle between them by pressing both Shifts at the same time.

I added new layouts using System -> Preferences -> Keyboard -> Layouts

and changed how to toggle between them using System -> Preferences -> Keyboard -> Layouts -> Layout Options -> Key(s) to change layout

I don't need to redo this every time, only once.  Are you saying that you did this, but when you restart your computer, you have to do it again?

---

### Post by orduek on 2009-11-23
> **Ludachrispeed said:**
> Are you asking about how to get several layouts on your computer?  I have QWERTY, Dvorak, and German layouts installed, and I can toggle between them by pressing both Shifts at the same time.

I added new layouts using System -> Preferences -> Keyboard -> Layouts

and changed how to toggle between them using System -> Preferences -> Keyboard -> Layouts -> Layout Options -> Key(s) to change layout

I don't need to redo this every time, only once.  Are you saying that you did this, but when you restart your computer, you have to do it again?

exactly.
after restart it goes back to one layout.

---

### Post by Ludachrispeed on 2009-11-23
Well that sounds terrible. Maybe try

```

sudo gnome-keyboard-properties

```

and do the same thing, as a superuser.

---

### Post by orduek on 2009-11-24
Didn't help.
Actually, as a superuser I already have the two layouts. 
But seems like I need to define these layouts to be permanent to all users or something.

---

### Post by ushills on 2009-11-30
I have exactly the same problem, I can set dvorak as the default keyboard but on new login the persistance of the keyboard layout is lost and I need to reselect dvorak as the default layout.

This was not a problem with the 9.04 but is a major problem with 9.10 and multiple users with different keyboard layouts.

Should we raise a bug!

---

### Post by Ludachrispeed on 2009-11-30
Ah, I take back what I said before; I did not set Dvorak as my default using the gnome-keyboard-properties program... Dvorak IS my system keyboard layout (selected as default during installation... so I enter my username and password in Dvorak when I log in).  That's why it's persistent.

So, this apparently is a bug.

---

### Post by Osama3bbas on 2009-12-06
> **Ludachrispeed said:**
> 
So, this apparently is a bug.

I think so. This is a bug.

I have the same problem in another PC. Netbook actually.

My default layout is English. Other one is Arabic/QWERTY which I need to add it every login!

How could we tell Ubuntu-Developers about this?

---

### Post by Ludachrispeed on 2009-12-07
I've seen several bug reports on launchpad about this general topic -- for example, even though Dvorak is my system keyboard layout, I still have to use the QWERTY "c" when I type "ctrl-c" in the terminal to stop a program.  Same with all control characters.

@orduek: All I can suggest is looking up how to make the xmodmap program load a new configuration file at startup. It would look something like this:

[http://www.mit.edu/~jcb/Dvorak/dvorak-keyboard.txt]("http://www.mit.edu/~jcb/Dvorak/dvorak-keyboard.txt")

As an example, I have the following saved in my home directory as ".Xmodmap", and if I remember correctly, Ubuntu asked me on the next reboot whether I wanted to run it automatically at startup (may be wrong about that though... I can't totally remember how I got it to run automatically).  It simply switches the Caps Lock and Control keys.

```
! Switch caps lock and left control
remove Lock = Caps_Lock
remove Control = Control_L
keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
add Lock = Caps_Lock
add Control = Control_L

```

---

### Post by StuartN on 2009-12-07
I set up a dual-keyboard 9.10 recently without any problem.

However, when discussing a difficult keyboard issue in an earlier thread, it turned out that the problem only existed for uid=1000 (the first account). All subsequent accounts were fine.

If you add a new account, does the keyboard behave correctly? I know it is a workaround and not a fix, but it may be the quickest solution.

---

### Post by nyarlathotep77 on 2009-12-28
Same with my Karmic workstation.

I want Italian layout and at every system start I need to reset the Italian layout from the US layout.

From the menu System->Preference->Keyboard I have two layouts> Italian and US, where the Italian one is even set as default.
If I remove the US layout I'll find it there again at the next reboot.

Related bug can be found at [here]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/401497")

---

### Post by nyarlathotep77 on 2009-12-28
In my case I've just found out the problem is related to autologin.

I tried by terminating the session (System-> Terminate Session), re-logging in by typing the password and the Italian layout was already set, great!!!

Then I restarted and even with autologin the keyboard layout was still set correctly to Italian, so it was like by logging off the keyboard setting got stored permanently somehow.

Hopefully this may help someone.

---

