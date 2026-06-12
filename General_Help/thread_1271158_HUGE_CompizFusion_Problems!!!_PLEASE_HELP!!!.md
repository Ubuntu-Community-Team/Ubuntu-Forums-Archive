---
title: "HUGE CompizFusion Problems!!! PLEASE HELP!!!"
date: 2009-09-20
forum: General Help
---

### Post by LifeEnemy on 2009-09-20
I'm having big problems with Compiz. I have a number of plugins enabled, all of which used to work perfectly, but now a bunch of them just don't work. I've checked to make sure that they are enabled and that the key bindings are correct, but they just won't work.

Here are the plugins I have enabled:
Gnome Compatibility
Negative
Show Mouse
Opacify
Enhanced Desktop Zoom
Expo
Show Desktop
Desktop Cube
Viewport Switcher
Rotate Cube
Widget Layer
3D Windows
Cube Reflection and Deformation
Window Decoration
Animations
Fading Windows
Motion Blur
Wobbly Windows
Animations Add-Ons
Paint Fire on Screen
Water Effect
Annotate
Splash
Window Previews
All "Image Loading" plugins
Crash Handler
Resize Info
Session Management
DBus
Mouse Position Polling
Workarounds
Regex Matching
Video Playback
Group and Tab Windows
Place Windows
Shift Switcher
Extra WM Actions
Scale
Snapping Windows
Move Window
Resize Window
Shelf


And these are the plugins that are not working, that have actions I can see:
Negative
Show Mouse
Expo
Paint Fire (works about 10% of the time, usually just doesn't start)
Annotate (I've had this work a couple times since this started, but that's it)
Resize Info
Group and Tab windows


This is extremely annoying. All these plugins worked fine when I first set them up, but now I'm having so many problems. Please help!

---

### Post by LifeEnemy on 2009-09-22
Someone please help!

---

### Post by DougieFresh4U on 2009-09-22
First, you do not mention what Ubuntu version your using and what is your graphics card?
Have you checked 'Appearance' to see if extra effects is checked. I know that after some reboots I have to go back and enable it again.

---

### Post by LifeEnemy on 2009-09-23
Sorry, I forgot. I'm using Jaunty, and I have a GeForce 8600M graphics card. I checked that setting and it is set to custom. All my animations still work, it's just that certain plugins don't work.

One other thing I noticed, that may be related: with Enhanced Desktop Zoom, I used to be able to hold down the <super> key and push down the mouse wheel to draw a box that would be set to the zoom area. I noticed that this stopped working a little while ago, probably around the same time. I can still zoom in by scrolling, though.

---

### Post by LifeEnemy on 2009-09-23
Very strange. Almost all of the ones that don't work use the "super" key (Resize info doesn't). However, I know that my super key is not broken, because if I change the shortcuts to include another modifier (ex: super+e  -->  super+alt+e) then they work. Can anyone tell me WTF is going on???

---

### Post by LifeEnemy on 2009-09-28
Will SOMEONE please help???? This is a huge issue, I can't use half of the damn features of Compiz. Could it be something with the OS? Would I reinstall help at all? Would it be worth the effort?

---

### Post by Giblet5 on 2009-09-28
Well, you can easily test your software install.

Create a new user.

Log in as that user.

Set up compiz just so.

Does it work?

If so, you could
A) use the new account
B) poke through gconfeditor and try to find out what's different
C) Move your existing .gconf directories to a backup and reconfigure

There's lots of options, but I see no reason to freak out over eye candy...unless you have the Really Good Coffee. ;)

---

### Post by LifeEnemy on 2009-09-28
I said before that my problem was related to the 'super' key. Here's something I noticed: I still can't use any plugin that uses the super key *only*, but I could sometimes use ones that had more than just the super key. Well, I found out that those ones only work if I press all the other modifier keys before 'super'. If I press super first and then, for example, alt, the action won't work.

That said, I did just try making a new user and I tested out two plugins and they work fine. I'm assuming the rest probably work as well. Thanks a lot for that suggestion. However, I would prefer not to have to redo ALL my settings and config files that I've changed to get things working (fingerprint scanner, mouse, etc). Is there any way that I could transfer all my settings to the new account, without also transferring the current problem I have? I'm guessing probably not. How could I go about solving my problem, then? I know next to nothing about computers. What is gconfeditor, where do I find it, and what/where are .gconf files?

One last thing: Normally I wouldn't worry so much, especially if this actually was just eye candy, but I've been trying to solve this (among many other problems) since I switched to Ubuntu, amidst an extremely busy college semester and a whole bunch of other crap. This isn't just eye candy, it's compiz plugins that I use often, and while they don't work it makes my life harder (best example: I can't use expo, which I really liked).


So, to sum up, thanks for the suggestion. It's good to know that I at least have a fall back if nothing else works. However, if I could get a little help trying to fix the problem without 'jumping ship', and maybe some insight into why/how this could have happened, it would be greatly appreciated. I don't know anything beyond general computer knowledge, and I'm still an Ubuntu newbie trying to make it work like I want it to.

---

### Post by LifeEnemy on 2009-09-29
bump

---

### Post by LifeEnemy on 2009-09-29
bump

---

### Post by LifeEnemy on 2009-09-30
i looked around in my user folder and the new user ("test"), but I couldn't find any config files, not that I would know what to even do with them if I could find them. Can't anyone help me?

---

### Post by Giblet5 on 2009-09-30
Did you create a new user and set up compiz as I suggested?

Does it all work for that new user? (just "yes" or "no", please)

---

### Post by Giblet5 on 2009-09-30
> **LifeEnemy said:**
> i looked around in my user folder and the new user ("test"), but I couldn't find any config files, not that I would know what to even do with them if I could find them. Can't anyone help me?

Configs are held in "hidden" folders (their names begin with a period...)

Click Places/Home Folder. Hit Ctrl-H to show hidden folders. Your config files for compiz are in the .gconf folder.

Do you have CCSM (Compiz Config Settings Manager) installed?

If you can get a working config under a new user's account, you can save that config and load it (via CCSM) on your old account.

---

### Post by LifeEnemy on 2009-10-01
As I said earlier, I did create a new user and it worked, so **Yes**.

I see, I didn't know how to show hidden folders. I found the .gconf folder, and then I looked under "apps" and I found folders for Compiz and CompizConfig. I do have CCSM installed.

Do you mean to copy a specific file from the new user, or just export the settings and import them to my current account? I'll try it, but like I said the problem has something to do with the 'super' key, so I'm not sure if it's related to Compiz anymore. Hopefully it works, though.

---

### Post by LifeEnemy on 2009-10-01
Well, I tried to import the settings like you suggested, but it wouldn't let me. I tried exporting the settings from the 'test' account to my own desktop, but the file would just not show up. I then tried exporting to the 'test' account desktop, which worked, but then it wouldn't let me move it to my account because it said I didn't have permission. I also just tried to import the file from the 'test' desktop, but it wouldn't work. The file didn't even show up unless I set the file type to "all files." I have no idea what's wrong, but for whatever reason it just won't do it.

EDIT: Actually, the import may have worked, although it certainly didn't give any indication that it did. I think it did because one of the shortcuts in the 'scale' plugin was different from default, and I only set it that way on the 'test' account. So, I guess the import did work, but didn't solve my problem. I'm thinking it probably isn't Compiz.

ANOTHER EDIT: Seems like there may not be an easy way to solve this problem. If you can't think of anything easy/simple to fix this, then I think I will just jump to a new account. I'd like to keep the same account name, though. Could you give me some advice on how to do that (i.e. what files to transfer, any config files, a good process to transfer by)? Could I transfer all my /home/account files, exported profiles (like compiz), and config files to another account, delete my account, and then recreate it? Would creating a new account with the same name cause any problems? Sorry to ask so many questions, but I've been struggling to get Ubuntu to work for me since I installed it, and I've accidently cause myself a number of problems before, and this seems potentially more risky than most things I've tried doing.

---

### Post by LifeEnemy on 2009-10-05
Bump

---

### Post by Zavior on 2009-10-07
**How to open gconf editor:**
To open gconf editor simply open a terminal (Ubuntu Menu > Accessories > Terminal) and type in "gconf-editor" without the quotes. Your compiz settings are in apps > compiz. Now, there are a lot of settings in there and I'm not sure if you really want to sort through all of these... 

**Another possible solution:**
I would recommend trying to remove all of you compiz settings (in order to start from scratch). To do that enter the following command into the terminal "rm -rf ~/.compiz ~/.gconf/apps/compiz ~/.config/compiz" again without quotes. After this you will of course need to set all of your plugins back up (a pain I realize). This may not be the optimal solution but it sounded like you were getting desperate so I thought I'd give you something to try. If this doesn't work or you would like to try something different let me know, I may be able to come up with something else.

---

### Post by LifeEnemy on 2009-10-07
Thanks for the response. I don't know enough to go through the settings files, I think. I will try removing my compiz settings, though. It's not a big deal because compiz already decided to erase my settings a few days ago (even changed the ones in my exported backup file, somehow), so I have to redo them all anyway. I've been planning to switch accounts as soon as I can find the time, since that worked and I haven't been able to fix the problem yet. I will try your suggestion though.

---

### Post by LifeEnemy on 2009-10-09
I just tried something, and I think it might affect the idea of wiping my Compiz settings. I went into Preferences>Keyboard Shortcuts, where I found a setting I could test using the 'super' key. I found out that the same problem exists when doing that (works fine as long as the 'super' key isn't used). I think that those shortcuts are independent of Compiz, which would mean the problem isn't with Compiz, and wiping the settings would have no point? Am  mistaken about something?

---

### Post by LifeEnemy on 2009-10-09
Haha! I solved the problem! I copied the .gconf folder from the 'test' user account (which was difficult to do with all the permissions issues to get around) and put it in my /home folder (ended up 'merging' the folders). Now the problem is gone and the super button works exactly like it's supposed to. Thanks for all the help and suggestions! I'm just glad to have solved this without having to move my account.

---

### Post by Zavior on 2009-10-16
> **LifeEnemy said:**
> Haha! I solved the problem! I copied the .gconf folder from the 'test' user account (which was difficult to do with all the permissions issues to get around) and put it in my /home folder (ended up 'merging' the folders). Now the problem is gone and the super button works exactly like it's supposed to. Thanks for all the help and suggestions! I'm just glad to have solved this without having to move my account.

Awesome! Glad to hear it. Sorry I posted that last comment and then forgot all about it. Glad to hear you fixed it without me :).

---

