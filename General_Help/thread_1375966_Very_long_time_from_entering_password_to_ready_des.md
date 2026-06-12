---
title: "Very long time from entering password to ready desktop"
date: 2010-01-08
forum: General Help
---

### Post by Falc7 on 2010-01-08
Hi
I have an unreasonably long time to wait from log in, to when my desktop is ready, it takes 40 seconds from hitting enter to seeing my files on the desktop, and about another 15 seconds from then to hearing the opening jingle. It used not to be this way, before it took less than 10 seconds, but about 4 days ago this time shot up suddenly, is there some way to diagnose whats causing this delay?

---

### Post by hwttdz on 2010-01-08
You can try looking at bootchart, make sure it continues to record after logging in (default behavior).  Later on if you're interested in bootup itself you can change this behavior.

---

### Post by Falc7 on 2010-01-08
Could you help me analyse it?

[http://img691.imageshack.us/i/jamiekubuntukarmic20100.png/](http://img691.imageshack.us/i/jamiekubuntukarmic20100.png/)

I've notificed that if i log in, then log out, then log in again, it is far far faster, taking about 10 seconds from password to a ready desktop

---

### Post by hwttdz on 2010-01-08
Well it looks like kded4 is using a lot of cpu and kmix is possibly dying for some reason upon starting up.  You can investigate what both of these do and if there are any problems with either.  Another possibility is to make a script along the lines of 

#!/bin/bash
top -b -n 100 > ~/my_startup_procs.txt

though of course this might not be terribly enlightening as if it starts after the program causing the trouble starts you won't get any info about it.  Another possibility would be extending the bootcharting 
edit /etc/init/bootchart.conf
and in the pre stop section there's a sleep command, extend it such that it reports longer, and you can see if you're getting a desktop when kmix finally unfreezes (or gets killed off).

---

### Post by hwttdz on 2010-01-08
Also I don't know the overlap between the suse repos and the kubuntu repos but you can take a look at this thread:
[http://forums.opensuse.org/pre-release-beta/408243-why-does-kded4-hog-one-my-processors.html](http://forums.opensuse.org/pre-release-beta/408243-why-does-kded4-hog-one-my-processors.html) though it looks a bit out of date to be experiencing the problem now.

And are you all updated?

---

### Post by Falc7 on 2010-01-08
Hi yep i'm using the latest everything, kernal  -17, and kde 4.3.4.

So i would change this:
pre-stop script
   ```
 # Sleep for an extra 45s to allow enough time to chart the desktop
    # login
    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 45
end script
```

To this:

```
pre-stop script
    # Sleep for an extra 90s to allow enough time to chart the desktop
    # login
    [ "$UPSTART_STOP_EVENTS" = "stopped" ] && sleep 90
end script
```

Is that it?

---

### Post by hwttdz on 2010-01-08
Yup, that will increase logging time.  Did you investigate kmix and kded4 any? are those processes running when you're logged in?  Are they using a lot of cpu?  Do you get any error messages if you try to instantiate them yourself?

---

### Post by Falc7 on 2010-01-08
> **hwttdz said:**
> Yup, that will increase logging time.  Did you investigate kmix and kded4 any? are those processes running when you're logged in?  Are they using a lot of cpu?  Do you get any error messages if you try to instantiate them yourself?

I'm having some problems with kmix as stated here:
[http://ubuntuforums.org/showthread.php?p=8621420#post8621420](http://ubuntuforums.org/showthread.php?p=8621420#post8621420)

Sorry i don't know how do investiage kmix and kde4 much further.
I know kmix dosen't start when i boot up though. I  believe kded4 does however. Kmix starts fine if i manually enter the command in terminal.
Regarding system usage, checking now and kded4 is shown as a sleeping process using 10mb of memory, and no CPU at all.
Now ive started kmix, it also shows 10mb of memory and no cpu usage. No error messages when running them myself though terminal
jamie@jamie-kubuntu:~$ kded4
KDE Daemon (kded) already running.

Edit:
The Kmix issue seems to have fixed itself, here is the new bootchart:
[http://img7.imageshack.us/img7/475/jamiekubuntukarmic20100.png](http://img7.imageshack.us/img7/475/jamiekubuntukarmic20100.png)

Kded4 still seems to be taking a lot of resources.

---

