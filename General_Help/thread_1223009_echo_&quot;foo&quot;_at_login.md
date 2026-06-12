---
title: "echo &quot;foo&quot; at login?"
date: 2009-07-25
forum: General Help
---

### Post by bjdonhauser on 2009-07-25
How would I get my bash terminal to open automatically on login and have "foo" echoed in it?

I tried adding:

$ echo foo

at the end of my ~/.profile. Didn't work. I then tried adding:

$ bash echo foo

That didn't work either. 

I'm a complete noob and just trying to learn my way around :)

P.S. I'm running Ubuntu 9.0.4

---

### Post by madsmeg on 2009-07-26
instead of just ```
echo foo
```

try ```
gnome-terminal | echo foo
```

I cannot try this at present as i am at work on Windows.

---

### Post by Johnny B on 2009-07-26
put "echo foo" at the bottom of ~/.bashrc

---

### Post by DaithiF on 2009-07-26
Do as Johnny B suggested, and add gnome-terminal to your list of startup applications, System->Preferences->Startup applications

---

### Post by bjdonhauser on 2009-07-27
> **madsmeg said:**
> instead of just ```
echo foo
```try ```
gnome-terminal | echo foo
```I cannot try this at present as i am at work on Windows.

So, this didn't work either. I even tried adding the full path "/usr/bin/gnome-terminal". 

Q: Does this mean that certain applications are closed when ~/.profile has finished running?

Maybe that's what's going on. gnome-terminal is actually run, but then is shut down before the system goes on to run /etc/bashrc and ~/.bashrc.

---

### Post by bjdonhauser on 2009-07-27
> **DaithiF said:**
> Do as Johnny B suggested, and add gnome-terminal to your list of startup applications, System->Preferences->Startup applications

Thanks! So this definitely works.

Funny: I was playing around and added "gnome-terminal" to the end of ~/.bashrc. Should've seen this one coming. Big mistake. gnome-terminal just ends up being called ad infinitum :)

Q: Which file is actually being modified when you, say, add the "gnome-terminal" command to System -> Preferences -> Startup applications?

---

### Post by DaithiF on 2009-07-27
> **bjdonhauser said:**
> 
Q: Which file is actually being modified when you, say, add the "gnome-terminal" command to System -> Preferences -> Startup applications?
I believe either ~/.config/autostart  OR /etc/xdg/autostart, depending on whether the app should start for everyone or specifically for your user.

Regarding your earlier question about why this:
```
gnome-terminal | echo foo
```
doesn't work, well it doesn't really make sense -- it says to run gnome-terminal and pipe its stdout output into the echo command.  gnome-terminal is a graphical application which will open a new window, its not going to pipe anything useful into echo.  So if the intention was to get foo to appear in the (new) gnome-terminal, then this suggestion was going in the wrong direction.

cheers
d

---

### Post by bjdonhauser on 2009-08-01
> **DaithiF said:**
> I believe either ~/.config/autostart  OR /etc/xdg/autostart, depending on whether the app should start for everyone or specifically for your user.


right. "gnome-terminal.desktop" was added to the ~/.config/autostart directory as a text file with a particular setup that the system reads on login i guess. thanks for the help!

---

