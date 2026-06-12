---
title: "Firefox 3.0.11 version completely Mute, No sound."
date: 2009-06-25
forum: General Help
---

### Post by theteju on 2009-06-25
Hello 
I have been using ubuntu 8.10 since morethan 6 months and never had a problem before.
recently couple of weeks ago, after normal upgrade , I notice new version of firefox update and after that update. I lost sound on firefox.

youtube, songs online everything absolutely soundless.

rest of the system sounds is just normal.

I tried on forums. could not found definite answer for 8.10

Looks like something wrong with firefox plugin but I am not sure how to solve my problem

this is getting really fustrating, Please help me asap.

Thank you all

any replies are highly appreciated.:confused::confused:

---

### Post by theteju on 2009-06-26
no reply yet..

Please help me guys.. I donot wanna switch you 9.04, i am middle of important semester here.. and a lot to back up

this is a minor issue i guess. please save my time for complete reinstallation.

plese help  me

please

---

### Post by lovinglinux on 2009-06-26
Try the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683). It usually solves all media related issues.

---

### Post by theteju on 2009-06-27
I went to the link above. tried few things.
first of all,, My mplayerplugin.conf file looks exactly same like its shown in guide so no need to change.

then I deleted pluginreg.dat file from home/mozilla/firefox folder. but no luck.

I reinstalled adobe flash but firefox is still mute.

Finally i changed my plugins from mplayer to GECKO media player. the problem is still same.

Let me repeat my problem. all system sounds work just perfect except all videos in firefox is absolutely mute. NO sound in Firefox. I had sound before it suddenly stopped after an upgrade. current firefox version on my system says 3.0.11

This is getting really really fustrating..

Somebody please help me. Or is there a way to remove and reinstall firefox again.

let me know

Thanks

---

### Post by gldearman on 2009-06-27
I don't know much about media, but I know *Firefox* pretty well, so I maybe can help.

I wouldn't bother re-installing Firefox, since that rarely helps.

Have you tried launching Firefox in safe mode?  Try this:

```
firefox -safe-mode
```

This will tell you if the problem comes from an extension, theme, or user setting.  Note that the "Disable all add-ons" option in safe mode does *not* disable plugins.

Are there any other users on your system?  Are they having Firefox sound problems?  If so, you know that it is something in *your* Firefox profile.

If you don't share your computer, you could try launching Firefox with a brand-new profile, and see if it has sound.  If it does, you know that the problem is somewhere in your profile folder.

---

### Post by lovinglinux on 2009-06-27
> **gldearman said:**
> I wouldn't bother re-installing Firefox, since that rarely helps

+1

You could try the Flash related stuff from [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). It also has instructions about backing up, deleting and fixing profiles. You could also try installing libflashsupport. Please keep in mind that this package might cause instability and crash Firefox when viewing flash content. To install it run this command on a terminal.

```
sudo apt-get install libflashsupport flashplugin-nonfree-extrasound
```

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.


> **gldearman said:**
> I don't know much about media, but I know *Firefox* pretty well, so I maybe can help.

Please take a look at the tutorial above and tell me what you think. Any contribution will be very welcome.

---

### Post by theteju on 2009-06-29
Hello Guys,,

Thank you so much for your replies.. But i could not solve my issue.
I gave up and back up my system.

Downloaded Ultimate edition 2.2 dvd .iso 64bit version. they say its 9.04 based system.

I did clean install. Right now. system look working good.

I never added another user account on my system.

Should I add a user account and use it regularly. How can I prevent similar issue happening again.

Let me know.

Thank you.

---

### Post by kostkon on 2009-06-29
It could be that you have two sound devices (for example one on-board and one PCI sound card) in your system and the Flash sound was sent to the non default one, to the one that you don't have speakers connected to it.

Could you give in a terminal the following
```
aplay -l
```
and post the output here?

---

