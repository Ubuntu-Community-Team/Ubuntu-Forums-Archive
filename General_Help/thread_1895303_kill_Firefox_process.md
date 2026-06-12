---
title: "kill Firefox process"
date: 2011-12-14
forum: General Help
---

### Post by justinrpg on 2011-12-14
ok I have this issue where Firefox is running but not responding, how do I kill a process in Ubuntu? I know how to in Windows, but not Ubuntu! how do I do it, I am just a beginner

---

### Post by mikewhatever on 2011-12-14
Open the System Monitor, Processes Tab, select the process, click the End Process button.

No you know how to do it in Ubuntu as well. :~)

---

### Post by justinrpg on 2011-12-14
how do I find 'system monitor'? it isn't in 'system settings'! sorry I am a noob

---

### Post by Lars Noodén on 2011-12-14
One way is to search in the Dash for 'system monitor'  It will be one of the first items to pop up.  I agree that it is not the most intuitive or easiest ways of finding apps.

---

### Post by seawolf167 on 2011-12-14
You can also use top/htop (just as an FYI, there are many other ways as well...)

Open htop

```
htop
```

If not installed, you can install it with

```
sudo apt-get install htop
```

search for the process by hitting [F3] then typing in the name, once you find the process, hit 'k' to kill it.

---

### Post by WorMzy on 2011-12-14
```
killall firefox
```
or
```
killall firefox-bin
```

will normally do the trick.

---

### Post by larrypg on 2011-12-14
Hello,

Another easy and fast way is to open a term and then ps aux and then kill the pid of firefox

---

