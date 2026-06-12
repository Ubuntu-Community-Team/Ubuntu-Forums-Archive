---
title: "Firefox updates_ firefox 10 Maverick Meerkat"
date: 2012-02-04
forum: General Help
---

### Post by christon74 on 2012-02-04
Hello everybody :)
Until very recently, it has been relatively easy to update Firefox. I agree with many people who are fed up with Firefox too frequent updates. 
I am no developer and I really cannot make heads or tails of this:

W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/f/firefox-mozilla-build/firefox-mozilla-build_10.0-0ubuntu1_i386.deb](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/f/firefox-mozilla-build/firefox-mozilla-build_10.0-0ubuntu1_i386.deb)
  Got a single header line over 360 chars

Many thanks in advance to anybody who can help me fix this.

Christophe.

---

### Post by lisati on 2012-02-04
*Thread moved to **General Help**.*

---

### Post by drpjkurian on 2012-02-04
This is due to server problem of sourceforge. Use the mirror instead
Try this instead ```
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

---

### Post by christon74 on 2012-02-05
I have tried this up to seven times ... not to much avail. It does not work. Still impossible to update Ubuntu.

---

### Post by christon74 on 2012-02-05
command deb not found

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found

---

### Post by roscius on 2012-02-06
The problem is on the repository end, it's sending out headers which apt doesn't like, the repository is working on fixing the issue: [http://sourceforge.net/p/allura/tickets/3683/?page=1](http://sourceforge.net/p/allura/tickets/3683/?page=1)

In order to fix the issue manually, you can try a mirror of the the repository.  Edit your /etc/apt/sources.list file and change the line:

```

deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main

```To

```
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

---

### Post by Rebelli0us on 2012-02-06
Best guide for updating Firefox is here:

[http://ubuntuforums.org/showthread.php?t=1712247&highlight=firefox+mega+thread](http://ubuntuforums.org/showthread.php?t=1712247&highlight=firefox+mega+thread)

... especially if you're sticking with Ubu 10.10 and want the latest FF

---

### Post by lovinglinux on 2012-02-07
> **Rebelli0us said:**
> Best guide for updating Firefox is here:

[http://ubuntuforums.org/showthread.php?t=1712247&highlight=firefox+mega+thread](http://ubuntuforums.org/showthread.php?t=1712247&highlight=firefox+mega+thread)

... especially if you're sticking with Ubu 10.10 and want the latest FF

I have recently changed some info in that thread, because there is no need to get a ppa anymore. The latest Firefox is now available in the official repos. Uninstall the Ubuntuzilla, update and upgrade to get the latest version.

---

### Post by Rebelli0us on 2012-02-07
> **lovinglinux said:**
> **I have recently changed some info in that thread**, because there is no need to get a ppa anymore. The latest Firefox is now available in the official repos. Uninstall the Ubuntuzilla, update and upgrade to get the latest version.

You sure did change stuff. I'd followed your instructions and added:

[HTML]http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu[/HTML]

so now I have Firefox 10.0 and I'm pleased because 3.xxx was crashing. Do I need to go into update manager and delete the ppa?

---

### Post by lovinglinux on 2012-02-08
> **Rebelli0us said:**
> You sure did change stuff. I'd followed your instructions and added:

[HTML]http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu[/HTML]

so now I have Firefox 10.0 and I'm pleased because 3.xxx was crashing. Do I need to go into update manager and delete the ppa?

Yes, I am sure. The *firefox-next* ppa is not needed anymore. It won't hurt if you leave it there, but you can safely remove it, update and upgrade to get the latest package from the official repos.

---

