---
title: "Nautilus/File Manager doesn't open in focus"
date: 2012-05-19
forum: General Help
---

### Post by robbiemacg on 2012-05-19
Nautilus/File Manager is not in focus when I open it via the Dash, Unity Launcher or a macro. A window will open on top of other open applications, blocking them from view, but that window is not in focus.

e.g. If I press Super + 1 right now, a window will open showing me the contents of ~/. That window will block my view of Firefox, it will be on top, but if I start typing, I won't be doing a quick find in that directory, I'll be typing in this text box. It's absolutely infuriating.

I've recently upgraded to Precise, and think this issue might be related to some of the changes to my system made during the upgrade. I've searched the forums for known bugs/problems, simple solutions, but have drawn a blank. Your suggestions and questions are very welcome.

Thanks,
Robbie

---

### Post by mc4man on 2012-05-19
I have a 10 wk. bug on this, mainly concerning opening nautilus when a terminal is open where nautilus almost always opens without focus but there are also other times when this occurs
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/945812](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/945812)

I'm not expecting this to be fixed any time soon, if ever (unless inadvertently from some other fix

---

### Post by robbiemacg on 2012-05-19
Thanks for the heads up, [mc4man]("http://ubuntuforums.org/member.php?u=320715"). We do appear to be encountering a similar issue. I won't double up, and file my own bug via Launch Pad. 
I agree with your suspicion that  the problem is in someway related to the Unity Shell.

---

### Post by philinux on 2012-05-19
> **robbiemacg said:**
> Thanks for the heads up, [mc4man]("http://ubuntuforums.org/member.php?u=320715"). We do appear to be encountering a similar issue. I won't double up, and file my own bug via Launch Pad. 
I agree with your suspicion that  the problem is in someway related to the Unity Shell.

Yep. Seen this behavior and the bug. It seems to happen on first run home folder. After that it gets focus.

---

### Post by robbiemacg on 2012-05-19
Regrettably, in my case, the behaviour is both persistent and consistent.
Regardless of how many times I open Nautilus/File Manager during a session; how I open the application; what other applications are running; the result is the same.
Have you any suggestions regarding how I should proceed? I suppose this might be too tricky a problem for us to develop a klugey solution to? I've been wracking my brain, but coming up short.

---

### Post by philinux on 2012-05-22
> **robbiemacg said:**
> Regrettably, in my case, the behaviour is both persistent and consistent.
Regardless of how many times I open Nautilus/File Manager during a session; how I open the application; what other applications are running; the result is the same.
Have you any suggestions regarding how I should proceed? I suppose this might be too tricky a problem for us to develop a klugey solution to? I've been wracking my brain, but coming up short.

Indeed I was wrong. Just subscribed to bug. [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/781931](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/781931)

---

### Post by mc4man on 2012-05-22
Hopefully they'll square that away at some point, the current bug, (mine was just duped to it), goes all the way back to natty.

At least here only saw on 12.04, started up during dev. I've applied the small gtk patch to the current gtk+3.0 source in 12.04 proposed & no longer see the problem  at all. Unfortunately  it's  a very large/long build (gtk+3.0), & may not be the intended or overall fix so i'd recommend waiting out for a while

---

### Post by robbiemacg on 2012-05-22
Thanks to you both for your input. I'm going to subscribe to that bug on Launch Pad, keep my eyes pealed for any updates/solutions coming down the pike.
While I don't necessarily have my solution, we've established that this is a know bug, that it's being worked on. As a result, I'm marking this thread [Solved].

Thanks again,
Robbie

---

