---
title: "Start directory in bash is ~/Desktop?"
date: 2010-03-20
forum: General Help
---

### Post by jdege on 2010-03-20
I'm playing around with Ubuntu for the first time.  I'm running 9.10.

When I open a new xterminal, my initial working dir is ~/Desktop.  This drives me crazy.  I spent 20 minutes trying to figure out why fetchmail wasn't working before I realized that I had .fetchmailrc in the wrong directory.

I had figured that there would be something in /etc/profile or ~/.profile or ~/.bashrc that was causing this behavior.  After all, my home dir is still set to ~, and a "cd" will put me there.  But if it's there, I can't find it.

Where is this behavior being defined, so I can turn it off?

---

### Post by kerry_s on 2010-03-20
is your launcher for xterminal on the desktop?

---

### Post by jdege on 2010-03-20
I usually use the Nautilus right-mouse menu.  It could be that the current directory is set to ~/Desktop only because it's inherited from the launching app.  I hadn't thought of that.

---

### Post by d3v1150m471c on 2010-03-20
The default directory is your home folder. ~/ or /home/$LOGNAME/ . If you're creating a custom launcher, a script has to first be given executable permission by checking it in the file's properties or by using chmod. A launcher will not launch a terminal or a gui if it is not written as a gui or specified to launch in a terminal.

---

### Post by PC_load_letter on 2010-03-20
> **jdege said:**
> I usually use the Nautilus right-mouse menu.  It could be that the current directory is set to ~/Desktop only because it's inherited from the launching app.  I hadn't thought of that.

It's a feature not a bug :D The open terminal in the right-click menu opens the terminal in the same directory as where you clicked.
So, if you right-clicked in a different directory, say /home/User/Music terminal will start there.

---

### Post by jdege on 2010-03-20
> **PC_load_letter said:**
> It's a feature not a bug :D The open terminal in the right-click menu opens the terminal in the same directory as where you clicked.
So, if you right-clicked in a different directory, say /home/User/Music terminal will start there.
Yep.  That's exactly the behavior I'm seeing.  And I can see the logic, and I can entirely disagree that it is the correct behavior.

---

### Post by PC_load_letter on 2010-03-20
> **jdege said:**
> Yep.  That's exactly the behavior I'm seeing.  And I can see the logic, and I can entirely disagree that it is the correct behavior.

What do you mean? You mean you still find it inconvenient? 
How about a keyboard shortcut? Open System > Preferences > Keyboard shortcuts. Scroll down to the Desktop category and a little more to find "Run a terminal", choose whatever shortcut that you like, I have it set up with CTRL+ALT+T.

---

### Post by jdege on 2010-03-20
> **PC_load_letter said:**
> What do you mean? You mean you still find it inconvenient?
I mean that when I open a terminal, I expect to start in my home directory. I can see how people who use the command-line in a different way than I usually do might like this "feature".  For me, it just gets in the way.

Still, it's easy enough to fix.  One line in .bashrc will put the current directory where it is supposed to be.

---

### Post by PC_load_letter on 2010-03-21
Sure, I understand, and for me it's really a great feature since it allows me to get in many folders and still use shell commands without too much hassle in navigation. Otherwise, I just use the keyboard shortcut.

IIRC, the terminal in the right-click menu was designed to behave exactly this way, the way you do not like, and it's not installed by default, to get it you have to install the package: nautilus-open-terminal

So, now I'm a little skeptical if a change in .bashrc will neutralize the behavior of above package, do you mind sharing the details?

---

### Post by kerry_s on 2010-03-21
i would just go with a nautilus script for that kind of behavior.

something like;
```
#!/bin/bash
gnome-terminal ~/
```

---

### Post by 3rdalbum on 2010-03-21
> **jdege said:**
> Yep.  That's exactly the behavior I'm seeing.  And I can see the logic, and I can entirely disagree that it is the correct behavior.

We'll have to agree to disagree then. It's called "Open in Terminal", not "Open Terminal". In other words, it is opening 'something' in the terminal; and that 'something' is the folder you've clicked on (in this case, the desktop).

If I want to open a terminal in my home directory, I click on the launcher in my top panel.

---

### Post by jdege on 2010-03-21
> **PC_load_letter said:**
> So, now I'm a little skeptical if a change in .bashrc will neutralize the behavior of above package, do you mind sharing the details?
.bashrc is run every time an interactive but non-login shell is opened.  In other words, it's run when you open an terminal using Nautilus.

So, add a last line in .bashrc, that does a "cd $HOME".

---

