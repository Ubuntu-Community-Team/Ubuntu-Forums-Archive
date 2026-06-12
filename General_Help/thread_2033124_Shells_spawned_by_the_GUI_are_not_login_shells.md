---
title: "Shells spawned by the GUI are not login shells"
date: 2012-07-25
forum: General Help
---

### Post by ArlieS on 2012-07-25
I've got a desktop installation, but I'm a unix user, not a PC user, so I do most things from shell (xterm) windows. 

Unfortunately, when I launch a window from the (unity) GUI, using the "dash" to select xterm (is there a better way?) I don't have my normal environment variables, because my .bash_profile was never run. 

Having to remember to type ". .bash_profile" in the first such window (and launch all other xterms from the first one)  is a nuisance. How do I convince the GUI to give me a normal login shell, in a convenient window? 

I'm running Ubuntu 12.04, pre-installed by system 76.

---

### Post by nkbielst on 2012-07-25
A couple of ideas come to mind:

-Have you tried regular gnome terminal? CTL+ALT+t will bring it up, or find it in Accessories menu. I'm not sure this will solve the problem, but xterm seems quite stripped down, comparitively.

-Could also try CTL+ALT+F1, it will switch to tty1. Command-line-only login shell. CTL+ALT+F7 will bring you back to the gui.

Good luck.

---

### Post by steeldriver on 2012-07-25
I may be wrong but I believe the recommended way to handle this is to move all your custom environment stuff into ~/.bashrc (so that it's read when you start a non-login shell), then change your ~/.bash_profile to source your .bashrc for the occasions when you start a login shell

in ~/.bash_profile:
```
if [ -f ~/.bashrc ]; then
    source ~/.bashrc 
fi
```

---

### Post by ArlieS on 2012-07-26
After some reading of man pages, it looks like "xterm -ls" will do what I  want, except that passing arguments to programs launched from unity  requires creating something called a "launcher". (I'm not really clear on what that is; I suspect it's the equivalent of a complex shortcut in windows, the kind where one uses "properties" to specify things like the environment in which the program runs.) The man page says I can get the  same effect by setting the "loginShell resource". I presume this is an X  resource, and I'm rather unclear on how or where to set such things, or whether it would have side effects on e.g. other shells.

---

### Post by ArlieS on 2012-07-26
> **steeldriver said:**
> I may be wrong but I believe the recommended way to handle this is to move all your custom environment stuff into ~/.bashrc (so that it's read when you start a non-login shell), then change your ~/.bash_profile to source your .bashrc for the occasions when you start a login shell

in ~/.bash_profile:
```
if [ -f ~/.bashrc ]; then
    source ~/.bashrc 
fi
```

That would get me the equivalent of login shells without explicitly sourcing .bash_profile each time.

My concern with it is that shell scripts also pick up the contents of .bashrc, which may have unexpected results.

---

### Post by ArlieS on 2012-07-26
> **nkbielst said:**
> A couple of ideas come to mind:

-Have you tried regular gnome terminal? CTL+ALT+t will bring it up, or find it in Accessories menu. I'm not sure this will solve the problem, but xterm seems quite stripped down, comparitively.



I didn't know a thing about gnome terminal. Nice to have a keyboard shortcut for spawning a shell window; from my POV that's even better than an icon I can simply click on. (Unfortunately it isn't a login shell, but having a keyboard shortcut is nice.) 

With an old fashioned X environment, I'd simply put an appropriately parameterized xterm into a menu, or make it an auto-start item. Then I'd spawn other xterms from the initial one, so they inherit that first login shell's environment. Realistically, I wouldn't even have to do this myself - there'd be a terminal window of some kind in the default menu. 

But AFAIK, the last window manager which I could conveniently control this way was twm - kde, gnome, unity and others all want to treat me like a clueless windows user, incapable of understanding anything except icons and mouse clicks. Configuration files are far too complex for their target audiences, so even if there's a config file under the covers, the GUI owns it, edits it at will, and probably wipes out user customizations regularly. At the very least, it lacks the kind of helpful hints that made it easy for me to figure out the latest features of /etc/fstab.  Given that I never had a deep understanding of X configuration, once the helpful comments and man pages disappear, I'm mostly stuck. 

More importantly - and less sulkily - gnome terminal gives me something else to try to get around [http://ubuntuforums.org/showthread.php?t=2032899](http://ubuntuforums.org/showthread.php?t=2032899) 

> 
-Could also try CTL+ALT+F1, it will switch to tty1. Command-line-only login shell. CTL+ALT+F7 will bring you back to the gui.

Good luck.The ability to switch screens is still there? That's great to know. I used to mess up my X configuration regularly, and wind up using an alternate screen to run dpkg-reconfigure, or worse ;-) 

Anyway, I think I may be on the way to a solution.

---

### Post by ArlieS on 2012-07-26
> **ArlieS said:**
> I didn't know a thing about gnome terminal. Nice to have a keyboard shortcut for spawning a shell window; from my POV that's even better than an icon I can simply click on. (Unfortunately it isn't a login shell, but having a keyboard shortcut is nice.) 


Aha - gnome terminal has a preferences menu, and one of the options is to make it a login shell. 

This looks like a lot less trouble than figuring out launchers. 

Now I just need to train my fingers to type CTRL-ALT-t when I want a shell window. 

Thank you very much!

---

### Post by ArlieS on 2012-07-26
> **ArlieS said:**
> Now I just need to train my fingers to type CTRL-ALT-t when I want a shell window. 


I didn't even have to do that. I've now got an icon for gnome terminal in that bar on the left side of the Unity  screen (can't remember what it's called) that mixes shortcuts-to-launch-things with showing what's currently running. If I've figured that out correctly, it will stay there, right beside firefox.

---

### Post by nkbielst on 2012-07-26
> **ArlieS said:**
> Aha - gnome terminal has a preferences menu, and one of the options is to make it a login shell. 

This looks like a lot less trouble than figuring out launchers. 

Now I just need to train my fingers to type CTRL-ALT-t when I want a shell window. 

Thank you very much!
You're welcome. I'm glad I could help.

---

