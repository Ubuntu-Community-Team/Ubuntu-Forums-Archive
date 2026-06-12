---
title: "What is the &quot;S&quot; column of chkconfig?"
date: 2011-12-31
forum: General Help
---

### Post by apollothethird on 2011-12-31
Can someone tell explain the 9th column of “chkconfig --list”.  It usually shows op as “S:On”.

The other columns are as such: first column the name of the service; the 2nd – 8th (runlevels 0-6) columns are the run levels.  Some of them such as the service, apparmor which have a 9th column (S:On).

Thanks in advance for any information on this.  I did research.  But so far the only information I can find on chkconfig shows how to list, add, delete or set the run levels on or off such as:

```

chkconfig --level [0123456] [service] [off/on]

```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Lars Noodén on 2011-12-31
That would be [Single User Mode](http://manpages.ubuntu.com/manpages/oneiric/en/man8/telinit.8.html), but without stopping any of the existing processes first.  Run level 1 is Single User Mode, but with stopping or starting a lot of processes.

---

### Post by apollothethird on 2011-12-31
> **Lars Noodén said:**
> That would be [Single User Mode]("http://manpages.ubuntu.com/manpages/oneiric/en/man8/telinit.8.html"), but without stopping any of the existing processes first.  Run level 1 is Single User Mode, but with stopping or starting a lot of processes.

Thanks!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

