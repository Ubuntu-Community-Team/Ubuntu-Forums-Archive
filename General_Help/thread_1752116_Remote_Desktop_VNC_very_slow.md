---
title: "Remote Desktop VNC very slow"
date: 2011-05-07
forum: General Help
---

### Post by Jefferythewind on 2011-05-07
Hi Everyone,

  I have my desktop at home installed with  Ubuntu 11.04.  I set up remote desktop through the native remote desktop server program.  I can connect to the server from my remote Ubuntu 10.10 laptop, and it works*.  The problem is, it is painfully slow -> lags at least 5 seconds for every input.  

  Can anyone help me with this?  Are there any settings that I need to change?

Thanks in advance!

---

### Post by lmarmisa on 2011-05-07
How is the speed of the network you are using for connecting to the remote desktop?.

---

### Post by Jefferythewind on 2011-05-07
The speed at both the server and client are pretty good.  I have done windows remote desktop before over the same connections, and it works very speedy.

---

### Post by lmarmisa on 2011-05-07
I recommend this test. Connect both computers to your LAN and check if you get the same problems.

---

### Post by Jefferythewind on 2011-05-07
OK thanks, I will check that out once I get back home, then I will post my findings.

---

### Post by collisionystm on 2011-05-07
> **Jefferythewind said:**
> Hi Everyone,

  I have my desktop at home installed with  Ubuntu 11.04.  I set up remote desktop through the native remote desktop server program.  I can connect to the server from my remote Ubuntu 10.10 laptop, and it works*.  The problem is, it is painfully slow -> lags at least 5 seconds for every input.  

  Can anyone help me with this?  Are there any settings that I need to change?

Thanks in advance!

I have always had the same problem. The default remote desktop is garbage. I use remmina remote desktop. Its in the software center.

---

### Post by Jefferythewind on 2011-05-07
Thanks collisionystm,

  Do you still use the native remote desktop viewer from the client computer, or is there another viewer to go with that program?

*edit*

Sorry I just checked out the Remmina website.  It looks like it is just the client side program.

---

### Post by Jefferythewind on 2011-05-07
OK, so I installed Remmina, and it is much better.  It is actually usable, but still a little laggy.  I will continue to investigate...

---

### Post by jnorthr on 2011-05-07
some versions of vnc allow you to choose the color depth of the remote display so the fewer colors, the faster it updates - the less lag. See if you can try that.

---

### Post by CMDRSweeper on 2011-05-07
Well for my server I run the X11VNC with great success. It is not laggy at all, I have so far tried it via the web from a remote location and locally over Gigabit Ethernet, they work in a very similar manner. Getting it properly set up and starting up with Ubuntu is a bit tricky but doable however.

---

### Post by Jefferythewind on 2011-05-07
So I took the advice from Imarmisa, and I connect to the remote desktop from my own LAN, and it is still supper laggy.  So for the time being I think Remmina is working pretty good.  I guess I still need to play around with the settings to see if there is something optimal.  Thanks everyone for the help!

---

### Post by Jefferythewind on 2011-05-10
After trying to use Remmina for a couple days, it is very sluggish and the color and refresh doesn't work too consistently.  I will try the X11VNC suggested by CMDRSweeper.

---

### Post by lmarmisa on 2011-05-10
Do you know Teamviewer?.

I really like it.

[http://www.teamviewer.com/](http://www.teamviewer.com/)

---

### Post by Jefferythewind on 2011-05-20
OK, so I found a good solution.  It is called nx server, or [nomachine]("www.nomachine.com").

I haven't checked out TeamViewer, but it looks cool.

---

### Post by cscort on 2011-08-12
I was seeing pretty good performance with Ubuntu remote desktop until the latest updates. At the same time I got very bad performance from remote desktop as well as my samba shares broke. I need to see how I can back out of updates like these !!!!!! :(

---

