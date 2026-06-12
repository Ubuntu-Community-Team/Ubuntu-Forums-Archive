---
title: "function similar to WIndows' &quot;repair internet&quot;"
date: 2011-07-26
forum: General Help
---

### Post by qwertyjjj on 2011-07-26
Does Linux have a "repair internet connection" function?
Every so often, particularly after using the hibernate function, I cannot open any webpages, etc. - not really sure what causes the problem.

---

### Post by FormatSeize on 2011-07-26
See [here](http://ubuntuforums.org/showthread.php?t=304654), and try the command given in post #5.

---

### Post by frankbooth on 2011-07-26
When hibernating you lose your network connection (since the computer goes to sleep).

Have you tried re-connecting through the Network Manager which can be found in the systray? You can access a quick-list by left-clicking the icon.

---

### Post by qwertyjjj on 2011-07-26
> **frankbooth said:**
> When hibernating you lose your network connection (since the computer goes to sleep).

Have you tried re-connecting through the Network Manager which can be found in the systray? You can access a quick-list by left-clicking the icon.

But it should just reconnect when I start it up again.

---

### Post by frankbooth on 2011-07-26
> **qwertyjjj said:**
> But it should just reconnect when I start it up again.

Yeah, it should. 
Have you looked for a bug report on Launchpad?

---

### Post by Mark Phelps on 2011-07-26
> **qwertyjjj said:**
> But it should just reconnect when I start it up again.

Yeah ... but ... I had this problem on several laptops, using several different Ubuntu versions, and not ONE was able to restart the network connection after "waking up".

I every case, I had to reboot cold to get the network back.

Caused me to take Ubuntu off two laptops -- since they were so slow that a cold reboot took ages to do.

---

### Post by Toz on 2011-07-26
> **qwertyjjj said:**
> Does Linux have a "repair internet connection" function?
Every so often, particularly after using the hibernate function, I cannot open any webpages, etc. - not really sure what causes the problem.

Perhaps the network card needs to be suspended prior to hibernate and resumed on thaw. Some system information would help. 

After a resume from hibernate where the network doesn't work, save copies of the following files:
- /var/log/pm-suspend.log
- /var/log/dmesg

After you've gotten the network working again (after a reboot), open up a terminal window, type in the following command, and post back the results along with the contents of the two files above:
```
lspci -vnn
```

Also, what is the make/model of your computer?

---

