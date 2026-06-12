---
title: "Ctrl-C in Matlab crashes Ubuntu"
date: 2010-05-03
forum: General Help
---

### Post by GraduateStudent on 2010-05-03
Hi all,

I installed a student version of Matlab 7.0.1 (R14) onto Ubuntu 9.10 (Karmic Koala) and it generally works fine.  But when I press Ctrl-C in the command window (to halt execution of a Matlab loop), I am immediately taken to the Karmic GDM login screen (and when I log back in, all my windows and unsaved data are gone).

Can anyone think of a reason why pressing Ctrl-C in Matlab would crash the whole system?

---

### Post by GraduateStudent on 2010-05-04
Bump... any ideas?

---

### Post by sbergman on 2010-05-05
Hmm.... try pressing Ctrl+C when you're not in Matlab and see if the problem arises.

As a suggestion: Check if the Ctrl+C hotkey combination is already assigned to do another task. (Sounds like a complete logout or a restart of the x-server from what you're describing).

To do this on my distro I go to System -> Preferences -> Keyboard Shortcuts. 

Just scroll through the list and check if there's anything with Ctrl+C

Another suggestion is to go through Matlab's list of keyboard shortcuts and see what Ctrl+c does there. In Matlab: click on File -> Preferences -> Keyboard -> Shortcuts

In the past I have found some of Matlab's keyboard shortcuts to be pretty weird when I first installed it on linux (for eg: Alt-w means copy and Alt-y means paste or something of the sort).

---

### Post by XCan on 2010-05-05
> **sbergman said:**
> 
In the past I have found some of Matlab's keyboard shortcuts to be pretty weird when I first installed it on linux (for eg: Alt-w means copy and Alt-y means paste or something of the sort).

Indeed, by default on *nix, Matlab installs with the so called "emacs-like shortcuts". However, ctrl+c should really override those shortcuts when trying to break a loop/run.

---

### Post by drs86 on 2011-02-21
Confirmed. I have exactly the same problem with MATLAB 7.1.0.21 (R14SP3) on Lucid x86. I tried changing to the &#8220;Windows&#8221; key bindings option in Preferences and it doesn&#8217;t help. I also checked my system keyboard bindings as sbergman suggested and nothing is set for Ctrl-C.

I checked /var/log/messages and found the following entry:

kernel: [178322.593231] nautilus[31085]: segfault at 20 ip 0081e17f sp bf86e300 error 4 in libgobject-2.0.so.0.2400.1[7f4000+3d000]

I&#8217;m not familiar enough with the stuff under the hood to know how to go about resolving this issue. Can anybody help?

---

### Post by drs86 on 2011-02-23
Bump

---

### Post by Atcold on 2012-03-06
> **sbergman said:**
> Hmm.... try pressing Ctrl+C when you're not in Matlab and see if the problem arises.

As a suggestion: Check if the Ctrl+C hotkey combination is already assigned to do another task. (Sounds like a complete logout or a restart of the x-server from what you're describing).

To do this on my distro I go to System -> Preferences -> Keyboard Shortcuts. 

Just scroll through the list and check if there's anything with Ctrl+C

Another suggestion is to go through Matlab's list of keyboard shortcuts and see what Ctrl+c does there. In Matlab: click on File -> Preferences -> Keyboard -> Shortcuts

In the past I have found some of Matlab's keyboard shortcuts to be pretty weird when I first installed it on linux (for eg: Alt-w means copy and Alt-y means paste or something of the sort).
I love you m8!

It was awful to remember to press Alt+W for Copy, Ctrl+W for Cutting, Ctrl+Y for Pasting and Ctrl+Shift+Minus for Undoing! Fortunately, in the path you mentioned (File -> Preferences -> Keyboard -> Shortcuts) there is the option to switch from Emacs Default Set shortcuts to Windows' ones.

Many thanks indeed!

---

