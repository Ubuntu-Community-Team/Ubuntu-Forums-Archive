---
title: "Updates seem to have damaged something"
date: 2012-03-29
forum: General Help
---

### Post by writebunny on 2012-03-29
Hello all, 

I was gone yesterday. When I got home last night and turned on the thinkpad r51, there was a long list of updates/upgrades to install. I clicked okay. They installed. I shut down the computer for the night. 

This morning, there was another update/upgrade. I installed. 

After this, suddenly, my internet connection said it was "on" but I couldn't find web pages. When I turned off the connection manually, it couldn't re-connect. Then I noticed my heat of the processor was getting very high - in the mid 50's C. I shut down completely. Then restarted. 

This keeps recurring however. If I do a simple restart, it won't resolve the problem. If I do a complete shut down and restart, the problem goes away for a little while, then begins agian. 

Seems this must be connected with those upgrades / updates from the Xubuntu system. 

What can I do to fix this?

PS: I accidentally hit that triangle with a ! Icon for the topic - can that be turned off? Sorry!

---

### Post by Elfy on 2012-03-29
IT's a bit hard to tell without knowing what upgrades there were.

Try looking in the history of synaptic - available from the File menu.

If not maybe look in the dpkg.log - open thunar - click File System and navigate to /var/logs - dpkg.log is in there.

It is possible that there was a kernel update - my 11.10 is on  Linux 3.0.0-15-generic - and it has not been updated for some time - if you have a newer one - try going to Previous versions at boot and booting the first one in there

> PS: I accidentally hit that triangle with a ! Icon for the topic - can that be turned off? Sorry!Done

---

### Post by writebunny on 2012-03-29
Thanks for helping and for fixing the icon. 

Synaptic doesn't list it in the history. 

I'm not finding Thunar. Is it supposed to be under Application menu > System?

I found application > system > update manager, but that doesn't have a history. :(

PS: I've refined my understanding of the order in which things happen:
First - the internet pages suddenly fail to load, although the network manager says I'm connected. 
Second - I click disconnect, then try to reconnect. 
Third - it hunts and hunts to connect and suddenly my processor temps starts going way up. 
Fourth - I tried connecting to an ethernet cable rather than wireless, but no difference.

---

### Post by writebunny on 2012-03-29
I'm sorry, but I can't find Thunar on here. Can anyone point me to the right place? I've googled about it, but I don't quite understand.

---

### Post by writebunny on 2012-03-29
I ask this in all seriousness, doesn't everyone get the same update prompts each day? (I'm a newbie)

---

### Post by LewisTM on 2012-03-29
Thunar = Xfce's file manager.
And security updates are released daily to everyone with recent Ubuntu versions, as you suspect.
It's possible a recent kernel update didn't go well with your hardware. To try an older version:
1) Reboot
2) Hold Shift during the boot process
3) A menu will appear, select Previous Linux versions
4) Select an older version and hit Enter.
If this helps, remove the packages in Synaptic that seem to be causing problems. Look for 'linux-image-3.0.0-XX-generic' 

Good luck!

---

### Post by Gremlinzzz on 2012-03-29
I m using Xubuntu did get a kernel update 3.0.0-17-generic
didn't mess anything up on me

---

### Post by Gremlinzzz on 2012-03-29
> **writebunny said:**
> Hello all, 

I was gone yesterday. When I got home last night and turned on the thinkpad r51, there was a long list of updates/upgrades to install. I clicked okay. They installed. I shut down the computer for the night. 

This morning, there was another update/upgrade. I installed. 

After this, suddenly, my internet connection said it was "on" but I couldn't find web pages. When I turned off the connection manually, it couldn't re-connect. Then I noticed my heat of the processor was getting very high - in the mid 50's C. I shut down completely. Then restarted. 

This keeps recurring however. If I do a simple restart, it won't resolve the problem. If I do a complete shut down and restart, the problem goes away for a little while, then begins agian. 

Seems this must be connected with those upgrades / updates from the Xubuntu system. 

What can I do to fix this?

PS: I accidentally hit that triangle with a ! Icon for the topic - can that be turned off? Sorry!

Which Xubuntu system are you using 11.10 or Xubuntu 12.04 Beta

---

### Post by brainwash on 2012-03-29
[QUOTE=writebunny]Then I noticed my heat of the processor was getting very high - in the mid 50's C.[/QUOTE]

You should check the task manager or run the **top** command (terminal). I'm pretty sure that some process will show high cpu utilization.

Like suggested by LewisTM you should try booting with the previous kernel version to track down the problem.

The output of
```
cat /var/log/apt/history.log
```
might be helpful as well.

---

### Post by writebunny on 2012-03-29
Thank you for helping. I'm going to read more about what you each suggested, because I need to understand more about how this all works --- but ---

It is possible this problem may have been fixed by an additional update I did an hour ago. I checked for new updates, found one, and installed it. I've been running the computer for 56 minutes now with no undesirable events. I'll keep watching it. 

For the record, I'm not running 12 yet. Looking forward to it though. 

Bear with me - I'll be testing out some of the suggestions you all gave. This is all good stuff for me to learn about even if the problem may now be resolved. (I sure hope it is!)

---

