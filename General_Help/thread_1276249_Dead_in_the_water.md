---
title: "Dead in the water"
date: 2009-09-26
forum: General Help
---

### Post by rmccutchan on 2009-09-26
It seems I have a problem.  Disclaimer: I am very new to Linux.

I went to compiz and was poking around and ticked the "window fade" (I think) button, and now Ubuntu will do nothing.  I restarted the computer by the button, logged on, and when I move the mouse, chunks of the desktop start to dissapear and nothing happens when I click on things except pieces of desktop slowly start to dissapear.

I made it to the command prompt, finally, after restarting a few times.  Is there anything I can do from the command prompt to disable compiz and hopefully get back to the desktop?

---

### Post by jflaker on 2009-09-26
if you can get to your home directory...press CTL-H to expose hidden directories and delete the .compiz folder, reboot and you should be ok...

If you can't, boot from the live cd and enter terminal


Type "sudo nautilus" (no quotes) and find that directory and delete it.....

reboot and you should have default compiz settings...

---

### Post by rmccutchan on 2009-09-26
O.K.  I could not get any response while in the command prompt, so I inserted the live cd and went to the terminal and did what you said and could not find the .compiz folder.  So I went into synaptic and removed anything that had compiz in it.  I rebooted and still nothing.  Pieces of the desktop start to dissapear and then finally the whole thing goes black.  Sounds like a virus.

---

### Post by jflaker on 2009-09-26
did you hit CNTL-H ....

.compiz is hidden, cntl-h unhides them.....

---

### Post by rmccutchan on 2009-09-26
Sorry if I sound dumb, but I am really new.  I am at the command prompt right now without the live cd.  This is what I see:
 
[EMAIL="mccutchan@mccutchan-desktop:/home$"]mccutchan@mccutchan-desktop:/home$[/EMAIL]
 
Is this where I am supposed to press ctl-h?  I did and got beeped at and nothing happened.
 
I apoligize for the dumb qestions.  I really am reading a bunch of material so I can learn.

---

### Post by lovinglinux on 2009-09-26
```
mv ~/.config/compiz ~/compiz_backup
```

---

### Post by jflaker on 2009-09-26
> **lovinglinux said:**
> ```
mv ~/.compiz ~/compiz_backup
```

That will do the job!

Reboot after this command...what this does is rename the folder....when you come back from the reboot and your system functions ok, then navigate to your home folder and delete the folder compiz_backup as the back up is no longer needed and just taking up space....

---

### Post by lovinglinux on 2009-09-26
> **rmccutchan said:**
> Sorry if I sound dumb, but I am really new.  I am at the command prompt right now without the live cd.  This is what I see:
 
[EMAIL="mccutchan@mccutchan-desktop:/home$"]mccutchan@mccutchan-desktop:/home$[/EMAIL]
 
Is this where I am supposed to press ctl-h?  I did and got beeped at and nothing happened.
 
I apoligize for the dumb qestions.  I really am reading a bunch of material so I can learn.

Since you are in the terminal, run the command from my previous post.

Just to clarify, the instructions to hit CTRL+H is for the file browser, not the terminal. When browsing your home folder with the file browser you can hit CTRL+H to display hidden files and folders, which are those starting with a dot.

---

### Post by rmccutchan on 2009-09-26
I get:
 
mv: cannot stat '/home/mccutchan/.compiz": no such file or directory

---

### Post by sukigenseki on 2009-09-26
nevermind people beat me to it

---

### Post by lovinglinux on 2009-09-26
Edit: Ignore this post.

---

### Post by lovinglinux on 2009-09-26
Sorry, the correct command is:

```
mv ~/.config/compiz ~/compiz_backup
```

The folder ~/.compiz only stores compiz session, while the one above is where the compiz config are stored.

Don't forget to reboot after doing this.

---

### Post by rmccutchan on 2009-09-26
I am getting "no such file or directory" when I look for compiz or .compiz.  I tried all commands and everything posted, rebooted several times, and get the same results (dissapearing desktop).

---

### Post by lovinglinux on 2009-09-26
> **rmccutchan said:**
> I am getting "no such file or directory" when I look for compiz or .compiz.  I tried all commands and everything posted, rebooted several times, and get the same results (dissapearing desktop).

Are you sure you are typing the correct command? It's better to copy the entire command instead of typing it:

```
mv ~/.config/compiz ~/compiz_backup
```

---

### Post by rmccutchan on 2009-09-26
I double checked the typing.  I am on another computer since I can't get to the internet with the one that is having problems.
 
I am getting a message that says "directory not empty"
 
I removed anything relating to compiz through synaptic while I had the live cd in, so I thought that would do it.  I am sure that is why it can't find the directory or folder.  
 
It may be time to re-install Ubuntu?

---

### Post by lovinglinux on 2009-09-26
> **rmccutchan said:**
> It may be time to re-install Ubuntu?

Not necessary. Let's try a different approach.

Open the terminal with your account, not the LiveCD, then run this:

```
nautilus ~/.config/compiz
```

It should open your file browser and at least a folder named **compizconfig** should be displayed. Delete that folder and reboot.

---

### Post by rmccutchan on 2009-09-26
It says:
 
*Could not parse arguments: Cannot open display:*

---

### Post by lovinglinux on 2009-09-26
> **rmccutchan said:**
> It says:
 
*Could not parse arguments: Cannot open display:*

Hmmm, I guess you might have a different problem.

Try this:

```
sudo apt-get purge compiz-core
```

It will ask if you want to remove a bunch of compiz related stuff. Confirm, then after it finishes, reboot.

---

### Post by rmccutchan on 2009-09-26
O.K.  We are closer.  I can actually maneuver around the desktop and open windows, but all the windows open narrow and the title bar at the top of the window is not there, so I can't exit windows with the mouse.  I also can not give focus to other windows.  They stay underneath the last window I opened and can not be moved.

---

### Post by lovinglinux on 2009-09-26
> **rmccutchan said:**
> O.K.  We are closer.  I can actually maneuver around the desktop and open windows, but all the windows open narrow and the title bar at the top of the window is not there, so I can't exit windows with the mouse.  I also can not give focus to other windows.  They stay underneath the last window I opened and can not be moved.

Don't know how to help any further. Perhaps you could delete all gnome configuration files and folders, if you don't have any special configuration, and reboot. Then you will start with a fresh default desktop.

---

### Post by rmccutchan on 2009-09-26
Well, I wasn't sure how to find the files you mentioned, so I went to synaptic and re-installed anything related to gnome (clunky, I know, but I will learn someday)

I now have the title bar back and I can move windows around and exit out of windows properly etc....

But when I go to system>preferences>appearance and try to enable normal or extra desktop effects, it gives me a message "Desktop effects could not be enabled"

I am sure this should be an easy fix for someone with a little more experience than me.

---

### Post by rmccutchan on 2009-09-26
Success!

I did a quick search and found a tutorial on Ubuntu forums that gave me this code:

[I]sudo apt-get install compiz compizconfig-settings-manager

[/I]I then went to appearances and the "extra" under visual effects worked, and the effects in Compiz work.
I am now back to where I was before I messed things up!  

FYI - I clicked  "motion blur" under "effects" in compiz, and thats when everything fell apart.  (I'm afraid to try it again!)
I don't know if it is a bug that needs reported or what.

Thank you VERY much for your time.  I hope to be able to help someone else by this time next year.  I start
classes next month to become a network administrator and plan on taking linux courses along the way.
I can see Ubuntu becoming a prominent OS in the workplace and for small businesses trying to save
every dollar they can.

Again, thanks.

---

