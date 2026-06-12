---
title: "Firefox Crash on Update"
date: 2012-06-15
forum: General Help
---

### Post by RieuxTarrou on 2012-06-15
I use Xubuntu 11.10, and after the most recent update, Firefox crashes immediately after initializing the program. A brief report indicates that my /usr/bin/firefox shell script is not executable, but after reviewing the file properties, this doesn't look like the case. 

I sent a bug report to Mozilla, but is there a way to get a more comprehensive read-out of what the issue might be? A command line function, maybe.

Thanks for the help!

---

### Post by lrcaballero on 2012-06-15
> **RieuxTarrou said:**
> I use Xubuntu 11.10, and after the most recent update, Firefox crashes immediately after initializing the program. A brief report indicates that my /usr/bin/firefox shell script is not executable, but after reviewing the file properties, this doesn't look like the case. 

I sent a bug report to Mozilla, but is there a way to get a more comprehensive read-out of what the issue might be? A command line function, maybe.

Thanks for the help!

Did you tried uninstalling firefox via terminal and then re-installing again via terminal? This happened to me with Midori and doing this solved my issue.

Cheers,

lrcaballero

---

### Post by kanikilu on 2012-06-15
Run firefox from the terminal and observe any errors or output there.

With firefox issues, the first thing I'd suggest is trying to run it in safe-mode and if that doesn't work try creating a new profile:

```
firefox --safe-mode
firefox -P
```

---

### Post by RieuxTarrou on 2012-06-16
> **lrcaballero said:**
> Did you tried uninstalling firefox via terminal and then re-installing again via terminal? This happened to me with Midori and doing this solved my issue.

Cheers,

lrcaballero
It looks like the re-installation worked. Thanks! Do you know what the bug may have been?

---

