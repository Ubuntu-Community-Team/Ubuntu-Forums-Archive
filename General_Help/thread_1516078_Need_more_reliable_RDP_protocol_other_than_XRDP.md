---
title: "Need more reliable RDP protocol other than XRDP"
date: 2010-06-23
forum: General Help
---

### Post by CorvetteFan86 on 2010-06-23
Hello all. I installed ubuntu server 10.04 32-bit and I installed XRDP so I can connect to it using RDP sessions. I was wondering if there is a better alternative to it. I have the following issues with it: 1. When I connect to the server locally using rdp it works just fine the first time. Then when I close the session I cannot connect to it again (it says connection timed out). Then if I uninstall then reinstall it will work again for another time then do the same thing. 2. I receive a protocol error when using Windows 7 or RDP version 6.1.7600 (Newest RDP version) Does anyone have any ideas?

Thanks,
Thomas

---

### Post by dcstar on 2010-06-24
> **CorvetteFan86 said:**
> Hello all. I installed ubuntu server 10.04 32-bit and I installed XRDP so I can connect to it using RDP sessions. I was wondering if there is a better alternative to it. I have the following issues with it: 1. When I connect to the server locally using rdp it works just fine the first time. Then when I close the session I cannot connect to it again (it says connection timed out). Then if I uninstall then reinstall it will work again for another time then do the same thing. 2. I receive a protocol error when using Windows 7 or RDP version 6.1.7600 (Newest RDP version) Does anyone have any ideas?

Thanks,
Thomas

```
man sesman.ini
```

---

### Post by CorvetteFan86 on 2010-06-24
So I assume you want me to change something since you had me lookup the explanation of the ini file? Which value/s do I need to look at?

Thanks,
Thomas

---

### Post by dcstar on 2010-06-25
> **CorvetteFan86 said:**
> So I assume you want me to change something since you had me lookup the explanation of the ini file? Which value/s do I need to look at?

Thanks,
Thomas

What does it say about disconnection - the issue you are complaining about.

---

### Post by lukeiamyourfather on 2010-06-25
I'm not familiar with xrdp so can't help with the specific issue. Though there are other tools like x11vnc that serve the same purpose. If you're using xrdp so Windows clients don't have to install anything, there are free and open source VNC clients for Windows that don't require any installation like UltraVNC (just uncompress the archive and open it). There is also an installer for UltraVNC if desired. Cheers!

---

### Post by CorvetteFan86 on 2010-06-25
> **dcstar said:**
> What does it say about disconnection - the issue you are complaining about.

The only thing I saw about disconnection in the man and .ini file was KillDisconnected and DisconnectedTimeLimit. Both of them by default are set correctly. Here is my sesman.ini file for reference:

[Globals]
ListenAddress=127.0.0.1
ListenPort=3350
EnableUserWindowManager=1
UserWindowManager=/etc/xrdp/startwm.sh
DefaultWindowManager=/etc/xrdp/startwm.sh

[Security]
AllowRootLogin=1
MaxLoginRetry=4
TerminalServerUsers=tsusers
TerminalServerAdmins=tsadmins

[Sessions]
MaxSessions=10
KillDisconnected=0
IdleTimeLimit=0
DisconnectedTimeLimit=0

[Logging]
LogFile=/var/log/sesman.log
LogLevel=DEBUG
EnableSyslog=0
SyslogLevel=DEBUG

[X11rdp]
param1=-bs
param2=-ac

[Xvnc]
param1=-bs
param2=-ac

---

### Post by dcstar on 2010-06-26
> **CorvetteFan86 said:**
> The only thing I saw about disconnection in the man and .ini file was KillDisconnected and DisconnectedTimeLimit. Both of them by default are set correctly. Here is my sesman.ini file for reference:
........
[Sessions]
MaxSessions=10
**KillDisconnected=0**
IdleTimeLimit=0
**DisconnectedTimeLimit=0**

........

If **you** are having problems with disconnection then **you** should change these things to try and fix **your** problems.

---

### Post by lukeiamyourfather on 2010-06-26
> **dcstar said:**
> If **you** are having problems with disconnection then **you** should change these things to try and fix **your** problems.

Nice attitude, I'm sure it makes everyone feel warm and fuzzy inside. :-|

---

### Post by CorvetteFan86 on 2010-07-03
> **lukeiamyourfather said:**
> Nice attitude, I'm sure it makes everyone feel warm and fuzzy inside. :-|

Thanks Luke. Dcstars two cents hasn't helped yet blaming me I need to troubleshoot it. Like I thought all along no matter what I change (Disconnect to 1) or (Amount of time to disconnect to 1 so they do not keep the session open) it still will not let me reconnect afterwards. I found the only way for it to start working again is to restart my computer (Not Practical!). I have taken some advice and just decided to use VNC. The only issue is if I have the server restart I cannot log in until I log in on the physical machine. Does anyone know of a way to fix this?

Thanks,
Thomas

---

### Post by gcmartin on 2010-07-17
@CorvetteFan86 Am I to assume that you did [this]("http://http://www.liberiangeek.net/2010/07/connect-ubuntu-10-04-lucid-lynx-remote-desktop-windows-machines/"); only to find out that you cannot start a 2nd session with the Ubuntu server after completing the 1st session when using your Windows RDP client? 

If so, do you have a XP/2000 machine that you can/have test with on your LAN?

Trying to understand...

---

### Post by CorvetteFan86 on 2010-11-20
> **gcmartin said:**
> @CorvetteFan86 Am I to assume that you did [this]("http://http://www.liberiangeek.net/2010/07/connect-ubuntu-10-04-lucid-lynx-remote-desktop-windows-machines/"); only to find out that you cannot start a 2nd session with the Ubuntu server after completing the 1st session when using your Windows RDP client? 

If so, do you have a XP/2000 machine that you can/have test with on your LAN?

Trying to understand...

@gcmartin

When I initally install xRDP it works great. But after the first time I disconnect from it working it won't work at all until I reinstall the software. I thought it had something to do with the option to disconnect at log off in the xRDP configuration settings but, no matter what I change it does the same thing.

---

### Post by wreed on 2010-11-25
Did you ever get this problem resolved?
 
I am having the same issue, I can connect once, log off.  When I try to RDP again with Windows Remote Desktop I get the xrdp login box but then when I click ok, it hangs....
 
Thoughts?   If I reboot the machine I can get back in once but not again, same as above.

---

### Post by CorvetteFan86 on 2010-11-25
> **wreed said:**
> Did you ever get this problem resolved?
 
I am having the same issue, I can connect once, log off.  When I try to RDP again with Windows Remote Desktop I get the xrdp login box but then when I click ok, it hangs....
 
Thoughts?   If I reboot the machine I can get back in once but not again, same as above.

Unfortunately, I have not. I ended up redoing my server with an upgraded motherboard that supports raid 1+0 (Which isn't support in ubuntu server natively. Only 0, 1 and 5 are.) So I went back to Windows Server. I hope someday this does get fixed because VNC is not a secure solution compared to RDP. And since 95% of the computers I use (Including I work with are Windows) this would help out tremendously.

---

### Post by Dorowan on 2010-12-06
Do you have to use RDP Clients? You could consider [www.nomachine.com](www.nomachine.com) as an alternative. It is really fast compared to vnc and they have Windows and Linux Clients.

---

### Post by gonzalov on 2011-07-07
Seems like an old thread, but I have my *provisional* two cents.

Ubuntu 10.04.1, installed xrdp which installs vnc4server. Had exactly the same problem as described above using WinXP client. So I did the following which does restore the service without rebooting:

```

service xrdp stop
rm /var/lock/xrdp/sesman.ini
service xrdp start

```

(all with sudo, of course)

And now you can login again.

I have no idea why this works or what is happening but AFAIK, xrdp gets "stuck", you need to restart it, but pidfile remains in place when you stop (smells like a bug), so you can't restart until you rm pidfile. Once done, you restart and xrdp works ok... for just one more time.

As for the (warm and fuzzy) dcstar's suggestions about sesman.ini, this doesn't seem to work since -as is noted in man page- "this options are currently ignored!", which still seems to be true.

Any better ideas for a definitive solution? Thanks!

---

