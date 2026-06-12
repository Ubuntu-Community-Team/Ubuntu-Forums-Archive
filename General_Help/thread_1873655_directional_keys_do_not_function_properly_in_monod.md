---
title: "directional keys do not function properly in monodevelop"
date: 2011-11-01
forum: General Help
---

### Post by zizzdude on 2011-11-01
I'm running Monodevelop 2.6 for my general developing on Xubuntu 11.10. For some reason, however, when editing in the source code and use the directional keys (up,down,left, and right) to attempt to navigate through the code, the cursor focus will jump from the editing section (the center) to the different panels (such as Solution,Class,Files,etc.) I haven't had this happen before. Is there a way to fix this?

Thank you.

---

### Post by HidekiAI on 2012-02-17
I thought I was crazy (I had figured it must only be on my laptop) so I tolerated this issue.  I'm glad I'm not insane and others are having this issue.

Mine is on regular (Gnome) Ubuntu 11 (at the time of this writing, lsb_release reports back as 11.10) and whenever I hit the cursor, in particular Up arrow, the focus switches to the toobar buttons.  It's kind of frustrating when coding because I constantly have to click on the mouse to the edit window to refocus my cursor back to where my code is...

Incidentally, Mododevelop running on my Gentoo (in Gnome) does not happen, and I've tried Monodevelop on Windows 7 and it didn't do this either...

My Gentoo's version is 2.8.5.1 while my Ubuntu version is 2.6;  The Windows version I've tried was (I believe) 2.8.6.4...  I have all of them set to key-binding to Visual Studio.

I might try to see if I can run 2.8.x on my Ubuntu, but in the meanwhile if anybody knows what possible solution can resolve this, please let me know.  At first I thought it could be because I'm using "Classic" instead of Unity, but because the original poster claims issues with Xfce, I figure it cannot be my desktop issue (and before I switched to Gnome on my Gentoo, I was using Xfce4 on Gentoo and it had no issues)

Sincerely,
Hideki A. Ikeda
[B]
Addendum/Update[/B]: *I've just finished building 2.8.6 on my Ubuntu laptop (from the GitHub), and the cursor issue seems to have been resolved.  So far, I seem to be able to edit with intellisense and autocomplete, compile and debug (step, run, break, etc) without any issues*.
**Update #2**: *By the way, I also do have iBus enabled (which apparently has some issues with Monodevelop).  Although that generally means programmers and developers that needs iBus to do localization is screwed unless they upgrade to 2.8.x*

---

