---
title: "readlink command problem"
date: 2012-05-11
forum: General Help
---

### Post by jpvrla on 2012-05-11
Ubuntu 12.04 LTS, 2.6.38-8-generic,Intel(R) Core(TM) i5 CPU  650  @ 3.20GHz

Recently I added a monitoring tool (3rd party) which which included the use of the readlink command.  The install script would fail not recognizing the "-f" parameter of readlink even though the man and help pages for readlink listed it.   This would not work outside the script as well.

I discovered the /usr/lib/klibc/bin/readlink command and it appeared to work and allowed the install script to complete.

There appears to be some kind of disconnect with the readlink command.  

Problem Illustrated:
# find / -name readlink
/usr/lib/klibc/bin/readlink
/bin/readlink

# /bin/readlink -f "$0"
/bin/readlink: invalid option -- 'u'
Try `/bin/readlink --help' for more information.

# /usr/lib/klibc/bin/readlink -f "$0"
#

---

### Post by hwttdz on 2012-05-11
It's complaining about the '-u' which must be in the $O variable, not about the -f you're feeding it.  And -u is not a valid flag for /bin/readlink but is for /usr/lib/klibc/bin/readlink (?, actually that other one confuses me greatly).

---

### Post by jpvrla on 2012-05-12
I understand the passing of incorrect flags but  ubuntu support needs to address the issue.   The current man pages for readlink are not in sync with the default /bin/readlink command.   I share your confusion.   I suspect /usr/lib/klibc/bin/readlink may be one offered by kubuntu.

---

