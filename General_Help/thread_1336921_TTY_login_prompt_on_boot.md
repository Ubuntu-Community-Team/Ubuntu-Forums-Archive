---
title: "TTY login prompt on boot"
date: 2009-11-25
forum: General Help
---

### Post by jmsthing678 on 2009-11-25
I recently did a fresh install of Karmic 64bit and it has been running smoothly so far. Today when I rebooted I was presented with the TTY login prompt and so I logged in. I then had to use the startx command to open the gui at which point the normal gui login screen opened and I was able to login normally. I have rebooted several times since and each time I have had the same problem. 

So my question is:
How do I disable this TTY prompt and boot normally without having to manaully login or startx?

I know this is only a minor issue but it is very annoying. I also wonder if this is an indicator of some other underlying issue that could threaten system stability. 

Any help is greatly appreciated. Thanks!:)

---

### Post by jmsthing678 on 2009-11-25
I just ran the "w" command it showed 3 of of the same user (which I have changed to "bob" for privacy). Should there be three of myself logged in? Does this have anything to do with me having to login twice as mentioned above?

```

bob@ub9:~$ w
 01:41:58 up  1:06,  3 users,  load average: 1.02, 1.02, 1.00
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
bob    tty1     -                00:35    1:06m  5.40s  0.01s /bin/bash /usr/
bob    tty9     :1               00:36    6:06m  2:16   0.13s gnome-session
bob    pts/0    :1.0             01:41    0.00s  0.17s  0.01s w
bob@ub9:~$ 

```

---

### Post by jmsthing678 on 2009-11-25
bump

---

### Post by jmsthing678 on 2009-11-25
Well I found a roundabout way of solving this issue. I wasn't able to find out why it was trying to boot into TTY1 but I killed this by completely deleting the tty1 virtual console from /etc/init/. So now I have no tty1 console, however I have a normal boot now. 

I would still like to know what caused this abnormal boot in the first place however. So feel free to share if you have any ideas. 

Thanks.

---

### Post by revelationman on 2010-08-02
I get that also the odd time I ran the following command startx and that loads the gui. 

But it's weird that I am getting at boot, I do run Vista on the other partition and the graphics are on board NVIDA.  

00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)

But could this be a bug I am not sure to be honest I am using the recommended drivers 

But this does not happen all the time but I am feeling that the problem is loading the drivers

---

### Post by revelationman on 2010-08-02
Just speaking with a friend who is a programmer this is what he feels the issue is



 I suspect they have synchronization issues because it is very hard to get right and even harder to test

The GUI requires several subsystems to be working before it will work.
more than that X is a network based graphics system, so networking must be up

Now it seems to me in order to get that fast boot there is still loads of work to do.

---

### Post by ademey on 2010-10-30
I got something very similar. You can read my story in ubuntu bug #498586

However, very little response and nobody marked to have the same issue. Frustrating me for almost a year now!

---

### Post by aaitken1998 on 2011-08-07
Firstly to tell you about the "three times logged in" thing this is because the system has TTY when you are logging in to the text base place that is not your GUI but one of the TTYs, the parts that say "tty7" and "pts/0" are necessary for the GUI. To try and get rid of this try pressing CTRL + ALT + F9 rather than logging in to the text based if not it might be a problem with tty9 in which case I would recommend reinstalling.

PS Your tty1 is the text based one you logged into so it appears that it is the one its designed to automatically go into. Correct me if I'm wrong but you could maybe create a file called .bash_profile in your home directory with gedit then input the following.

```
 startx 
```This should take you straight to the gui after you login to the tty if my past assumption was wrong :)

It's not perfect but at least you won't have to input "startx" everytime you login.

---

