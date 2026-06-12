---
title: "Red dot Ubuntu 10.4"
date: 2010-07-21
forum: General Help
---

### Post by Jimgary on 2010-07-21
I'm getting a red dot on the top panel. On mouseover, it says "An error occurred, please run package manager from the right click menu... This usually means installed packages have unmet dependencies.

If I run package manager (from right click or terminal: sudo apt-get check), it says 0 packages broken.

The dot isn't there on log on. Update manager won't run from System menu, but runs fine from terminal: sudo update-manager

Package manager runs fine from menu.

Nothing seems to be wrong, it's just annoying.

---

### Post by quixote on 2010-07-23
You could try ```
sudo dpkg --configure -a
```but if apt isn't finding any broken packages then neither will this method, probably.  But it may be worth a try.  Those stupid alert buttons, when they're useless, can be quite maddening.

---

### Post by Jimgary on 2010-07-27
No response at all from sudo dpkg --configure -a. I guess that means everything is fine. So, the message says "usually" means I have unmet dependencies. So, if that's not the issue, what else could cause the problem? 

The red dot isn't there at boot up. I assume it shows up when the system tries to check for updates since the only way I can get the gui for update manager to run is to sudo from the console. I wonder what would happen if I quickly ran update manager as soon as I log on? Hmmmm. BRB!!

---

### Post by quixote on 2010-07-27
Yes, sounds like you don't have any obviously broken packages.  Officially, since update-manager is a gui package, you're supposed to use gksudo to run it, rather than plain sudo.  I ran into a problem like this a couple of years ago, where it turned out the issue was some bug in gksudo.  Try running "gksudo update-manager" and see if refuses to start.  That'll mean the problem is somewhere in gksudo.  It doesn't mean I have a clue what you'd do about it... :???:

---

### Post by Jimgary on 2010-07-28
Well, I tried running update manager as soon as I logged on using sudo. Update manager runs fine but red dot appears about 2 minutes after log on so no change in behavior. However, adding gksudo to the command in the gnome administration menu now runs update manager from the menu. Still have no clue what my problem is, my well computer problem anyway!! Other problems are well documented. Ask my wife!! I think she's actually blogging about it now. I think if I just put a little grey dot on my screen I won't see it and everything will be fine!!

---

### Post by quixote on 2010-07-29
(Hey, if the other problems were real problems, she wouldn't be there to ask :biggrin:)

I like the gray dot idea.  Sometimes the best solution is a patch.

---

### Post by Jimgary on 2010-08-01
Or, I can run the same version in a VirtualBox in full screen mode!! It's still frustrating! Guess all I can do is pout!

---

### Post by P4man on 2010-08-01
Go to system > admininstation > synaptic package manager
Filter for broken packages (left panel) and/or run the fix broken packages from the menu

---

### Post by Jimgary on 2010-08-03
Yeah, I thought that would have fixed it, too. But, apparently I don't have a problem with unmet dependencies. So, what else could cause an:

'Unknown Error:'<type 'exceptions.System.Error'>' (E:Opening configuration file /etc/apt/apt/apt.conf.d/99synaptic - ifstream::ifstream (13:Permission denied))'This usually means that your installed packages have unmet dependencies


Error Message.

---

### Post by P4man on 2010-08-03
> **Jimgary said:**
> Yeah, I thought that would have fixed it, too. But, apparently I don't have a problem with unmet dependencies. So, what else could cause an:

'Unknown Error:'<type 'exceptions.System.Error'>' (E:Opening configuration file /etc/apt/apt/apt.conf.d/99synaptic - ifstream::ifstream (13:Permission denied))'This usually means that your installed packages have unmet dependencies


Error Message.

Looks like a permission problem on that file. Try this:

```
sudo chmod o+r /etc/apt/apt.conf.d/99synaptic
```

If that doesnt help, post the output of:

```
ls -l /etc/apt/apt.conf.d/
```

---

### Post by Jimgary on 2010-08-03
Yep, that was it. Found the same problem on a French forum while you were typing! I should have realized that when I had to use sudo/gksudo to run synaptic and update manager I really had a permissions problem. Not the "usually caused by unmet dependencies" message. Had to set

etc/apt/apt.conf.d/99synaptic 

(a plain text file which contains one line: APT::Install-Recommends "true";)

to world readable.

Now, my question is, "What is update manager running as that a file it needs to read has to be set world-readable?

---

