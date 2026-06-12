---
title: "Unable to login"
date: 2010-06-25
forum: General Help
---

### Post by putnam120 on 2010-06-25
I am running Ubuntu 10.04 from an external hard drive.  I am able to get to the GUI login and enter the correct user/password combination.  However, one I push enter it cuts away to a blank screen then returns to the login screen as if nothing happened.  This doesn't happen if I log in without GUI (using alt+ctrl+f1 (or any other function key but 7).

Can someone tell me what is going wrong?  I am still able to access my files from the hard drive by booting from a live CD if that matters at all.

---

### Post by sikander3786 on 2010-06-25
> **putnam120 said:**
> I am running Ubuntu 10.04 from an external hard drive.  I am able to get to the GUI login and enter the correct user/password combination.  However, one I push enter it cuts away to a blank screen then returns to the login screen as if nothing happened.  This doesn't happen if I log in without GUI (using alt+ctrl+f1 (or any other function key but 7).

Can someone tell me what is going wrong?  I am still able to access my files from the hard drive by booting from a live CD if that matters at all.

Hi.

Are you using Gnome? Under session list, there should be failsafe-gnome session. Have you tried it?

---

### Post by putnam120 on 2010-06-25
Yes I am using GNOME.  I haven't tried using failsafe-gnome session, where do I find the session list?

---

### Post by cryptotheslow on 2010-06-25
At the bottom of the screen where you login, the selection options will appear once you have selected which user to login.

---

### Post by putnam120 on 2010-06-25
I tried to select the failsafe mode, however, after I entered my username there was no option for what kind of session I wanted to start.

---

### Post by sikander3786 on 2010-06-26
Click on your user name. Don't enter the password. First select failsafe-gnome from sessions in the nearly right bottom of the screen, then enter password and hit Enter. See what happens. If you are able to login there is a possibility of a problem with your graphics drivers.

Hope that helps.

---

### Post by putnam120 on 2010-06-26
I wasn't able to see the option to select failsafe after entering my username (and before entering the password).

However, I was able to fix the problem by reinstalling the desktop.  I don't know why this helped.

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by peterh84 on 2010-06-26
See [http://ubuntuforums.org/showthread.php?t=1472770&highlight=dhclient+gnome-session](http://ubuntuforums.org/showthread.php?t=1472770&highlight=dhclient+gnome-session).  

I had a problem that sounds like yours--input password in Gnome, some messages flash in black screen, then I get the Gnome password prompt again.  An endless loop like that.  No session selection available at bottom of screen.

I followed the directions by bitter_mike at post #6: typed Ctrl+Alt+F1 from Gnome screen to get command interface, typed "sudo dhclient" (I'm too new to Linux to know whether that was really necessary at that point to get an IP session, but it did no harm), typed "sudo apt-get install gnome-session", responded to a few prompts, typed "Ctrl Alt Del" as a clumsy way to get out once the package installation was done (I'm sure I could have started Gnome from the command prompt, but didn't remember how), and ended up back on Gnome with a password prompt that works again.  I now get a message about "problem while loading OAFIID: GNOME_FastUserSwitchApplet", which I haven't figured out yet, but I just pick the choice not to delete it and I'm fine.

Like WalkerPL in the post I reference, I had deleted Evolution the night before I stopped being able to log in, since I don't plan to use it.  The fact that deleting that package caused deletion of an essential Gnome package suggests to my layman's mind that there is a problem with the way the package or the package management is set up.  I would have thought that Synaptic would protect me from such a problem, but perhaps I need to pick some more conservative option.  Much to learn.

---

