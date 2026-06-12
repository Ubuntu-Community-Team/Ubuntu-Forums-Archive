---
title: "trying to install, libnotify error"
date: 2011-02-28
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-02-28
i am trying to install bmpx. i have finally googled my way to getting it to the ./configure step. it had some dependencies that i took care of, and now i get the error
 "configure: error: conditional "HAVE_LIBNOTIFY" was never defined.
Usually this means the macro was only invoked conditionally."

i have googled, and forum searched for about an hour now, and there were a couple of people who had the same issue, but never got resolved. i grabbed up all the .dev files from synaptic, and still same error. there are several more files that are .dbg or are plugins for different programs (like vlc) and i dont believe that the issue is NOT having a file. 

i just dont know what to do. i know there are OTHER media players, and i have a small collection of them, but i would really like to get this one, and it will then be my first time installing from a tarball and not just using synaptic/software center. 

i give many thanks to anyone who can help me take the next step in my linux experience.
i am on ubuntu 10.10 x64 if it makes any difference.

---

### Post by zenwalker on 2011-02-28
Is there no BMPX package supported in official repos? Did you search?

Might this help? [http://ubuntuforums.org/showthread.php?t=154305](http://ubuntuforums.org/showthread.php?t=154305)

---

### Post by SE7EN-LOCSTA on 2011-02-28
i have not seen bmpx in either synaptic or software center.. i tried beep media player, bmp, bmpx etc. all the websites for it are dead, and the people ive seen to have my problem did not get a solution. that link was good, but they were having the issues that i have already resolved. just stuck on (hopefully) this last part :(

---

### Post by Krytarik on 2011-02-28
I know, you said you have all packages you need, but do you surely have those (with respective dependencies)?:
[http://packages.ubuntu.com/maverick/libnotify-bin](http://packages.ubuntu.com/maverick/libnotify-bin)
[http://packages.ubuntu.com/maverick/libnotify-dev](http://packages.ubuntu.com/maverick/libnotify-dev)

---

### Post by SE7EN-LOCSTA on 2011-02-28
i went thru and checked on those links, and just grabbed everything that even looked similar to them. thanks. never knew about these 'extra' files i needed.

---

