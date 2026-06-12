---
title: "cannot open firefox with trickle"
date: 2010-04-22
forum: General Help
---

### Post by fermulator on 2010-04-22
Trickle is an application that lets a user limit the bandwidth of a process or processes.  An example, limiting the download rate of wget:
```
trickle -d 600 wget http://mystuff.com/myfile
```

This will download "myfile" from "mystuff.com" at a maximum rate of 600KB/s.

Now, all of a sudden (I'm not sure what caused this), I can no longer use trickle with Firefox.

```
trickle -d 600 firefox
```

> fermulator@fermmy:~$ trickle -d 600 firefox
trickle: Could not reach trickled, working independently: No such file or directory


It just sits there, and never opens.  How can I debug this?  I've tried uninstalling and re-installing trickle, but that didn't help.

Versions:
 * Ubuntu 9.04 Jaunty
 * trickle 1.07-5
 * Firefox 3.6.3

---

### Post by Christor on 2010-05-13
I also have this problem =/

---

### Post by fwpost on 2010-08-22
This exact problem is still there. When using Trickle as follows:

```

fwiep@waanzinspc:~$ trickle -vvvv -d 20 firefox
trickle: Could not reach trickled, working independently: No such file or directory
firefox: [trickle] Initialized
firefox: [trickle] Initialized
firefox: [trickle] Initialized
firefox: [trickle] Initialized
^C
fwiep@waanzinspc:~$
```,

firefox and firefox-bin both show up in the System-Monitor, suggesting they started allright - but without any GUI. There is no way to get to them.

Any help would be appreciated!


FWieP

Versions:
* Ubuntu 10.04 Lucid
* trickle 1.07
* Firefox 3.6.8

---

### Post by pererik87 on 2010-09-03
bump

---

### Post by pererik87 on 2010-09-03
works with opera

---

### Post by fermulator on 2010-09-04
There are similar reports in ubuntu and other distros:
 * [http://forums.fedoraforum.org/showthread.php?p=1329586#post1329586](http://forums.fedoraforum.org/showthread.php?p=1329586#post1329586)
 * [https://answers.launchpad.net/ubuntu/+source/trickle/+question/96940](https://answers.launchpad.net/ubuntu/+source/trickle/+question/96940)

We are not alone it would seem ...

I still have no solution to this problem, but, it would appear that it is firefox related.  So, I submitted this on the mozilla support page: [https://support.mozilla.com/en-US/questions/750813](https://support.mozilla.com/en-US/questions/750813)

---

### Post by mag1 on 2010-11-30
Is there a fix for this now?

---

### Post by mag1 on 2010-12-07
Anyone?

---

### Post by dpiwowarski on 2011-03-08
Try to run trickle in standalone mode.
e.g. ```
trickle -s -d 100 /opt/google/chrome/google-chrome
```

---

### Post by insanity54 on 2011-06-13
> **dpiwowarski said:**
> Try to run trickle in standalone mode.
e.g. ```
trickle -s -d 100 /opt/google/chrome/google-chrome
```

No cigar.

---

### Post by insanity54 on 2011-07-01
Couldn't get it working with FF but I got it working with chrome by doing this:

```
trickle -s -d 30 -u 30 /usr/bin/google-chrome
```

---

### Post by midiqui on 2012-04-26
I have tried trickle with firefox, and it didn't work at first (no speed limit). But inserting the url at the end, it works. For example:

trickle - u 10 firefox "url"

 I don't know why (I am a kind of Ubuntu rookie), but I hope it helps someone

---

