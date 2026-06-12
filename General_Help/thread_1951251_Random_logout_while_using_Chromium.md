---
title: "Random logout while using Chromium"
date: 2012-04-02
forum: General Help
---

### Post by vkrajacic89 on 2012-04-02
Hey, I have a problem with new Ubuntu 11.10. While I'm surfing on the internet system just logout and Ubuntu welcome screen is presented to me. I searched this problem, and found out that many people have this problem as well, but couldn't find any solution.

This bug always occurs while using Chromium. I found this report in syslog:

Apr  2 12:00:52 Vjekoslav-Ubuntu gnome-session[1474]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012

Does anyone else had this problem?

---

### Post by kc1di on 2012-04-02
believe this is a know bug and their working on it. 
There are some problems with chromium in 12.04 also but there was an update on that one this morning so hopefully it's fixed, we will see. 
you can go to this webpage and see if your bug has been reported if not report it [https://bugs.launchpad.net/ubuntu]("https://bugs.launchpad.net/ubuntu")

you may want to update your system if you haven't in a few days just to see if chromium has been updated for 11.10 also.
Cheers !

---

### Post by vkrajacic89 on 2012-04-10
I updated my system from 11.10 to 12.04, and tried to used Firefox instead of Chromium, but the problem still occurs. I've googled it, and it seems there's hasn't been any solution to this problem yet... :(

---

### Post by ehime on 2012-04-23
There's an issue on my 11.10 box producing same symptoms/errors with forced logout as GTK (reboots?) panics from Chrome (not Chromium). 

```

ehime@ehimeprefecture:~$ cat /var/log/syslog | grep "Fatal"
Apr 23 08:47:24 ehimeprefecture gnome-session[3445]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Apr 23 13:15:47 ehimeprefecture gnome-session[1729]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Apr 23 13:48:43 ehimeprefecture gnome-session[11869]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012

```

---

### Post by techsupport on 2012-04-23
> **vkrajacic89 said:**
> Hey, I have a problem with new Ubuntu 11.10. While I'm surfing on the internet system just logout and Ubuntu welcome screen is presented to me. I searched this problem, and found out that many people have this problem as well, but couldn't find any solution.

This bug always occurs while using Chromium. I found this report in syslog:

Apr  2 12:00:52 Vjekoslav-Ubuntu gnome-session[1474]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012

Does anyone else had this problem?

Did you install the Chromium PPA yet to see if they have a upgrade for your browser available?

The Chromium PPA is down the list here:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

