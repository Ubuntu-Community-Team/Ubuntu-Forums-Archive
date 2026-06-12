---
title: "Had a crash and now can't open anything...."
date: 2012-02-15
forum: General Help
---

### Post by LibbyLou on 2012-02-15
Hi all and thanks in advance for any help you might be able to give me.

I've been running Ubuntu 10.04 and for a while now when I play games with Flash (mainly Facebook games like Cityville, Castleville, etc.) after a bit of playing Chrome would freeze up and sometimes the only way I could do anything would be to do a hard shut down.  Sometimes I've been able to kill the tab, but usually not.  

Happened again today, had to do a hard shut down, but this time when I rebooted, all the files, pictures, folders on my desktop had locks in the upper righthand corner and I am now unable to open anything up.  None of those things, no browsers, no terminals, nothing.  I'm using Windows right now to post this.

NO clue where to go from here, but I surely would appreciate any advice because I do NOT like running Windows!

:confused:

---

### Post by LibbyLou on 2012-02-15
Bumping out of desperation.........](*,)

Some more info about what's happening: If I try to open a terminal, or bring up anything really with a dialogue box, it's just a blank gray box.  It says at the top what it should be, but there's nothing actually in the box.  We were able to get system info to come up earlier, but a different way than we normally would and there were some things running, like ksysguard at 23%, knotify4 at 23%.....

Anyone have ANY clues at all as to what has happened?  My husband swears it's a virus, but I'm thinking it's not.  Just because Flash has been giving me issues for a while now, freezing and whatnot.  This time it just went a little further after the freeze. :(

---

### Post by LibbyLou on 2012-02-15
Also: normally when we boot it up, the keyring thing will come up asking for our password.  Now it doesn't. :confused:

---

### Post by nothingspecial on 2012-02-15
> **LibbyLou said:**
>   

Happened again today, had to do a hard shut down, but this time when I rebooted, all the files, pictures, folders on my desktop had locks in the upper righthand corner and I am now unable to open anything up.

This looks like a permissions problem. If you press Ctrl-Alt-F1 and log in and type ```
ls -al $HOME
``` who owns all your files and directories?

---

### Post by LibbyLou on 2012-02-15
> **nothingspecial said:**
> This looks like a permissions problem. If you press Ctrl-Alt-F1 and log in and type ```
ls -al $HOME
``` who owns all your files and directories?

From what I can tell, it's our username on everything.

---

### Post by LibbyLou on 2012-02-15
Okay....so I was messing around and went into user settings and changed our account type to Administrator.  Rebooted and now all the locks are gone from the folders, but I also had a ton of error messages about all my notifiers and things I had on the panel being messed up and asked if I wanted to delete or not.  I chose not to for each, but they are all gone.

Still can't open up any photos, browsers, etc.

This is maddening!!!!

---

### Post by LibbyLou on 2012-02-15
I also keep getting these knotify error messages popping up.  One is about "knotifyrc" being not writable.  I've also gotten one about "ksysguardrc" and now also digikam, after I tried to open it up.

---

### Post by nothingspecial on 2012-02-15
Still sounds like some sort of permissions issue.

The most important thing to do now is make sure all your personal data is backed up.

What I would do after that is to create a new user and log in to that account to check that it is just some some problem with your account rather than the system as a whole.

You'll have to excuse me though, it's a long time since I've booted 10.04.

---

### Post by Leppie on 2012-02-15
could you post the output of the following command:
```
ls -al ~
```
this command will produce a detailed list of files in the home folder of the currently logged on user.

---

### Post by LibbyLou on 2012-02-15
Okay, weird......rebooted again, but this time instead of ignoring the errors it said it found, I chose to fix them.  It did a bunch of stuff with orphaned inodes and then when it was up, I am now able to access everything again.  The only strange thing I see so far is that in Chrome, my bookmarks and things are still there, but the theme is changed and my Chrome apps and extensions are gone.

It also looks like my home page has been changed from iGoogle to just the blank Chrome tab.

:confused:

Do you all think I should do anything else?  This is so strange!  And thank you for your help so far.

---

### Post by nothingspecial on 2012-02-15
Have you got all your personal data backed up?

---

### Post by LibbyLou on 2012-02-15
> **nothingspecial said:**
> Have you got all your personal data backed up?

Most of the important stuff, yeah.

I would really like to know what exactly caused this to happen, even if it does appear to be fixed.  And I wonder what happened to Chrome -- would those inodes have something to do with it?

This ALL started after the Flash freeze during Castleville.  Might just have to give those games up, not worth the hassle!

---

### Post by Leppie on 2012-02-15
> **LibbyLou said:**
> 
Do you all think I should do anything else?  This is so strange!  And thank you for your help so far.
this can happen when you stop the system using the hardware button.
like nothingspecial said, it's good to have a backup of your files for these kind of situations.

also, next time your machine locks up, try the following:

[LIST]
[*]press and hold the ALT and the SysReq/PrtSc buttons at the same time
[*]while keeping those keys pressed, press the following keys one by one with a couple of seconds of pause between each key: R E I S U B
[/LIST]
if done correctly, the machine should start rebooting after you've pressed the "B".

---

### Post by LibbyLou on 2012-02-15
> **Leppie said:**
> this can happen when you stop the system using the hardware button.
like nothingspecial said, it's good to have a backup of your files for these kind of situations.

also, next time your machine locks up, try the following:

[LIST]
[*]press and hold the ALT and the SysReq/PrtSc buttons at the same time
[*]while keeping those keys pressed, press the following keys one by one with a couple of seconds of pause between each key: R E I S U B
[/LIST]
if done correctly, the machine should start rebooting after you've pressed the "B".

Yeah, I know it's always a bad idea and should be a last resort to power down using the power button.  It's just the only thing I knew to do when everything would freeze like that.  Thanks for the alternate reboot instructions, I'll be keeping those handy! :P

---

### Post by nothingspecial on 2012-02-15
Well hard shut downs are not good.

In future do this, hold down Ctrl-Alt-SysRq

and with those keys held down press

R E I S U B

in that order to restart cleanly or

Ctrl-SysRq-K to just kill the Xserver


***Edit*** Or do what Leppie said :p

---

### Post by LibbyLou on 2012-02-15
> **nothingspecial said:**
> Well hard shut downs are not good.

In future do this, hold down Ctrl-Alt-SysRq

and with those keys held down press

R E I S U B

in that order to restart cleanly or

Ctrl-SysRq-K to just kill the Xserver


***Edit*** Or do what Leppie said :p

Thank you! :D

---

