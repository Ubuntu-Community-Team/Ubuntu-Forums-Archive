---
title: "Help with .jnlp - Natty Narwahl"
date: 2012-09-11
forum: General Help
---

### Post by aga021 on 2012-09-11
Hi, complete novice here...pardon my stupidity!
 
I have Ubuntu Linux 11.04, Natty Narwahl, and am trying to use a Website that runs a .jnlp file.  A few weeks ago, it worked fine, but for the last couple weeks I've had this happen:
 
In Firefox: dialogue box - unknown error, try saving the file to disk.  If I download the file and try to open with Iced Tea Java 6, nothing happens.
In Chromium: the file downloads but again will not open (it used to run automatically)
 
I've not tried running it in Terminal because I don't know the appropriate commands.
 
I have openjdk6 installed and I've not added/removed any Java plug-ins since the problem started.  I did update Firefox recently, but I'm assuming that's irrelevant as the problem is also happening in Chromium.
 
Can anybody offer any advice?  Thanks!

---

### Post by dozdozez on 2012-09-11
right click on the internet ink and "copy link location"

then in a terminal:

```

javaws  (paste link address here)

```

it should give some error message so we can know what is happening.

---

### Post by aga021 on 2012-09-11
Thanks for your reply.  Terminal showed java as not installed, but the software centre showed the opposite.  I tried installing Oracle7 and everything is now working fine, so I guess there is a problem with openjdk.

---

