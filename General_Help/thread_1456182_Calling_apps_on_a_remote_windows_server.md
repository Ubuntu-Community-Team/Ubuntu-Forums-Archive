---
title: "Calling apps on a remote windows server"
date: 2010-04-16
forum: General Help
---

### Post by greggc2006 on 2010-04-16
Hi, this is perhaps a strange one!!

My desktop is running 'buntu 9.10 and I have recently aquired a couple of half decent servers running Windows server 2003. I have a few windows app's that I use regularly for work that I have had limited success in running with wine or in vm's. 

I stumbled upon a how to to call apps in a vm to run seamlessly on the host desktop and did some playing and have succeeded in calling app's on my servers from my 'buntu desktop, the command I have set in my launcher for one of them (DIALux) is:-

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\DIALux\DIALux.exe" <servers IP address>:3389 -u username -p password
```

This works fine to launch the app.

My question is, can I change the default application/file association in 'buntu with a custom command so I can double click on a file and have it open in one of these remote app's??

If I can, what is the correct custom command to be using as using the above doesn't work at all, it just tries to open the file with rdesktop not the remote app.

---

