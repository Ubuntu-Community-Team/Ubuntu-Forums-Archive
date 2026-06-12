---
title: "Failed to connect to the server using Nautilus 3.2.1"
date: 2011-11-09
forum: General Help
---

### Post by billzt on 2011-11-09
Today I suddenly failed to connect to my lab server using my own account through nautilus SFTP. The error reads like this:

[COLOR=Red]DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a   reply. Possible causes include: the remote application did not send a   reply, the message bus security policy blocked the reply, the reply   timeout expired, or the network connection was broken.[/COLOR]


Perhaps you may think something is wrong with my nautilus, my  network, my server machine, or my account. However, what really strange  thing is:
  (1) I am able to conntect to the server using **Dolphin**, the default KDE file manager. That means **there is no problem with my server machine, my account and my network**.
  (2) I am able to conntect to **another server** using Nautilus. That means **there is no problem with my nautilus**.
  So is it a paradox? By the way, this phenomenon happens just from today.


By the way, when I login to the server through terminal( Of course it is normal), I excuse " ps aux | grep zhut  ", (zhut is my account), I can see:


zhut      2350  0.0  0.0  53864  2000 ?        Ds   15:06   0:00 /usr/libexec/openssh/sftp-server
zhut      4171  0.0  0.0  53868  2008 ?        Ds   15:25   0:00 /usr/libexec/openssh/sftp-server
root      4320  0.1  0.0  90136  3292 ?        Ss   15:26   0:00 sshd: zhut [priv]
zhut      4323  0.0  0.0  90136  1816 ?        S    15:26   0:00 sshd: zhut@pts/9 
zhut      4325  0.5  0.0  66076  1600 pts/9    Ss   15:26   0:00 -bash
zhut      4388  0.0  0.0  65608  1000 pts/9    R+   15:26   0:00 ps aux
zhut      4389  0.0  0.0  61172   780 pts/9    S+   15:26   0:00 grep zhut
zhut     12474  0.0  0.0  53868  2000 ?        Ds   11:13   0:00 /usr/libexec/openssh/sftp-server
zhut     13139  0.0  0.0  53864  2004 ?        Ds   11:17   0:00 /usr/libexec/openssh/sftp-server
zhut     25622  0.0  0.0  54760  2008 ?        Ds   13:33   0:00 /usr/libexec/openssh/sftp-server
zhut     26059  0.0  0.0  53868  2020 ?        Ds   13:37   0:00 /usr/libexec/openssh/sftp-server
zhut     27947  0.0  0.0  53868  2000 ?        Ds   13:57   0:00 /usr/libexec/openssh/sftp-server
zhut     29874  0.0  0.0  53864  2004 ?        Ds   14:15   0:00 /usr/libexec/openssh/sftp-server
zhut     30500  0.0  0.0  53864  2000 ?        Ds   14:22   0:00 /usr/libexec/openssh/sftp-server
zhut     31980  0.0  0.0  54756  1996 ?        Ds   14:38   0:00 /usr/libexec/openssh/sftp-server


Opps, so many "/usr/libexec/openssh/sftp-server"! In fact every time I tried to connect to the server using Nautilus, it hangs up and I have to close it. Thus it remains there? Is it the problem? I don't know

---

