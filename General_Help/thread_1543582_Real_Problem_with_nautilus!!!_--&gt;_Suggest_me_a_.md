---
title: "Real Problem with nautilus!!! --&gt; Suggest me a solution"
date: 2010-08-01
forum: General Help
---

### Post by hakermania on 2010-08-01
well, i have a problem with nautilus. It stacks all the time and I type
killall -v ping to unfreeze it
I realized that this way it unfreezes while it stacked and I had a network sniffer open, watching pinging packets to ping google. Well, since then, because I haven't find any solution to this problem I execute all the time killall -v ping in order nautilus to unfreeze.

A day, 2 months ago, when nautilus used to freeze but I didn't know about the 'ping [www.google.com]("http://www.google.com")' procces, I was trying to create a share to a folder named 'share' with samba etc., but when I was pushing the 'Create Share' button nautilus stacked all the time. Before 5 mins or something I remembered that and i pushed the 'Create Share' button. Nautilus stacked and I run killall -v ping. Nautilus unfreezed and that's what there was in the folder's properties window:
[CENTER][IMG]http://a.imageshack.us/img190/4418/screenshotct.png[/IMG]
[LEFT]What does this mean?
How can I fix it?
I have never never never edit nautilus documents or anything like this....
But, as I do remember now, I have made an application named 'net' that is pinging [www.google.com]("http://www.google.com") in order to check my internet connection easily. I know that there is another process named net at /usr/bin/net but I really don't know what the problem is... Does nautilus call the default net process by its name ('net') and so my process is running instead of the default 'net'???? 
[/LEFT]
[/CENTER]

---

### Post by dcstar on 2010-08-02
> **hakermania said:**
> well, i have a problem with nautilus. It stacks all the time and I type
........
But, as I do remember now, I have made an application named 'net' that is pinging [www.google.com]("http://www.google.com") in order to check my internet connection easily. I know that there is another process named net at /usr/bin/net but I really don't know what the problem is... Does nautilus call the default net process by its name ('net') and so my process is running instead of the default 'net'???? 


You do **not** have a problem with Nautilus, **you** have a problem with **you** making weird "applications" that clash with system functions that Nautilus seems to use.

Any solution seems obvious.

---

### Post by LowSky on 2010-08-02
check the coding of that 'net' application.

---

