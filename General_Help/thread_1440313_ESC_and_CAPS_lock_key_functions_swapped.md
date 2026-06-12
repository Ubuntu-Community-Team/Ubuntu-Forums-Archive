---
title: "ESC and CAPS lock key functions swapped"
date: 2010-03-27
forum: General Help
---

### Post by valar on 2010-03-27
hi i am using ubuntu7.10. my ESC key and CAPS lock key functions got interchanged..when i use WINDOWS  the keys perform their normal functions.. i dont know why their functions got interchanged in ubuntu.. pls help me out.

---

### Post by labinnsw on 2010-04-03
The easiest solution I can think of is to install keytouch editor and keytouch. Use keytouch editor to reassign the key functions and use keytouch to apply the settings. If all goes well, keytouch should apply the setting whenever the system restarts. If that is not the case, you can add ```
keytouchd
```(Copy and paste) to the start up applications in your session manager. (Symtem >> Preferences >> Sessions)

---

### Post by HermanAB on 2010-04-03
Hmm, I have on occasion had the keyboard mess up on me.  Once the capital T stopped working for no good reason.  This is due to a configuration setting in X getting messed up, but goodness knows why.

One can fix problems like this using Xmodmap.  Here is a paragraph that I wrote to fix a keyboard issue wiht my Eee PC:


Right Hand Control Key

I tend to do a lot of one handed typing while holding the Eee PC in my left hand. The Firefox Zoom keys are 'Ctrl+' and 'Ctrl-', which I also use a lot while browsing. Even with my huge paws that can span 12 notes on a piano, I still find the missing right-hand control key to be annoying.

The solution is to use 'xmodmap' to remap the useless 'Menu' key (between 'Alt' and 'Home') to 'Control'. This can be done by creating a small configuration file and calling 'xmodmap' from '.bash_profile'. This way the key will be remapped each time you log in.

Press 'ctrl-alt-t' to open a X terminal and create the file '.keymap' in '/home/user' using 'nano':

keycode 117 = Control_R
clear Control
add Control = Control_L Control_R

Then edit '.bash_profile' with 'nano' and add the following line to the bottom:

xmodmap .keymap

Next time you log in, this command will execute automatically, but for this session, you have to execute it manually:

$ xmodmap .keymap

There you go, the useless 'Menu' key is now a 'Control' key.

In case you were wondering, you can get the mystical key codes with 'xev'.

---

