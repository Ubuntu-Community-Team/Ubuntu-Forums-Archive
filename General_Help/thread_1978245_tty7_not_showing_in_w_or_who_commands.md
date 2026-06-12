---
title: "tty7 not showing in w or who commands"
date: 2012-05-11
forum: General Help
---

### Post by footprint on 2012-05-11
I have recently changed to ubuntu 12.04 . If I open a terminal and type the w or who commands the desktop session on tty7 does not show up! Is this a bug or an intentional change? I've just tried on 10.04 in a VM and tty7 does show...

12.04 version:
xxxxxx@xxxxxx-laptop:~$ w
 16:04:27 up  1:42,  2 users,  load average: 2.75, 2.36, 1.62
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
xxxxxx   pts/1    :0.0             16:04    0.00s  1.16s  0.01s w
xxxxxx@xxxxxx-laptop:~$ who
xxxxxx   pts/1        2012-05-11 16:04 (:0.0)
xxxxxx@xxxxxx-laptop:~$ 

10.04 version:
xxxxxx@xxxxxx-laptop:~$ w
 16:01:32 up 15 min,  2 users,  load average: 3.57, 2.90, 1.65
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
xxxxxx   tty7     :0               12:45    3:17m  1:44   1.83s gnome-session
xxxxxx   pts/0    :0.0             16:01    2.00s 11.02s  0.79s w
xxxxxx@xxxxxx-laptop:~$ who
xxxxxx   tty7         2012-05-11 12:45 (:0)
xxxxxx   pts/0        2012-05-11 16:01 (:0.0)
xxxxxx@xxxxxx-laptop:~$

---

### Post by fdelin on 2012-07-20
Anyone have an answer?  shutdown-at-night now shuts down machines that only have someone in an X session, an unacceptable outcome.

---

### Post by Cheesehead on 2012-07-20
I don't see how it's a bug...tty7 is not a user.

---

### Post by sudodus on 2012-07-20
I think who is not working correctly and filed this bug report.

[[COLOR="Red"]_https://bugs.launchpad.net/ubuntu/+source/coreutils/+bug/1027101_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/coreutils/+bug/1027101")

Add that you are ***also affected by this bug*** and or add information about your problem!

---

### Post by fdelin on 2012-07-20
Agreed, 

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297) is the same issue, lightdm isn't updating utmp but there is a patch already in the verification-needed stage so I think a fix is right around the corner.  I am making my end users aware and backing shutdown-at-night off to 6PM, if they need it open longer they just need to keep a gnome-terminal open.

---

### Post by matt_symes on 2012-07-20
Hi

Seems to be fixed in 12.10. Bare metal install.

```
matthew@matthew-Aspire-7540 ~ % w  
 15:57:17 up  2:54,  9 users,  load average: 0.17, 0.28, 0.37
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
matthew  tty2                      15:54    2:16   0.13s  0.11s -zsh
**matthew  tty7                      13:04    2:54m 11:58   0.41s gnome-session --session=ubuntu**
matthew  pts/1    :0:S.0           13:05    2:52m  3:57   3:57  htop
matthew  pts/5    :0:S.1           13:05    4:28  27.83s 27.83s weechat-curses
matthew  pts/6    :0:S.2           15:57   10.00s  0.16s  0.02s mocp
matthew  pts/7    :0:S.3           13:05    2:52m  0.04s  0.04s vim
matthew  pts/8    :0:S.4           13:05    2:52m  0.00s  0.00s slrn
matthew  pts/9    :0:S.5           13:05    2:52m  0.54s  0.54s newsbeuter
matthew  pts/11   :0:S.7           13:05    0.00s  0.36s  0.01s w
matthew@matthew-Aspire-7540 ~ % 
``````

matthew@matthew-Aspire-7540 ~ % cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu quantal (development branch)"
matthew@matthew-Aspire-7540 ~ %
``````
matthew@matthew-Aspire-7540 ~ % w --version
w from procps-ng 3.3.3
matthew@matthew-Aspire-7540 ~ % 
```Kind regards

---

