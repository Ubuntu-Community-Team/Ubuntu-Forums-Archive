---
title: "Help! Can't start session on Karmic!"
date: 2009-11-19
forum: General Help
---

### Post by GonzalitoUY on 2009-11-19
Noob here, so I'll try to explain my problem as accurate as possible.
Been using Ubuntu for a couple of years, and updated to Karmic as soon as it got out.
But today, after working normally on the morning, when I booted up my laptop, all was normal,until the user selection screen, where I put my password as usual, but when my session is starting (welcome sound and everything), it goes black, and get back to user selection screen?
I can boot on safe mode, and currently writing from Guest session, but don't have the slightest clue of what happened.
The only thing that comes to my mind, is that the system updated as usual, but nothing big (no kernell or anything).
Any ideas on how to restore normal access to my session?

---

### Post by Giblet5 on 2009-11-19
You might want to write this down...

Flip to the text console via Ctrl+Alt+F1 and log in.

Enter: ```
mkdir dotback
mv .gconf* .config dotback
mv .kde dotback
exit
```

Now flip back to the graphic screen via Ctrl+Alt+F7 and log in.

Note that just about everything is the Karmic default. But at least it works, right?

All of your prior settings have been saved in ~/dotback/* so you haven't exactly lost anything.

---

### Post by GonzalitoUY on 2009-11-19
I tried what you told me, but despite having resetted all graphics preferences, the desktops shows for a moment, and then it goes black,logs out and goes back to login screen.
Any more ideas? Isn't there any log that should tell me what's going on?

---

### Post by Giblet5 on 2009-11-19
Past errors will have been logged to:
/var/log/Xorg.0.log.old
~/.xsession-errors

You can move your old config stuff back too:

From the console:
```
mkdir dotnew
mv .gconf* .config dotnew
mv .kde dotnew
mv dotback/.* $HOME
```

That'll save you some setup after this is resolved.

Now you can try doing what recovery mode's "xfix" solution did on earlier releases:

From the text console: ```
sudo /etc/init.d/gdm stop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old ## remember and post if there's an error here
sudo /etc/init.d/gdm start ; exit
```

And try to log in.


> I tried what you told me, but despite having resetted all graphics preferences, the desktops shows for a moment, and then it goes black,logs out and goes back to login screen.
Any more ideas? Isn't there any log that should tell me what's going on?

I would expect it to work. Did you provide the exact commands, paying attention to leading '.'s in the filenames?

Those commands eliminate any and all session customizations.

Did you try logging in in failsafe mode?

Did you try explicitly selecting a Gnome session?

---

### Post by GonzalitoUY on 2009-11-20
I've solved the problem somehow, the cause was xorg-edgers package, and after uninstallling and reconfig, all seemed well,but when I try to restore my old settings, it fails at the ```
mv dotback/.* $HOME
```, the output says something like "can't move...device or ressource busy" (trenslated from spanish).
Also, even if I got Karmnic defaults looks, if I change anything (or connect to WiFI), the changes or password don't seem lo be remembered when I restart.
Anyway, something is something,but the last yhing intrigues me

---

### Post by Giblet5 on 2009-11-20
It's important to do the entire process on that move and not just part...

The dotback folder will be in an unknown state now: part there part not.

Have you been running gui applications as root? It is possible that you don't own everything in your home directory.

Here's a one-liner that will set reasonable permissions on your home directory, allowing you to save config changes from session to session:

```
sudo find $HOME -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; sudo find $HOME -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
```

It may hiccup twice on ~/.gvfs (OK) and it will take a minute or three to run. I recommend logging off when it's done and logging in again. Now, any changes you make will stick.

---

### Post by GonzalitoUY on 2009-11-20
On the dotback part, I did all the steps on the recovery you suggested, always the same result (I did the backup, and it's there on my home folder).
On the oneliner, after it ask for my password it says something like (TRANSLATED FROM SPANISH)
```

find: routes must belong to expression: sudo
Use: find [-H] (bla bla)

```

---

### Post by GonzalitoUY on 2009-11-20
Look I somewhat messed up with my backup, but after looking a litlle bit, for the moment my changes are saved, so we can tag this as solved.
Thanks for the help

---

### Post by teodosio on 2009-12-31
Thanks Giblet. You could solve my problem!

---

