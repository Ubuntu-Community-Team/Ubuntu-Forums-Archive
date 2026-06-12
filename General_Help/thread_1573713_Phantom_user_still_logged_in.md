---
title: "Phantom user still logged in"
date: 2010-09-13
forum: General Help
---

### Post by chris_uk on 2010-09-13
Hi all,

I'm wondering if anyone has ever encountered this problem before:
[FONT=Courier New]
$ uptime
 09:55:00 up 7 days, 6 min,  2 users,  load average: 0.00, 0.00, 0.00[/FONT]

..but I'm the only user logged in!

[FONT=Courier New]$ who -a
           system boot  2010-09-06 09:48
           run-level 2  2010-09-06 09:48                   last=
LOGIN      tty4         2010-09-06 09:48              4293 id=4
LOGIN      tty2         2010-09-06 09:48              4296 id=2
LOGIN      tty5         2010-09-06 09:48              4294 id=5
LOGIN      tty6         2010-09-06 09:48              4300 id=6
LOGIN      tty3         2010-09-06 09:48              4299 id=3
chrisu   + pts/0        2010-09-13 09:25   .         10388 (10.16.98.69)
LOGIN      tty1         2010-09-06 09:54              4651 id=1
[COLOR=Red]           pts/1        2010-09-07 10:43              5485 id=ts/1  term=0 exit=0[/COLOR]
LOGIN      tty1         2010-09-07 16:52              6126 id=1[/FONT]

looks as though this is the culprit, but...

[FONT=Courier New]$ kill 5485
-bash: kill: (5485) - No such process[/FONT]

This process doesn't exist in the /proc folder or the output of ps. Does anyone know how this happened, and how to remove this ghost user from my system without a complete reboot? I think I have seen a similar thing on a RedHat machine ages ago but I have never figured out how to log out these ghost users.

[FONT=Courier New]$ uname -a
Linux ubuntu 2.6.24-28-server #1 SMP Wed Aug 25 16:07:16 UTC 2010 i686 GNU/Linux[/FONT]


Any help would be much appreciated!

Chris.

---

### Post by Elfy on 2010-09-13
It's you - you in your desktop and you in the terminal, open another terminal and run top - there will be 3 users.

---

### Post by nothingspecial on 2010-09-13
There are many users.

There`s root who is running processes aswell as your self

There`s even a user called nobody

type ```
cat /etc/passwd
``` to see

---

### Post by chris_uk on 2010-09-13
> **forestpiskie said:**
> It's you - you in your desktop and you in the terminal, open another terminal and run top - there will be 3 users.

Hi forest,

This is ubuntu server and X11 isn't installed. I am the only user connected to this machine via ssh and I am using the login shell.

Many Thanks,

Chris.

---

### Post by Elfy on 2010-09-13
```
who
```

will show you active users and where they are - I have 2 terminals open and tty7 for gnome 
> 
kevin    tty7         2010-09-13 06:35 (:0)
kevin    pts/0        2010-09-13 09:08 (:0.0)
kevin    pts/1        2010-09-13 10:14 (:0.0)

---

### Post by nothingspecial on 2010-09-13
Me too

```
~:$ w
 10:29:04 up 1 day, 19:29,  3 users,  load average: 0.58, 0.43, 0.44
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
rob      pts/1    :0:S.0           Sat22    0.00s  0.51s  0.02s w
rob      tty7     :0               Sun08   43:29m  6:22   0.21s gnome-session
rob      pts/2    :0:S.1           Sun08   25:47m  0.18s  0.18s /bin/bash
```

3 users, but they are all me

---

### Post by Elfy on 2010-09-13
@nothing special - we ought to merge bit's of our sigs

> By the time people ask you for help, they've probably tried several things. As a result, their computer might be in a strange state. This is natural. Linux assumes you know exactly what you`re doing :lol:

---

### Post by chris_uk on 2010-09-13
Hi Both,

I appreciate your help, but a couple of key facts:

1) I don't have gnome installed, I don't even have a GUI installed. This is ubuntu server *not* desktop
2) I have already used 'who' as per my original post and the phantom user in question is not part of my session, and the PID listed is invalid.

Its as though wtmp has not been correctly cleaned up by the operating system after an earlier session ended.

Many Thanks,

Chris.

---

### Post by nothingspecial on 2010-09-13
Yeah, that`s nice. :D

Sorry Chris, totally off topic


I sometimes think mine's a little bit stern, but it`s just something I read once that clicked with me.

If you sudo rm something it will darn well rm it because you told it to. It won`t ask you if your sure.

A little like another one that someone`s got about linux not stopping people doing stupid things because that would stop them doing clever things......... something like that.

I`ve even had a couple of first time users that I have responded first to, who don`t understand that sigs appear at the bottom of every post, thinking that I directed it at them.

But, it`s my sig and I`m sticking with it.

Gong and the Ozrics are touring btw

---

### Post by Elfy on 2010-09-13
Ok- so back on topic then - what does ```
w
``` give

---

### Post by chris_uk on 2010-09-13
OK no worries I'll just reboot the machine.

I just thought it may have been a bug in OpenSSH or something rather than me doing something 'stupid', although I can't rule that out as I'm only human :)

Chris.

---

### Post by nothingspecial on 2010-09-13
Hi Chris

The server is running, that`s one user

You are logged in remotely, that`s another one

When I posted my last response, I just logged in to my desktop from my netbook and it showed 3 users, the console, gnome and my remote log in

If I open another terminal on my net book and login again I have 4 users
```

~:$ w
 10:54:07 up 1 day, 19:54,  4 users,  load average: 0.15, 0.26, 0.31
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
rob      tty7     :0               Sun08   43:54m  6:26   0.21s gnome-session
rob      pts/0    :0.0             Sun08   26:08m  0.19s  0.19s bash
rob      pts/3    rob-laptop.local 10:16   25:03   0.24s  0.24s -bash
rob      pts/4    rob-laptop.local 10:52    0.00s  0.24s  0.02s w
```

If I open yet another terminal on my netbook and login again I have 5 users
```

~:$ w
 10:54:53 up 1 day, 19:55,  5 users,  load average: 1.71, 0.67, 0.45
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
rob      tty7     :0               Sun08   43:55m  6:27   0.21s gnome-session
rob      pts/0    :0.0             Sun08   26:09m  0.19s  0.19s bash
rob      pts/2    rob-laptop:S.0   10:54    0.00s  0.21s  0.02s w
rob      pts/3    rob-laptop.local 10:16   25:49   0.24s  0.24s -bash
rob      pts/4    rob-laptop.local 10:52   46.00s  0.22s  0.22s -bash
```

---

### Post by chris_uk on 2010-09-13
> **forestpiskie said:**
> Ok- so back on topic then - what does ```
w
``` give

[FONT=Courier New] 10:58:43 up 7 days,  1:10,  [COLOR=Red]2 users[/COLOR],  load average: 0.00, 0.00, 0.00
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
chrisu   pts/0    10.16.98.69      10:58    0.00s  0.11s  0.00s w
[/FONT]
Many Thanks,

Chris.

---

