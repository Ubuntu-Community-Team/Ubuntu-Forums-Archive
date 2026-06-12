---
title: "gnome-terminal, Lucid and utf8"
date: 2010-05-08
forum: General Help
---

### Post by Svip on 2010-05-08
So I upgraded to Lucid via the update-manager.  In retrospect, perhaps an ill conceived decision, I know how this system upgrades can go horrible amiss.  But everything seemed to be working just nicely.

Well, except for one glaring thing.  Non-ASCII characters does *not* work in the gnome-terminal.

And since I have quite familiar with locales problems (I assume the developers introduce these problems now and then to entertain people like me), so I tried to pull off all the tricks I know in the book:

```
$ sudo locales-gen
$ sudo locales-gen en_GB.UTF-8
$ sudo dpkg-reconfigure locales
$ sudo ln -s /usr/lib/locale/en_GB.utf8  /usr/lib/locale/en_GB
```

Yes, I have also tried to set LC_ALL in several bash start init scripts.  But to no avail either.

```
$ locale
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=en_GB.UTF-8
```

And I know it is a Unicode issue.  Whenever a special character appears from some else on irssi, it appears like two question mark boxes, indicating the double byte nature of Unicode.  In addition, when I type æ, ø and å into a terminal, the result is 'ae', '?' and '?'.

And I also run Lucid on my laptop, where there is no such issue.

Also, why did they change how dpkg-reconfigure locales work?  Now it just seems to run locales-gen. o_O

---

### Post by gmargo on 2010-05-08
Try tossing an update-locale into the works:
```

$ sudo update-locale LANG=en_GB.UTF-8

```

---

### Post by Svip on 2010-05-08
That unfortunately did not work, but I have located the problem to be software-wise.  It is gnome-terminal that is the problem.

I tried it in xterm, where it worked flawlessly.  A reinstall, perhaps?

Nope; did not work.

---

### Post by UnSandpiper on 2010-05-26
Hi,

updgraded from Karmic to Lucid as well and also just come across this issue.

In Terminal the default character encoding is "Current Locale(ANSIX3.4-1968)".
If I type € the output is EUR. 
If I type £ the output is ?.

Then I change to UTF-8 and when I type € or £ nothing happens.

I tried the commands that were suggested in this thread, with no avail.

Any more ideas anyone?

---

### Post by Svip on 2010-05-26
Well, my issue subsided, when I restarted X.  Apparently, my obsession with uptime was keeping the gnome-terminal from restarting properly.

---

### Post by dino99 on 2010-05-26
try to remove/purge then reinstall your language(s) packages with synaptic

be sure you only use lucid repo, maybe localepurge can help by removing unneeded packages, and gconf-cleaner wipe out old settings

---

