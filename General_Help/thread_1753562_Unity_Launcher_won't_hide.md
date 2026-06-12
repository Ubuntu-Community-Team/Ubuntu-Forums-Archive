---
title: "Unity Launcher won't hide"
date: 2011-05-09
forum: General Help
---

### Post by Azguz Bloodfist on 2011-05-09
I've just installed Ubuntu 11.04 and have come across a strange bug, where after using Ubuntu for a while, the launcher suddenly appears and will not hide. This occurs when my mouse is no where near the launcher. I have a duel screen display.

This is very annoying as the launcher appears above the windows I am working on as shown in the screenshot:
[ATTACH]191630[/ATTACH]

I have tried changing the launcher hide options in ccsm but it doesn't seem to make any difference. At the moment it is set to autohide.

Has anyone else come across this?

---

### Post by stimpie on 2011-05-09
This could be a bug, see also [http://ubuntuforums.org/showthread.php?t=1751282&highlight=unity+launcher+hide](http://ubuntuforums.org/showthread.php?t=1751282&highlight=unity+launcher+hide) for someone with a similair issue.

Trying closing some applications to see if that solves it.

I have created bug [https://bugs.launchpad.net/unity/+bug/779802](https://bugs.launchpad.net/unity/+bug/779802) for this. Please comment with your details.

---

### Post by grahammechanical on 2011-05-09
Do you have the CompizConfig Settings manager installed and the Unity Plugin ticked? If so, then click the Unity Plugin and look at the line that says Hide Launcher. You will have the option to, Never, Autohide, Dodge Windows, Dodge Active Window.

Regards.

---

### Post by Azguz Bloodfist on 2011-05-09
Thanks I have commented on the bug, although it seems a bit different as my bug is not limited to Java applications. I suspect it is something to do with Duel screens and it detecting the mouse over the launcher when it isn't. I've just noticed the clock on one of my screens is trailing off the end of the screen, which may be a related issue (first time it's happened)

---

### Post by daveybuntu on 2011-05-13
Same problem here, although it only ever occurs when Libreoffice is running.  When I quit Libreoffice, the launcher happily hides itself straight away.

---

### Post by James.Denholm on 2011-05-15
I experience the same thing as daveybuntu - Running Calc and Firefox, with the plugin set to "Dodge windows" in CCSM. Although it doesn't happen consistently, so there might be slightly more to it.

---

### Post by Azguz Bloodfist on 2011-05-16
Yes the problem is the same as Daveybuntu for me. Seems to be caused by libreoffice-calc as the launcher hides itself when calc is closed

---

### Post by dfv78 on 2011-05-17
I can confirm it also, Libreoffice Calc running didn't let the launcher autohide. Does not happen often, sometimes the launcher autohides when Calc is running with no problems.

---

### Post by lateralchaos on 2011-06-16
I can confirm this behaviour, but not sure if it is from LibreOffice being open, because it still hung there after I closed it. I was able to get the launcher to hide after closing a bunch of open applications, not sure which one it was.

---

### Post by 0xParse on 2011-06-27
I have the same problem.  I set it to auto-hide in Compiz and it seems to occur either when running Libreoffice or Clementine (music player).  Do they have any structural similarities?

---

### Post by b0wter on 2011-06-28
Same happens for me with opera as soon as I use drag'n'drop. It's already an official bug as it seems to happen with any QT related software:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/769703](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/769703)

---

### Post by BCingyou on 2011-07-01
Same problem and I was afraid I had somehow screwed up my Compiz settings... I had made some changes in the "experimental" tab of settings like turning off backlighting and I thought that might be the culprit.  

But I can confirm that once I quit Clementine (the only QT app I ever use) the problem disappears.

---

### Post by zabuch on 2011-08-05
> **b0wter said:**
> Same happens for me with opera as soon as I use drag'n'drop. It's already an official bug as it seems to happen with any QT related software:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/769703](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/769703)

Yup, that's it! The same is happening for me when using D&D in Amarok.

---

### Post by rafe101 on 2011-08-11
The launcher does pop out when I drag and drop in LibreOffice Writer, but that wasn't a big deal until it slid out and wouldn't go away. After reading this thread, I closed Writer and, sure enough, it auto-hid.

---

### Post by tm4rt on 2011-08-13
Is this still an offical bug?  I have ubuntu 11.4 and sometimes when libreOffice writer is open.. the launcher wont hide.

---

### Post by corpcleg on 2011-08-24
I can think of thousand s of Apps that I have run that make use of the left side of the screen with menus etc.And am strained to think of ONE that uses the RIGHT???????????
I dont know which is worse the fact that it was Put there or the fact that I cant seem to Move it!!!!!!!!!

Somebody dropped the ball on this one . I appreciate its opensource etc but if your goin to try and be Clever/Different at least let the USER decide whether its left there.

Sorry to be whinging but it just makes no sense to me

---

