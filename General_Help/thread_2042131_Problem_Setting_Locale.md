---
title: "Problem Setting Locale"
date: 2012-08-14
forum: General Help
---

### Post by AleatoricConsonance on 2012-08-14
I very recently installed Xubuntu 12.04, and have found it to be a pretty good, pretty simple disto the suits my needs.

However, the locale seems to be set to **en_US** and I'm in Australia so I need it to be **en_AU**. I'm having serious difficulties correcting it.

I have followed a few suggestions from various web pages, and so far I have managed to update some, but not all of the vars that I seem to need to.

This is the output from the **locale** command:

[FONT="Courier New"]LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE="en_AU.UTF-8"
LC_NUMERIC="en_AU.UTF-8"
LC_TIME="en_AU.UTF-8"
LC_COLLATE="en_AU.UTF-8"
LC_MONETARY="en_AU.UTF-8"
LC_MESSAGES="en_AU.UTF-8"
LC_PAPER="en_AU.UTF-8"
LC_NAME="en_AU.UTF-8"
LC_ADDRESS="en_AU.UTF-8"
LC_TELEPHONE="en_AU.UTF-8"
LC_MEASUREMENT="en_AU.UTF-8"
LC_IDENTIFICATION="en_AU.UTF-8"
LC_ALL=en_AU.UTF-8
[/FONT]

**/etc/default/locale**
[FONT="Courier New"]LANG=en_AU.UTF-8
LANGUAGE=en_AU
LC_ALL=en_AU.UTF-8[/FONT]

**/etc/environment**
[FONT="Courier New"]PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_AU.UTF-8"
LANGUAGE="en_AU"[/FONT]

Can anyone offer any guidance as to how to set the LANG and LANGUAGE to their correct settings, and have it persist?

*nb: My summary on left says I have 9.04. Ignore it. Old setting and it won't let me update it until I have 50 posts.*

---

### Post by AleatoricConsonance on 2012-08-15
bump. Anyone able to assist?

---

### Post by Toz on 2012-08-15
Did you make the change to ~/.pam_environment as well?

---

### Post by AleatoricConsonance on 2012-08-16
Thank you very much, that worked. All of the pages I'd been able to find discussing this issue did not mention any changes to .pam_environement.

---

