---
title: "locked up on updates last night, what do I do?"
date: 2006-05-05
forum: General Help
---

### Post by txinga on 2006-05-05
When I got home from work yesterday, the system showed 69 updates were available. So, I started off the update manager and went to bed. When I awoke this morning the system is completely frozen. The "Applying Changes" window is up. It looks like it's about 95% done. The part that it's stuck on is: "configuring linux-image-2.6.12.10-386." I have no mouse or keyboard functions. 
What do I do here? Should I just power off the system and hope it comes back? There doesn't appear to be any drive activity.
Thanks,
txinga

---

### Post by jazzmuzik on 2006-05-05
Can you Ctrl-Alt-F1 and login? From there you could 'reboot'. Or do a 'ps aux' and kill any frozen processes.

---

### Post by txinga on 2006-05-05
Unfortunately, the keyboard and mouse are locked up.

---

### Post by Sef on 2006-05-05
> Should I just power off the system and hope it comes back? 

Sometimes that is the only thing to do.  If you have trouble booting in, then you may want to go into grub and set an older kernel to boot.  If you can't update at all, use the Terminal (Applications > Accessories > Terminal) and type 'sudo apt-get update'. It will like give you a message that it can't and tell you what to do.  The message will say something like 'dpkg --configure -a'.  Just type that in the terminal and all should be ok after it finishes.

---

### Post by txinga on 2006-05-05
OK. Powered off the system and it came back to life. Yea! Thanks folks

---

### Post by jazzmuzik on 2006-05-05
[QUOTE=txinga]OK. Powered off the system and it came back to life. Yea! Thanks folks[/QUOTE]

One of the good things about ext3 is that it fixes 99.9% of disk problems when you have to reboot after a lockup like that. Still, total lockups remind me of Microsoft and unfortunately something I'm seeing more of in Linux.

---

### Post by henriquemaia on 2006-05-05
[QUOTE=jazzmuzik][...] Still, total lockups remind me of Microsoft and unfortunately something I'm seeing more of in Linux.[/QUOTE]

If I may ask, does this means that you have been having lockups or are you referring to others experiences as well?

I just got curious, because there are a lot of reasons one can think about this potencial lockups rising on Linux. The first one that I think is that Linux is getting a lot of attention and, as a result of that, you have Linux being used (and tested) under a lot more hardware combinations and some may not be the best ones to it - one can find that its hardware is not totally supported under Linux, as by the community or by the vendors, etc.

---

### Post by jazzmuzik on 2006-05-05
I'm experiencing freezing a lot more than I used to. But as you say there are many hardware combinations, plus I'm using Linux in more complex way as my knowledge of how to accomplish things grows. Still, one would hope that X would not completely lock up.

---

### Post by Ramses de Norre on 2006-05-05
I think the safest thing to do when you've got updates for X and kernel and things like that is to go to a tty, kill gdm and run the updates from cli. Then reboot.
You're problem is probably related to X searching for files that have been changed or moved by the update.

---

### Post by jazzmuzik on 2006-05-05
What is gdm and cli?

---

### Post by Ramses de Norre on 2006-05-05
gdm: Gnome Display Manager, when you kill this your xsession will be killed. So you wont end up with X searching for files that are changed by the update (to kill it: sudo /etc/init.d/gdm stop)

cli: Command Line Interface: just the console;) an abreveation like gui for Graphical User Interface.

---

### Post by jazzmuzik on 2006-05-05
Are gdm and x separate? So if I kill gdm would that take me to the main login screen or out of x completely?

---

### Post by henriquemaia on 2006-05-05
GDM and X are different things. GDM run on top of X. The X server draws the graphical screen and GDM manages logins using Gnome's environment. You can have X running and no login screen (GDM). 

On a command line, type:

```
sudo xinit -- :2
```

It will open another instance of X, with xterminal running. To quit that and return to your default desktop, type exit if the xterminal (if available). If there's not terminal in it, press **ctrl+alt+backspace**.

---

