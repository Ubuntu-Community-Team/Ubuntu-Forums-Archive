---
title: "Caught in login screen loop - karmic 9.10"
date: 2010-03-16
forum: General Help
---

### Post by barnskybeat on 2010-03-16
Dear Ubuntu community,

I have a real issue and need urgent help. I am stuck in a login loop and have looked in several threads in order to find a solution for my issue. I am relatively new to Ubuntu/Linux and do not really know my way around especially when it comes to command prompt. Thus I need someone with patience and who can guide me step by step in order to get to the bottom of the issue and to fix it. 
The issue started all of a sudden, no particular reason. I only uninstalled evolution  before and then rebooted. The shutting down process got stuck forever and I turn off the PC by holding the power button. Then I attempted to start, the PC boots to the login screen and I select my name and enter the correct password as usual. Then the screen changes for a split of a second to the back command screen and I can see the word “crypto” or so. Then the screen returns to the login screen and this loops.

Karmic 9.10, fully updated
Thinkpad x61s

Please help, need to access my data on my PC. I am online on my second (work) PC.
:-(

---

### Post by GorgeousGe0rge on 2010-03-17
I'm having a similar problem with logging in.  I just keep looping back to the login screen after entering my password.  Also of note, I don't have the keyboard or language drop down options at the bottom of the screen.  Nor is there the blue Xubuntu logo - just a generic icon of a black monitor in the login dialog box.  Only the desktop option shows itself.

Prior to all these problems with login, I'd installed the JAVA 6.0 plugin and before that I installed Nautilus.

I would like to get  back to my desktop too as I also have some data that I need to access.

---

### Post by Naiki Muliaina on 2010-03-17
Are you able to log into a terminal session? (down the bottom of the log in screen where it says session, choose terminal)

If yes someone might be able to help better. 

My only idea for the first poster (im realy not as techy as most here, so im probaly barking up the wrong tree) I think uninstalling Evolution used to uninstall Gnome. If you can get a termanal session, try typing in 

sudo apt-get install gnome

sudo reboot 

Might work.

---

### Post by john newbuntu on 2010-03-17
Try getting on to one of the virtual terminals.  You can do this by pressing the Ctrl+alt+F2 key.  Remember that get back to gnome login screen, press Ctrl+alt+F7.

Now, once to go to the virtual terminal, log in using your id and password.  First check for space by issuing the command:
df -h

If the line corresponding the root file system (mounted on  /) says 99% or so, it means you have no disk space.  So you need to clean up some stuff.  Once you remove a few (hopefully large) unnecessary/old log files (say in /var/log or /tmp), you can get back to the gnome login and try logging in again.

---

### Post by johnnycasher on 2010-04-21
i get caught in that loop too :\ And i think i will get out of ubuntu cuz i'm trying but i can't get things back to work.

---

### Post by klemes on 2010-04-21
There was a similar [solved] thread in this forum.
If you can get into a terminal console (ie with CTRL+Alt+F2)
and you are able to login with your username then type at the prompt:

ls -l .ICEauthority

and note the results.(be carefule to preserve the dot (.) before ICEauthority).

If the permissions (the line that looks like (rwxrw...and so on) in the beginning of the output row of teh command) look different than (-rw-r--r--) then type:

```
sudo chown (your_username_here):(your_username_again) .ICEauthority
```

wait for the command prompt and then type:

```
chmod -c 664 .ICEauthority
```

---

### Post by johnnycasher on 2010-04-21
Klemes, what thread?
 
I don't know what your command is usefull for mate. But it doesn't help me.

---

### Post by klemes on 2010-04-21
Look I do not remember the exact thread but you can use the search facility in this forum to find it(there are lots of similar threads).In one of them someone had the same problem as you (logging in into gnome) and solved it by changing the permissions in the .ICEauthority file of his home directory.That's all I 've been trying to tell you.

---

