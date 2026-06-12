---
title: "screen resolution problems"
date: 2009-11-01
forum: General Help
---

### Post by abrooks211 on 2009-11-01
Hello, I'm running the new version of Ubuntu in a virtual window through the program Virtual Box (by Sun microsystems), and I'm having problems putting Ubuntu in the right screen resolution. Right now it only gives me two options when messing around with the display (800x600 and something else), and says it can't find my monitor. Right now (in Windows Vista - my main OS) I'm using 1280x800, but I just don't have that option in Ubuntu. Is there any way to fix this? Thanks for any help in advance!

---

### Post by dbyjazz on 2009-11-01
run

```
gksudo gedit /etc/X11/xorg.conf
```

and paste this..

```
#Custom Xorg

Section "Screen"
    Identifier  "Screen0"
    Device      "Videocard0"
    Monitor     "Monitor0"
    DefaultDepth    24
       Subsection "Display"
                          Depth 24
                          Modes "1280x768"
                          Virtual 1280 768
       EndSubsection
EndSection

Section "ServerFlags"
    Option            "DontZap"    "False"
EndSection
```

but change the '1280x768' to your needed resolution

---

### Post by abrooks211 on 2009-11-02
Thank you for replying!

I did what you said, and restarted my virtual machine, and now there is something wrong with Ubuntu. Whenever I boot it up, it "flickers" and doesn't go to the normal login.
What I am seeing right now is just a black screen with the following text:

Ubuntu 9.10 alex-laptop tty1

alex-laptop login:



And whenever I try to log in I can't because half the time it doesn't register my typing, since it is flickering, so I can't tell if I typed my password in completely and correctly. Is there any way to fix this?

---

### Post by abrooks211 on 2009-11-15
Can anybody help me out?

---

