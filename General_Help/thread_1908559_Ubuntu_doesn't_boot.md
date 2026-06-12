---
title: "Ubuntu doesn't boot"
date: 2012-01-13
forum: General Help
---

### Post by akaicewolf on 2012-01-13
So I was running Ubuntu 11.10 version and I got a new dock and I uninstalled unity then I was unsatisfied to I reinstalled unity then I rebooted my computer now I get the Ubuntu Logo screen and then it goes to this and doesnt go further.

[http://i.imgur.com/4Mmde.jpg](http://i.imgur.com/4Mmde.jpg)

---

### Post by liquidmonkey on 2012-01-13
your issue looks very similar to my problem in an earlier thread.
although its a bit out of focus so hard to read but the layout looks about right.

here is the thread if it helps you.
[http://ubuntuforums.org/showthread.php?t=1908524](http://ubuntuforums.org/showthread.php?t=1908524)

---

### Post by akaicewolf on 2012-01-13
So I tried running the Boot-Repair and it didn't help but it did change the black screen messages

Here is the log from the boot repair: [http://paste.ubuntu.com/803569/](http://paste.ubuntu.com/803569/)
Here is the picture of the black screen: [http://i.imgur.com/HxFnp.jpg](http://i.imgur.com/HxFnp.jpg)

---

### Post by liquidmonkey on 2012-01-13
i just figured out my problem, after literally 6 hours!!
my HDD was totally full from an earlier image so ubuntu could not boot properly.
so dumb yet so simple.
i delete the directory and all is well again!

so my advice is to check if your HDD is full :)

good luck!!

---

### Post by akaicewolf on 2012-01-13
So what exactly did you delete/how?

Oh and now its showing this
[http://i.imgur.com/yy6aM.jpg](http://i.imgur.com/yy6aM.jpg)

---

### Post by liquidmonkey on 2012-01-13
earlier in the day i had been using clonezilla and accidently placed a rather large image onto the laptop HDD instead of putting it onto my external HDD. this filled up the laptops HDD.

i was able to get into terminal by hitting ctrl alt f1 (at the screen where your at now). once in terminal i deleted the directory with the image and BANG! it all works!

if that is not your problem try the link to the thread i included earlier.
it might help.
good luck!

---

