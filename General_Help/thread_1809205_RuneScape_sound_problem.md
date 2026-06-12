---
title: "RuneScape sound problem"
date: 2011-07-21
forum: General Help
---

### Post by mitk0o0o0 on 2011-07-21
Hello, i had this problem a while ago and i fixed it by following this post: [http://ubuntuforums.org/showpost.php?p=9493360&postcount=6](http://ubuntuforums.org/showpost.php?p=9493360&postcount=6)

A few days ago i got a notification about update for Java and JDK. I updated it and after the update the sounds have gone away again.

I tried following this again: [http://ubuntuforums.org/showpost.php?p=9493360&postcount=6](http://ubuntuforums.org/showpost.php?p=9493360&postcount=6)
But whenever i do, no java apps ever start and i have to re-install sun-java6 again to get it to work.

Please help, anyone found a solution? It's really bad with no sounds, i almost died 3 times.

---

### Post by mitk0o0o0 on 2011-07-21
Bump

---

### Post by mitk0o0o0 on 2011-07-22
Bump

---

### Post by mitk0o0o0 on 2011-07-23
Anyone?

---

### Post by markjensen on 2011-07-23
Do you use Firefox for playing? Does your sound work if you boot and just try to play music or a sound outside of a browser (such as using mplayer)?

If so, try opening a terminal and starting firefox this way:```
aoss firefox
```and see if you get your sound that way.

It may be a problem with alsa/pulseaudio incompatibilities, and if so, the "aoss" may take care of it.

I use Chrome for RS, and i have the starting icon for it prefaced with the "aoss" command, so it forces it to that mode.

Hope that helps!

---

### Post by mitk0o0o0 on 2011-07-23
> **markjensen said:**
> Do you use Firefox for playing? Does your sound work if you boot and just try to play music or a sound outside of a browser (such as using mplayer)?

If so, try opening a terminal and starting firefox this way:```
aoss firefox
```and see if you get your sound that way.

It may be a problem with alsa/pulseaudio incompatibilities, and if so, the "aoss" may take care of it.

I use Chrome for RS, and i have the starting icon for it prefaced with the "aoss" command, so it forces it to that mode.

Hope that helps!I'm using the RuneScape client, i followed a tutorial somewhere to install it. But i'll try what you gave me, hope it still does the job. Thanks.

---

### Post by mitk0o0o0 on 2011-07-23
Thank you so much, you explained me everything on RS. :)

The solution for me was this:
Uninstalled all sun-java stuff from synaptic package manager.
Installed them again except the jdk one and it all works now. :D

---

