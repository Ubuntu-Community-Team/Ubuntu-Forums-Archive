---
title: "Terminal program just gives white screen"
date: 2009-12-14
forum: General Help
---

### Post by bamim2 on 2009-12-14
[SIZE=2]Sorry if I don't know the correct terminology (no pun intended) to ask an intelligent question. I'm brand new to Ubuntu Linux, but a long time UNIX user. 

The problem I'm having is that every time I try to run the Terminal "program" (Applications, Accessories, Terminal), all I get is a white screen with nothing on it. There's no text, no cursor, no boarder or anything. Just white. I can right click & change settings, but that doesn't actually do anything. How do I get the Terminal program to work? I'd like to be able to type some commands & ping some places etc. [/SIZE]

---

### Post by solar george on 2009-12-14
Thats odd, are you using graphical effects?
As a workaround you could try installing one of the other terminal emulators (try konsole or even the plain xterm)

---

### Post by bamim2 on 2009-12-14
Yes, I am using graphics effects. I've also modified my Xorg.conf file to get around my nVidia graphics card's crappy driver that would only let the display be set to 640x480. Now I'm in a higher graphics mode, but that's making the terminals not display correctly or at all. I've tried a couple of other terminal apps, but none of them work correctly.

---

### Post by solar george on 2009-12-14
have you tried any non-gtk terminal programs - these are mostly based on the gnome-terminal code?

---

### Post by bamim2 on 2009-12-14
Sorry. I don't know what that means. However, I've tried Konsole, Terminal & all of the terminal apps that I can find in the "Ubuntu download center" & none of them work for me.

---

### Post by solar george on 2009-12-14
hmm,
do your ordinary terminals work 
press ctrl+alt+F1 to get to tty 1
 then ctrl+alt+F7 to switch back to Xorg

---

### Post by bamim2 on 2009-12-14
Your question got me thinking (& it's only Monday!) so I turned off my graphics effects & that fixed it!! Thank you!

---

### Post by solar george on 2009-12-14
Yeah thats what I was thinking of to start with, would have been nice to be able to keep your effects though.
(btw. i feel you pain wrt to nvidia drivers)

---

### Post by bamim2 on 2009-12-14
Actually, now that I see this mode with my current driver settings, this is WAY nicer than what I had going on with the EFX.  This undoes a bunch of stuff I screwed up without knowing it. THX!

---

