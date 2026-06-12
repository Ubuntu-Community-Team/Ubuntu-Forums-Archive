---
title: "KDE issue: Enforcing desktop margins"
date: 2011-05-31
forum: General Help
---

### Post by Mariane on 2011-05-31
I don't think I've messed up my settings because this is happening on both my computers. But it is still always a possibility. 

When I open a program, whether by command-line or by clicking somewhere, the windows don't always open completely inside the available desktop space. I mean the total space minus the task bar along the bottom. Firefox always opens with the bottom margin unreachable. kdenlive opens half out of the screen towards the right and the bottom. 

It is easy to drag them back where they belong, but always having to do this, with eventually a resize needed, to see the whole window of the program is getting tedious. 

Is there a way to say it's OK to open over another window but not OK to open under the task bar or out of the screen? 

Mariane

---

### Post by Zorael on 2011-05-31
Hmm. You could perhaps create a window rule and have it enforce Placement of new windows. See the attached screenshot for the available options. I think Smart puts it in an empty space, and Centered is pretty obvious.

The tricky part is figuring out how to match the windows you want this to affect. If it's only Firefox and Gimp, you could probably set Window Class to Regular Expression: **firefox|gimp**. Use that Detect Window Properties button and the terminal **xwininfo** command to get properties of windows.

If it happens to pretty much every program, you could perhaps set everything to Unimported except Window Type to Normal Window. That's a pretty broad sweep though.

Note that this probably won't help if the windows end up too large for your screen. :<

---

### Post by Mariane on 2011-06-01
Thank you. I installed it by installing the package kdeadmin. But I didn't find how to launch it. I'm sorry if that is a stupid question... typing "kcontrol" or "kdeadmin" says "command not found" and it appears neither in "Application/System" nor in "System settings". "Application/Settings/System settings" just launches "System settings". Rebooting didn't help. 

```

kstart --window --windowclass kcontrol

```

Returned without error messages but did nothing. 

I found a bug report dating from 2008: 
[https://bugs.kde.org/show_bug.cgi?id=169175](https://bugs.kde.org/show_bug.cgi?id=169175)
Doesn't look promising... 


Mariane

---

