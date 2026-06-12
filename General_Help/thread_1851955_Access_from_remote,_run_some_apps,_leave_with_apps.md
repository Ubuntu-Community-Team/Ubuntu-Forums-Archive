---
title: "Access from remote, run some apps, leave with apps running"
date: 2011-09-29
forum: General Help
---

### Post by Sidrabs on 2011-09-29
Hello,

Time to time I need to access my work PC from home. It is running Ubuntu 10.04. Typically it has several virtual machines running on VirtualBox, and typically I access remotely those VMs (using LogMeIn), not the host PC. There is TeamViewer running on the host PC in case I need to access the host PC, though.

All if fine unless the VM I am working with crashes, and then TeamViewer crashes, too, when I try to reestablish my work environment. Then I am basically left without means to access my PC and I have to call up somebody in the office to help me out.

I'd like to set things up so that I can do it smarter. So, I've established VPN with my office. Now I can get on VPN, and access my PC via SSH terminal session.

I yet have to find out, how to run via terminal all the apps that let me start my work: TrueCrypt, VirtualBox, etc. Once the apps are running, I'd like to get off that SSH session, and get back to working as usual. However, the problem is, closing the session terminates all the running apps. So, the question is, how should I run those apps so that they stay running even when I close the session?

---

### Post by JCM_Pico on 2011-09-29
If you want to run an file you can make "./foo.sh &>foo.log &"
For a program theoretically it would work too "program &>program.log &"
this way you can leave the ssh session and append to a log file....

It works for me :P

---

### Post by Habitual on 2011-09-29
> **Sidrabs said:**
> ...I yet have to find out, how to run via terminal all the apps that let me start my work: TrueCrypt, VirtualBox, etc. Once the apps are running, I'd like to get off that SSH session, and get back to working as usual. However, the problem is, closing the session terminates all the running apps. ...

```
sudo apt-get install screen
```
run "screen" on local system, connect and do your business on the remote machine. Then Ctrl+A+D to disconnect the screen session and return back to your localhost. On a reconnect, just do a 'screen -ls' and then screen -x + 1 of the detached screen session identifiers 

If only 1 screen is run, then screen -x is sufficient to 'return' back to session-via-screen on the remote host.

[http://ss64.com/bash/screen.html](http://ss64.com/bash/screen.html)

HTH.

---

### Post by Sidrabs on 2011-09-29
Thanks, I'll go and check the manual how the screen works.

---

