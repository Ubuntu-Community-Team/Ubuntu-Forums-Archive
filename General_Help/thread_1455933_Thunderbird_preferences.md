---
title: "Thunderbird preferences"
date: 2010-04-16
forum: General Help
---

### Post by borepstein on 2010-04-16
Hello all,

We have server-mounted directories and a mix of various Linux platforms. So, on OpenSuSE (versions 11.1 - 11.2) the Thunderbird settings are in $HOME/.thunderbird. They are read fine. However, once you log into an Ubuntu 9.10 machine the Thunderbird there failes to detect them. Any idea why and how to remedy this?

Thanks in advance.

Boris.

---

### Post by bobcollard on 2010-04-16
> **borepstein said:**
> Hello all,

We have server-mounted directories and a mix of various Linux platforms. So, on OpenSuSE (versions 11.1 - 11.2) the Thunderbird settings are in $HOME/.thunderbird. They are read fine. However, once you log into an Ubuntu 9.10 machine the Thunderbird there failes to detect them. Any idea why and how to remedy this?

Thanks in advance.

Boris.
In Ubuntu it is looking for $HOME/.mozilla-thunderbird 
A different file name.

---

### Post by borepstein on 2010-05-06
> **bobcollard said:**
> In Ubuntu it is looking for $HOME/.mozilla-thunderbird 
A different file name.

Yes, this seems to have worked, thanks. I just linked thins as follows:

[adelaide@bepstein][~] ls -ld .*thund*
lrwxrwxrwx 1 bepstein bepstein   12 2010-05-04 13:22 .mozilla-thunderbird -> .thunderbird
drwx------ 3 bepstein bepstein 4096 2010-04-19 13:37 .thunderbird
[adelaide@bepstein][~] 

and it is working fine.

Boris.

---

### Post by bobcollard on 2010-05-06
Glad to help.  Please Edit your first post and add [Solved] to the Title.  Other people may benefit from your experience.

---

