---
title: "Caps lock inverted"
date: 2011-08-04
forum: General Help
---

### Post by Tzaratte on 2011-08-04
[FONT=Century Gothic]Hello, thank you very much for receiving me  :)  I hope I am posting in the correct place.

Got the following problem, which is quite annoying:[/FONT] [FONT=Century Gothic]

From time to time it looks like caps lock gets enabled by itself, inverting its normal way.  Right now, I am writing with my caps locked on (showing the caps light), and if I turn them off, WRITING COMES THIS WAY. [/FONT] [FONT=Century Gothic]

I don't know what to do.  Looking for an answer, found this post [/FONT] *[FONT=Century Gothic][COLOR=RoyalBlue][here]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10924170")[/COLOR][/FONT]*[FONT=Century Gothic].  It says is solved, unfortunately I don't understand what was done in there. 

Last time this happened to me, some months ago, I even bought a new keyboard and a new mouse and finally it went to normal just the way it came, one day just automatically. [/FONT] [FONT=Century Gothic]

Could anybody help me with this, please?  I am a complete newbie in Ubuntu although it's been a while since I finally got the courage to fully migrate from windows.  I feel so proud because now I am able to do a lot of things, however, still am a donkey with the terminal, it's been hard for me to understand it.  I have a desktop computer working with Ubuntu Lucid 10.04. [/FONT] [FONT=Century Gothic]

Thank you very much for your kind help. [/FONT]  :)

---

### Post by MDguy on 2011-08-04
Try installing the program "xdotool", which will invert the state of the caps lock key without affecting the light on your keyboard.  To install it, open a terminal (Ctrl+alt+t) and run:
```
sudo apt-get install xdotool
```Then enter your password and hit Enter.

To switch the state of your caps lock key, run:
```
xdotool key Caps_Lock
```

---

### Post by Tzaratte on 2011-08-05
[FONT=Century Gothic]Oh great!!!  It changed the caps !!!  Thanks MDguy, you're an angel ... !!! 

I guess then that I just need to run **xdotool** in terminal each time the caps lock invert, isn't that right?

Well, again, thank you very, very much for your help.  I'm so glad to have joined Ubuntu Forums and hope one day I could be of help to someone just as you have so kindly been to me.  Thanks !!![/FONT]

:-D :D

---

