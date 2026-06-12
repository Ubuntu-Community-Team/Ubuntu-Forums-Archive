---
title: "Ibus &quot;no input window&quot; with certain programs only"
date: 2009-11-02
forum: General Help
---

### Post by dnova on 2009-11-02
After upgrading to Karmic, I've tried using IBus as my input method manager. In most programs, including Firefox and gedit, it works just fine, but in other programs (including TeXworks, my preferred LaTeX editor) I get "No input window" when I try to change keyboards. Any thoughts?

---

### Post by Shiranami on 2009-11-04
Same issue here. To add to previous, iBus also gives the "no input window" -message with kate, openoffice and amsn. Anyone have a solution?

---

### Post by ChoBolT on 2009-11-14
Same problem here, I can switch layout in all my programs but not in "nateon", a Korean Instant messaging.. Ibus says "no input window" :(

---

### Post by aquamammal on 2009-12-06
Me too. I can't even use it on Firefox.

---

### Post by Bernard Hurley on 2010-01-03
Try the following:

1]

Under System->Administration->Language Support

For "Keyboard input system" choose "ibus"

2]

Under System->Preferneces->Startup Applications
Click on "Add" and fill min dialog box as

Name:  iBus
Command:  ibus-daemon -drx
Comment:  the ibus demon

Now click "Add"

Note: all options in -drx are needed.
   -d makes ibus-daemon actually run as a deamon. 
   -x starts the ibus xim server so that applications that only use xim can use it
   -r this is more subtle. It re-starts ibus. If you don't have this, ibus will work OK the first time you log in. However when you log out ibus will still be running. When you log in again, "ibus-daemon -dx" will be called and will think "I'm already running so I don't need to do anything". The problem is that the running version of ibus expects a different gnome session (the one you logged out of) and as a result you won't see the ibus applet. It's actually still usable in this state, but its much nicer to have the applet. 

3]
Open .bashrc in an editor (e.g. gedit) and add the following lines:

   export GTK_IM_MODULE=ibus
   export XMODIFIERS="@im=ibus"
   export QT_IM_MODULE=ibus

Note: You can probably get away without [3], as far as I can make out it is only needed for some legacy apps that run in a terminal. But, what the hell, it doesn't do any harm!

---

### Post by jcpshd on 2010-03-07
Thank you very much, that last post worked for me. I can know write Japanese with Ibus.:D

---

