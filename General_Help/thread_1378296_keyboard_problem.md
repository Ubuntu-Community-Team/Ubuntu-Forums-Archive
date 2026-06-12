---
title: "keyboard problem"
date: 2010-01-11
forum: General Help
---

### Post by poderoso3009 on 2010-01-11
hello!

I have a Asus EEE 1000h with ubuntu 9.10 remix.
A problem on first asus eee's is the keyboard:
also just typed a letter once, the laptop writes it double (every 200 letters more or less). 
For example it looks like this while writing:
"thiss is a ttest" 

For Windows XP I found a way to fix it: i increased the time, that limits writing letters twice by fast typing. 
Its _not_ the time "Repeat Keys" Delay (Keyboard Settings "Key presses repeat when key is held down")! In fakt its the opposite:
It limits pressing the key to fast. (I hope you understand the problem *g)

Does anyone of you know, if there's something similar in Ubuntu?

thanks a lot!

---

### Post by poderoso3009 on 2010-01-17
Actually found the solution. (so far it seems to be fixed)

For all Asus EEE Users with bouncing key Problems:

> Terminal -> sudo gconf-editor
Desktop/Gnome/Accessibility/Keyboard
bouncekeys_delay 500
bouncekeys_enable on

Explanation for the Option (Wikipedia):
Bounce keys is a feature of computer Desktop Environments. It is an accessibility feature to aid users who have physical disabilities. Bounce keys allows you to configure the computer to ignore rapid, repeated keypresses of the same key.

---

