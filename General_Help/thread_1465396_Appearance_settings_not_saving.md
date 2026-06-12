---
title: "Appearance settings not saving"
date: 2010-04-29
forum: General Help
---

### Post by dnr1128 on 2010-04-29
I've installed Lucid, and so far the only problem I'm having repeatedly is that my appearance settings aren't saving.  Every time I reboot I have to change the visual effects from "none" to "normal", whereupon it searches for drivers and changes the settings.  Any ideas what could be causing this and how to fix it?

---

### Post by dnr1128 on 2010-04-29
I'm running it on a Lenovo thinkpad t42, all stock.  Karmic ran flawlessly.  Lucid seems to have a few graphics problems, especially on shutdown.  The colors around the "ubuntu" go all weird, like its going to 24 color or something.  Once it boots up and I change the appearance settings, it runs fine.  I just need to be able to save the settings so I don't have to change it everytime I boot up the laptop.  Sometimes when I go to shut down the shutdown screen locks up on a purple background with green haze around the word "ubuntu".  

I've uninstalled and reinstalled compiz with no change.  I've also tried "sudo apt-get reinstall ubunutu-desktop" and the command "reinstall" isn't recognized.

---

### Post by fizikz on 2010-04-29
I have the same problem with the appearance settings not saving. I have no window borders when I reboot and the appearance setting is on 'none'. If I select 'normal' the window borders are back for that session until I reboot. Solutions?

---

### Post by miesogeno on 2010-04-29
i had the same problem when i saw this thread. but i tried something before replying and it worked.

what i did was

system-> preferences-> startup aplications

then, in the "options" tab, i just pressed "remember currently running applications"

i restarted and the windows had borders for the first time at reboot.

---

### Post by dnr1128 on 2010-04-30
Since I'd done an upgrade, and I already had my /home backed up, I downloaded the iso and did a fresh install.  All seems to be working well now.  @fizikz try that suggestion and see if it works for you.  May save you the headache I've had this evening.

---

### Post by fizikz on 2010-04-30
I tried the suggestion but it didn't work for me. I'm having a few problems since upgrading to 10.04 that I'm not certain what is causing which problem. One issue is the window decorations not appearing, and the other is some problems with the nvidia video drivers. For the window decorations, these links might be useful: 

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/561271]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/561271")

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/559111]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/559111")

Bottom line, the suggestions are to:

* install compiz package, or
* remove ~/.gconf/desktop/gnome/session/

----------------------

I can't really confirm if those solve the problem, since at the moment the window decorations are back for me after trying many different things, including installing/uninstalling various video drivers.

If the problems persist I may do a clean install, but I'm dreading having to reconfigure everything to my liking. Just goes to show that having a backup of /home is always a good idea.

---

### Post by miesogeno on 2010-04-30
i also thought about the video drivers, since the splash screen doesnt look very well.

it looked much better when booting from the live CD, with better resolution. now it seems like its using the lowest possible resolution, i.e. the "ubuntu" logo its very large, with low definition and always blinking.

but once it shows the login screen everything is fine.

i'm sorry i cant explain this any clearer, i'm a recent linux user, all my vocabulary is very naive, but i didn't need much in windows (and i didn't expect much either..)

---

### Post by r-senior on 2010-04-30
I also have this issue after a 9.10 -> 10.04 upgrade (not a clean install, an upgrade using the alternate CD downloaded via BitTorrent).

I've tried removing ~/.gconf/desktop/gnome/session/, which didn't work for me.

I also tried reinstalling compiz and uninstalling and installing, but the metapackage didn't seem to do anything. So I tried uninstalling compiz-core, then reinstalling compiz. That certainly did something but didn't fix the problem.

Setting /usr/bin/metacity as a startup application works in terms of getting the window decoration up at startup but Compiz settings aren't being saved for the next logon (System - Preferences - Appearance - Effects reverts back to None, and if I don't autostart metacity, that means no window decoration).

I tried creating a new user account and that works fine without Compiz. Windows are decorated with Metacity.

---

### Post by r-senior on 2010-04-30
I've not got to the bottom of this, but I have an ugly workaround. ;)

Assuming compiz is installed, add /usr/bin/compiz --replace as a startup application.

See also [http://ubuntuforums.org/showthread.php?t=1466162&highlight=effects]("http://ubuntuforums.org/showthread.php?t=1466162&highlight=effects")

---

### Post by DeadMetal on 2010-04-30
> **r-senior said:**
> I've not got to the bottom of this, but I have an ugly workaround. ;)

Assuming compiz is installed, add /usr/bin/compiz --replace as a startup application.

See also [http://ubuntuforums.org/showthread.php?t=1466162&highlight=effects]("http://ubuntuforums.org/showthread.php?t=1466162&highlight=effects")

Thanks, this workaround works for me as well, after booting I have window borders and visual effects working just fine.

The other suggestions mentioned in this thread and in the bug reports did not solve the problem, but this one did.

---

### Post by fizikz on 2010-04-30
I have the same bootup behaviour that miesogeno described, but once at the login screen everything is normal. I'm not sure how, but the appearance setting and window border problem is solved for me now. I have now installed the nVidia proprietary drivers and blacklisted the nouveau drivers. Those seemed to be causing me some grief. I can't be sure that was what solved it for me, but I figure it's worth keeping in mind.

---

### Post by r-senior on 2010-04-30
Bug report filed:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617")

---

### Post by DeadMetal on 2010-04-30
Thanks for your work, I have indicated that this bug affects me as well.

---

### Post by _0R10N on 2010-04-30
Well, this affects me, too... I'd tried almost everything, I'm going to try a couple of workaround I saw in this thread! I let you know!

Kind regards!

---

### Post by _0R10N on 2010-04-30
> **r-senior said:**
> I've not got to the bottom of this, but I have an ugly workaround. ;)

Assuming compiz is installed, add /usr/bin/compiz --replace as a startup application.

See also [http://ubuntuforums.org/showthread.php?t=1466162&highlight=effects](http://ubuntuforums.org/showthread.php?t=1466162&highlight=effects)

Great!!! it worked!!! I know this is only a workaround, and I'm taking it as just that! But, until it this is fixed, it'll stay in my Startup Applications List.

Many thanks!:popcorn:

---

### Post by obiku on 2010-05-08
OK, that did the trick almost. The windows borders are back, even after a reboot. But I set visual effects to EXTRA, but after reboot everything is empty in the visual effects tab.

Also my settings in Compriz are not saved.....


But...... it is better than before this workaround.

---

### Post by deanamartin71 on 2010-06-11
> **miesogeno said:**
> i had the same problem when i saw this thread. but i tried something before replying and it worked.

what i did was

system-> preferences-> startup aplications

then, in the "options" tab, i just pressed "remember currently running applications"

i restarted and the windows had borders for the first time at reboot.

This helped me out no end.... Great work....

---

### Post by kaspar_silas on 2011-01-27
I realise this is a slightly old thread but it was the most recent one I came across when I ran into this problem. However it's solution isn't good for me. I don't want to remember the running applications everytime so I found a new solution.

Go to:
Startup Applications  
and turn off
"GSettings Data Conversion"

this sorted it for me. God knows what this application actually done but I have had no problems since I turned it off.

EDIT: Nope it returned later so I re-enabled this. Strangely after a few days the problem went away.

---

