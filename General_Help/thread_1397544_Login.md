---
title: "Login"
date: 2010-02-03
forum: General Help
---

### Post by uuuubunt2 on 2010-02-03
Yesterday I did a clean install of xubuntu 9.10. I set up an account for my wife on it and now everytime I try to login under my own it keeps going back to the login screen. Sometimes twice last night I had to log in 4 times before it went to the desktop. I have played with some live CD's of ubuntu and xubuntu, but this is the first full install I have done. Before I set up the wife account, I could login first time. Should I try and reinstall and hope for the best or is there something in terminal that could be done?

---

### Post by Vaphell on 2010-02-03
going back to the login screen means that the gui layer crashes and restarts - usually that means some gfx driver problems. What's your hardware

---

### Post by cjhabs on 2010-02-03
Did you set up your wife's account to use the same home folder as yours? If so, it could be a permissions issue.

---

### Post by uuuubunt2 on 2010-02-03
the paths are:
/home/wife
/home/mine

not really sure on the graphix card since this is an older comp
but have 64.4gb avail on hdd and 465mb memory processor is amd sempron 3000+

---

### Post by Vaphell on 2010-02-03
run lspci from terminal and look for anything related to vga

---

### Post by uuuubunt2 on 2010-02-03
here is the vga section of the command

```

01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)


```

---

### Post by uuuubunt2 on 2010-02-03
i still cant understand why my grfx card would be the problem with logging in with 2 users set up. mind as well as scope the net and forums to get a better handle on xubuntu.

---

### Post by Vaphell on 2010-02-03
well, considering your system is fresh you can try to install it again. 
You can also try some older version (9.04 for example) to see if it's more stable/hassle-free?

if the gfx is the problem then it doesn't really matter how many accounts are there. Graphical environment simply crashes during loading phase and starts again in loop - that's why you get login screen again. I am not saying that this is the root of the problems in your case though.
If you have some via driver loaded, try to see if changing it to vesa in 800x600 makes system more stable (vesa is a legacy mode supported by all VGAs, it's slow as hell but at least it should be rock solid) - that would indicate problems with gfx driver. Unfortunately i can't give accurate suggestions, because i am not too familiar with 9.10, not to mention xubuntu flavor. May the google be with you :/

---

### Post by uuuubunt2 on 2010-02-03
thanx for the suggestions though, i do plan on upgrading the grfx card on ram at a later time, may just deal with it unless it aggrivates me more. besides wife has pw to mine if need b no biggie

Plus i have a live cd of ubuntu, dont know version of it though, may try dual boot it

---

