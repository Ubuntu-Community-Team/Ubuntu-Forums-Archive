---
title: "LTSP Problem with thin client"
date: 2010-09-08
forum: General Help
---

### Post by tommyold85 on 2010-09-08
Hi
I have a problem using LTSP.
I successfully installed Ubuntu 10.04 server LTSP mode.
Until here everything ok. Then i create a user, very simple.
After that i start a thin client, boot from the network then i reach the login window.
Ok, then insert the user credentials and the login is successful.
From then on, the client crashes because you see the desktop background and nothing else. Then i restart the client, i try to login and the desktop is loaded. It seems to go alright but ....all  commands are displayed backwards (as if they were in front of a  mirror), not enough i can't click with the mouse or use the keyboard  ....
[COLOR=#000000]How do I run this damn client? ](*,)[/COLOR]

---

### Post by jeight on 2010-09-08
The mirror problem is caused by your proprietary video driver. Disable that device and then sudo ltsp-update-image. Should fix the problem. Other than that the only program that causes LTSP to crash is controlaula.

---

### Post by diablo2nd on 2010-09-08
I'm jumping on the bandwagon too here. Following the advice in this thread, I got my client displays working like a charm. So the next question is, I intend on using the server as a workstation too. (Not for your everyday users, for the administrator, me)  How can i go about using the proprietary drivers on host only? I tried setting XSERVER=vesa in the lts.conf file but that made big problems with the clients - they were not starting. MY understanding is that vesa should work for anything?  

Also seen this - have not tested it yet though. will this work? Is there a better way?

Cole

---

### Post by tommyold85 on 2010-09-09
> **jeight said:**
> The mirror problem is caused by your proprietary video driver. Disable that device and then sudo ltsp-update-image. Should fix the problem. Other than that the only program that causes LTSP to crash is controlaula.

Great!!!Now[COLOR=#000000] it seems that everything work!!!Thank you!!!
[/COLOR][COLOR=#000000]Another thing,[/COLOR][COLOR=#000000]i installed the thin client manager[/COLOR],[COLOR=#000000]but when a client connects [/COLOR][COLOR=#000000]the manager doesn't show it.
Why?

[/COLOR][COLOR=#000000]Problem solved[/COLOR],[COLOR=#000000]there is a topic about this:

[/COLOR][http://ubuntuforums.org/showthread.php?t=1336101](http://ubuntuforums.org/showthread.php?t=1336101)

---

### Post by tommyold85 on 2010-09-13
Another problem :cry:
[COLOR=#000000]if i connect my PC to the server[/COLOR] everything works smoothly.
[COLOR=#000000]If i connect another laptop[/COLOR], LTPS hangs[COLOR=#000000] in the loading screen of ubuntu.
[/COLOR][COLOR=#000000]I have to edit the LTS.conf file for this laptop?[/COLOR]

---

### Post by jeight on 2010-09-21
The problem with the thin client hanging at the load screen deals with the NBD proxy not working properly. This patch works for some people, but I had to go disable the nbd proxy manually on my server. [https://bugs.launchpad.net/ltsp/+bug/589034](https://bugs.launchpad.net/ltsp/+bug/589034)

---

