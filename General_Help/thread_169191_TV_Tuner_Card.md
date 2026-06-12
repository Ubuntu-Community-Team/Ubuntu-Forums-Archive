---
title: "TV Tuner Card"
date: 2006-05-02
forum: General Help
---

### Post by zuccs on 2006-05-02
ok I have a Leadtek Winfast TV 2000XP TV Tuner Card, I think it might have been automatically installed as I can see "video0" in /dev/.

I have installed TVTime and selected appropriate area but when I try to "Scan channels for signal", it just goes through the stations 1-->65 and does not find anything. It also says "No signal".

I have plugged a pretty standard TV antenna into the right port on the back of the card also. I don't see why it won't pick up anything. I had a similar problem with a different card in Windows XP also. What am I doing wrong? Thanks again

---

### Post by dlai on 2006-05-02
did you try writing "mplayer /dev/video0" in the terminal? If this gives you a picture you got a mpeg2-encoder card ( I think). Then you have to install the ivtv-drivers...(maybe)

---

### Post by the_tiger on 2006-05-02
TV time will only show channels if the signal strength is strong enough. Use the menu to disable signal detection and use an internet transmitter guide to find the correct channels for your local station. Make sure you are using the correct signal frequencies for your country. I am fairly sure you can ignore the last post as I believe your card is based on the bt878 chipset. This should be automatically detected by ubuntu.

There is a guide based on your card here which you may well find useful.

[http://www2.truman.edu/~dat725/htpc2.html]("http://www2.truman.edu/~dat725/htpc2.html")

---

### Post by zuccs on 2006-05-03
hmm...thanks for the posts...

the_tiger i followed that guide and it all went very smoothly, i was sure it was going to work but i'm just getting the same problem...."No signal". I think the card is setup fine, there must be another setting or something more obvious.

I know the card works and with linux because I got it off mate who use to use it. And I use to have a TV in this room, so I'm fairly sure there is reception here too hehe. Any other ideas?

---

