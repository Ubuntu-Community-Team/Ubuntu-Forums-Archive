---
title: "gnome-do not loading at start-up"
date: 2010-01-04
forum: General Help
---

### Post by sjnims on 2010-01-04
Hey folks,

I'm having trouble getting gnome-do to load at start-up and cannot figure it out...running Karmic w/ compiz

When starting from the CLI I get the following output:

```
steve@McLovin:~$ gnome-do

(/usr/lib/gnome-do/Do.exe:2780): GLib-WARNING **: g_set_prgname() called multiple times

(/usr/lib/gnome-do/Do.exe:2780): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

Could not locate Tomboy on D-Bus. Perhaps it's not running?

```

I've already tried using a script that waits for a specified number of seconds before trying to start the application, any ideas?

---

### Post by jamesisin on 2010-01-04
Does gnome-do not run ever then?  You can't start it manually?

What is the relationship between gnome-do and Tomboy?

---

### Post by sjnims on 2010-01-04
no idea about how tomboy and gnome-do are related...however i can start gnome-do via the menu or cli

---

### Post by jamesisin on 2010-01-04
How did you go about setting up gnome-do to auto-start?  Did you use gnome-do's preferences or did you create an entry in the start-up yourself?

---

### Post by sjnims on 2010-01-04
I've tried both

---

### Post by jamesisin on 2010-01-04
Anything else in startup that might be conflicting with gnome-do?

I don't get any errors when I run gnome-do from the command line, and I don't think there is any necessary connection between gnome-do and Tomboy.  This is an odd message to see.

---

### Post by jager_nl on 2010-01-09
sjnims,

From the error message it looks like gnome-do was already running, just not responding.

As to Tomboy - my version (0.8.2) has a Tomboy plugin you can select in preferences. I got the same message, but it stopped after deselecting this plugin.

HTH

---

### Post by jamesisin on 2010-01-09
You say that because of the "called multiple times" error?  I suppose that might be due to it being in both the Start Up items and being called from its own preferences.

I'd say choose the Preferences option (only) and then start up your system.  If Gnome-Do does not appear (I set mine to show the notification icon and silent first-run), then check the System Monitor (or top or ps) to see if it is running at all.

I am running the Tomboy plugin as well.  I don't get the error though.  Maybe try disabling, restarting, and re-enabling that plugin (but after you get this other issue sorted out).

---

### Post by llawwehttam on 2010-01-09
With conky I have to use a .sh script to launch it 10 seconds after login.

```
#!/bin/sh
sleep 15; conky
```

You could probably use it but instead of conky type gnome-do.

Then add an entry for it in startup programs.

---

### Post by jager_nl on 2010-01-13
> **jamesisin said:**
> You say that because of the "called multiple times" error?  I suppose that might be due to it being in both the Start Up items and being called from its own preferences.


Yes, but I was wrong:

```
willem@donut:~$ ps aux | grep gnome-do
willem    2263  0.0  0.0   3040   792 pts/2    S+   00:41   0:00 grep gnome-do
willem@donut:~$ gnome-do

(/usr/lib/gnome-do/Do.exe:2302): GLib-WARNING **: g_set_prgname() called multiple times

(/usr/lib/gnome-do/Do.exe:2302): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.
```

I get the called multiple times messages even when starting gnome-do the very first time. Clearly it is not related to starting gnome_do multiple times.

As to the Tomboy message ("Could not locate Tomboy on D-Bus. Perhaps it's not running?"), I get those repeatedly when Tomboy is not running and the gnome-do Tomboy plugin is selected. Lots of them in .xsession-errors. Does not seem relevant to the original problem.

So - I do not have a solution yet, only negative results, unfortunately.

---

### Post by jamesisin on 2010-01-14
I suppose you could try purging and reinstalling Tomboy in case something connecting them is in fact causing the problem.  (Grasping at straws, of course.)

---

### Post by llamallama on 2010-02-22
I was having this issue and found a way around it. Try this.

In /usr/local/bin create a file called launch-gnome-do. In that file enter:

#!/bin/bash
sleep 15
gnome-do

After that, go to System->Preferences->Startup Applications and add an entry with that runs the command "/usr/local/bin/launch-gnome-do"

I hope this helps.

---

### Post by ghostborg on 2010-02-26
I have the same problem but mine started with the fact that I am running Ubuntu 10.04 Lucid Lynx Alpha 3.

I'm hoping it will work itself out soon.

I just dragged(left click-hold) the icon from the accessories menu to the top panel and just click on the Gnome Do icon after a restart.

Found this info about Gnome Do separating the Dock and Do.[http://tecverse.com/software/a-look-at-docky-post-do-divorce.html]("http://tecverse.com/software/a-look-at-docky-post-do-divorce.html")

I had to reload Synaptic before docky was available for install.
Did not solve the loading problem but docky looks cool.
Both Gnome Do and Docky will not work at the same time, one will just sleep in the background.

---

