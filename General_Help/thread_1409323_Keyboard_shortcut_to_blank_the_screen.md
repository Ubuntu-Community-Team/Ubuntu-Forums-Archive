---
title: "Keyboard shortcut to blank the screen"
date: 2010-02-17
forum: General Help
---

### Post by sinter on 2010-02-17
Hi everybody, I'm new around here.

I have a little script stored in the file 'monoff.sh' that turns off my LCD. It contains the single line:
```
xset dpms force off
```When I click this file a popup asks if I want to run or display it. If I choose run it turns off my monitor and it's all good. But I also added a keyboard shortcut (System->Preferences->Keyboard Shortcuts) that should run the file with the command above.
And now the problem: when I use the keyboard shortcut my screen goes blank for half a second but turns right back on. What am I doing wrong?

My system:
Ubuntu 9.10 2.6.31-19 x64
Dell Vostro 1400 laptop
Nvidia driver 185.18.36

---

### Post by sinter on 2010-02-19
Bump. I noticed this only happens if I have some audio playing in totem, vlc or some firefox plugins. If I run the command file from the terminal it works but if I run it with the keyboard shortcut the monitor turns back on in a second. If I run the file with the keyboard shortcut a few more times it takes a bit more but the monitor turns back.

Can anyone test this behavior for me on their systems? It takes only a minute to set it up like I described it in my first post. Just test the keyboard shortcut with and w/out some audio playing. Thanks a bunch.

---

### Post by stinkeye on 2010-02-19
Try ```
sleep 1 && xset dpms force off
```
It's probably recording the key as you release it thus bringing the screen back on.

---

### Post by sinter on 2010-02-19
Thank you. It doesn't explain why it's happening only while some audio is playing but it works!

---

### Post by stinkeye on 2010-02-19
Stays off when I'm using rhythmbox, vlc or Movie Player.

---

### Post by sinter on 2010-02-19
If I put  "sleep 1" in the command it stays off while playing audio for me as well, but without it it doesn't. Thanks again.

---

