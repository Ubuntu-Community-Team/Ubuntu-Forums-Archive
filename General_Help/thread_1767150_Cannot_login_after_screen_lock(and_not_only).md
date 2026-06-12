---
title: "Cannot login after screen lock(and not only)"
date: 2011-05-25
forum: General Help
---

### Post by Vahagn_IV on 2011-05-25
Hello all.

I used ubuntu for the past 3 years and never had serious problems. Say, my laptop was not switched off for 6-7 months(I put it to suspend).  However, after the last upgrade to 11.04 several problems appeared.
[LIST=1][*]Sometimes (didn't notice any regularity)I cannot login after the screen off. What I can do is only move the mouse pointer on the black screen. The box for username and password does not appear. The only way out is to press Ctrl+Alt+F1 and restart computer by "shutdown" command.
[*]Sometimes the computer logs off unexpectedly. Here there is some regularity. Usually it takes place when I press on a link in "Chrome".
[*] I have only 2 desktops and there is no way to add more 2(in order to use compiz cube). 
[*] Laptop stopped to suspend when the lid is closed. Here I've noticed a regularity. If I suspend it manually and then log in, then it works perfectly. However, after restart the problem appears again.
[/LIST]
There are also some less important problems like that the goldendict's icon stopped to appear in cairo-dock notification area. I have to restart the applet (or , more often the cairo-dock itself) to make it appear there.

Please, tell me what to do. Thanks in advance.

P.S.
OS:Ubuntu 11.04(64 bit), 
Computer: HP Compaq 6720s.

---

### Post by Vahagn_IV on 2011-05-26
bump?

---

### Post by HanDez on 2011-07-06
I was having the same issue with the screen lock when I found your query, although I was able to just type my pswrd and then hit enter and the screen came back.

I found that it was the "Advanced Compiz Config Settings Manager" that I had installed that was causing the problem.

I uninstalled it and did a reboot and all was well like before.

What really led me to this was that my "screensaver preferences" was not responding  when I went into it, it would not respond to my selections until i closed it and then opened it again to find that what I had clicked before had changed. Then only to find the GUI unresponsive again.

I thought about what changes I had made that could have affected things, and "Advanced Compiz Config Settings Manager" was the culprit.

---

### Post by HanDez on 2011-07-06
Also, fresh install FTW, I find the online upgrades to be a bit buggy.

---

