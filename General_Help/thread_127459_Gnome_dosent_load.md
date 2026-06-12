---
title: "Gnome dosent load"
date: 2006-02-09
forum: General Help
---

### Post by 3dmaker on 2006-02-09
My gnome seems to freeze when it says Loading Metacity packages or whatever.. I tried using Gnome Failsafe. That worked fine. Whats going on with the normal gnome?

---

### Post by Mustard on 2006-02-09
I would try cd'ing to your $HOME directory and making sure that the .Xauthority file is not owned by root now.

---

### Post by 3dmaker on 2006-02-09
If it is how do I change it? 
chmod what?
I only know 777 :D

---

### Post by Zeroangel on 2006-02-09
```
chown yourusername
```
That changes the file's owner.

chmod 777 gives read, write, and execute access to everyone, and is little more then a temporary hack (for if you can't yet remember the chmod numbers and syntax like I do) until you can get into the GUI and change it using the menus.

---

### Post by Mustard on 2006-02-09
I believe you can just delete them with the rm command to fix it.

This is the advice from the help bot on the IRC support channel....

[quote=ubotu] If the GUI hangs after logging in, use <ctrl><alt><f1> to switch to text mode. Log in and do: rm .{X,ICE}authority[/quote]

This is specifically for the problem of Xauthority/ ICEauthority being changed to ownership by root, usually because a graphical application was run with sudo rather than gksudo.  Some graphical apps are ok, but for a number of graphical apps, if you run them with sudo then this problem can occur.  For example, gedit doesnt seem to mind just using sudo (when editing system files), or synaptic seems to work fine with sudo.  For anything else I would tend to use gksudo.

This might not be your specific problem, but it sounds like its a possibility.  You have described a 'freezing' symptom.

---

### Post by 3dmaker on 2006-02-09
I have tried everything listed here. Still no luck I think one of the startup scripts are broken. Because Failsafe Gnome loads fine in Failsafe which is without the startup scripts. How do I check wich scripts load at startup and how do I change them?

---

### Post by Mustard on 2006-02-09
Have you gone through your logs at all looking for potential clues?
What is coming up in your /var/log/Xorg.0.log?

---

### Post by 3dmaker on 2006-02-09
Unfortunately when the loader freezes at Metacity Window Manager no log is created

---

