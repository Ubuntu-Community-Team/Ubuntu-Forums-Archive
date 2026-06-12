---
title: "apt-get clean vs apt-get autoclean"
date: 2011-01-19
forum: General Help
---

### Post by Alcardil on 2011-01-19
I'm trying to learn more about managing my ubuntu system and I was wondering what the difference is between apt-get clean and apt-get autoclean; and if there is a general rule of thumb on when to use them.

---

### Post by veggen on 2011-01-19
Please search before you post.
[http://ubuntuforums.org/showthread.php?t=592141](http://ubuntuforums.org/showthread.php?t=592141)

You'll probably want to execute apt-get clean/autoclean/autoremove all together when ever you want to do general maintenance.

---

### Post by lithopsian on 2011-01-19
If you work on the command line, you can use the autoremove option every time you uninstall software.  You could even alias it.

Autoclean cleans stuff you don't need any more.  Clean cleans (nearly) everything.

---

### Post by lithopsian on 2011-01-19
If you work on the command line, you can use the autoremove option every time you uninstall software.  You could even alias it.

Autoclean cleans stuff you don't need any more.  Clean cleans (nearly) everything.

---

### Post by oldos2er on 2011-01-19
```
man apt-get
```

---

### Post by matt_symes on 2011-01-19
Hi clean

>            clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(1) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.


The man pages are a great source of information, just as oldos2er suggested. Always my first port of call.

Kind regards

---

### Post by rjdaggett on 2012-04-05
Niether of you explained to him what the difference between them are. I hate when people just quote man. I had the same question come up in passing and have already read the man page.

---

### Post by uRock on 2012-04-05
This thread is more than a year old.

Thread Closed.

---

