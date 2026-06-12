---
title: "Computer performance degraded. diagnostic ideas?"
date: 2009-09-17
forum: General Help
---

### Post by oomar on 2009-09-17
Umm recently my computer has started to become a lot slower. Fire fox seems to be maxing out at about 15? tabs and right now I have 22 and its just plain slow. Pretty much an average of 50% core usage constantly. Now Some people may read this and think that well duh its going slow.. you have too many tabs open. Well not true. I used to be able to have like 35-50 tabs with only around 25-35% core usage and had experienced little to no impact on the rest of the computers usage. Now everything is a little slow and occupationally applications like cheese fails to load. I've also noticed slower network speeds and logging in is slower as well. 
Really I would just like any advice of diagnosing the culprit, whether it is a firefox update that hasnt worked as well as it should or recently Ubuntu updated some important files and i defered to restart later. I really wouldn't like to have to re-install ubuntu to fix this speed problem and I can tthink of anything I could have installed to slow it down. Ugh just typing this is lagging. Anyway Thanks for any help.

---

### Post by lovinglinux on 2009-09-17
[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by oomar on 2009-09-17
ok i went there. great link! i did a few of those but nothing to really solve or diagnose this problem. 

I did a little experiment. I had it so it was running slow then closed tabs till it went down. 

I had 22 tabs open. The CPU usage was through the roof even when minimized. I closed 5 tabs. (so 17 were open) and it went down from like 54% to an average of under 10%. So I'm pretty sure its just the number of tabs... but its NEVER done this before. So I'm a little confused... any ideas?

---

### Post by lovinglinux on 2009-09-17
> **oomar said:**
> I did a little experiment. I had it so it was running slow then closed tabs till it went down. 

I had 22 tabs open. The CPU usage was through the roof even when minimized. I closed 5 tabs. (so 17 were open) and it went down from like 54% to an average of under 10%. So I'm pretty sure its just the number of tabs... but its NEVER done this before. So I'm a little confused... any ideas?

I don't believe is the number of tabs, but the content in the tabs. It's probably some javascript going nuts. For example, try to open 22 tabs with the Ubuntu forum page. I bet they won't use too much CPU.

---

### Post by undecim on 2009-09-17
It could be a script on a site you are on. I've had this happen to me before on sites that use heavy and poorly developed javascript or flash to display content. If you can narrow it down to one tab, then it's probably just scripts on that website.

EDIT: Yeah.. what lovinglinux said.

---

### Post by oomar on 2009-09-17
well im going to have to agree. And i remember which pages I closed and that would make sense. well problem solved i think. thanks guys! i didnt think about that.

---

### Post by tgalati4 on 2009-09-17
Install adblock and noscript and that will recover some of those CPU cycles.  They are yours after all.

Run firefox from a ramdisk.  That speeds it up as well.

[http://www.verot.net/firefox_tmpfs.htm](http://www.verot.net/firefox_tmpfs.htm)

---

