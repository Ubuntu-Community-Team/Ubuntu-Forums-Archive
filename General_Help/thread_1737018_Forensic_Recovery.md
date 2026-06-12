---
title: "Forensic Recovery"
date: 2011-04-22
forum: General Help
---

### Post by inoh on 2011-04-22
Is there a program available to Ubuntu which can recover data from a dead hard drive?

The hard drive in question is running Windows Vista but cannot boot.  Used Ubuntu live CD to try and mount it, did not work.  However Ubuntu told me it was bad, found 12,500 bad sectors.  It will let me erase the hard drive and start new, but I need lots of photos that are on there recovered first.

Any suggestions?

---

### Post by jcolyn on 2011-04-22
Try entering ```
sudo photorec
``` in the terminal with this drive connected as a slave.

I don't know if it can be done from a live CD but you might give it a try. However you'll need an external drive connected in order to copy the files to.

---

### Post by flipper T on 2011-04-22
this may be relevant

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by coldraven on 2011-04-23
There is some good stuff here, examples of data recovery:
 [http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")

and look at Foremost as well.

[http://linux.die.net/man/1/foremost](http://linux.die.net/man/1/foremost)
[ ]("http://members.iinet.net.au/%7Eherman546/p21.html")

---

### Post by Rasa1111 on 2011-04-23
inoh~
If you want to shoot me a private message with your email,
I can provide something that may be of use to you. 

Good luck. <3

---

### Post by DeMus on 2011-04-23
sudo photorec +1
I have used it several times and it works great. Many options to choose from, just the way you like it.

---

### Post by aysiu on 2011-04-23
> **jcolyn said:**
> Try entering ```
sudo photorec
``` in the terminal with this drive connected as a slave.

I don't know if it can be done from a live CD but you might give it a try. However you'll need an external drive connected in order to copy the files to.
You can't run *sudo photorec* until you install *testdisk*: ```
sudo apt-get update
sudo apt-get install testdisk
```

---

### Post by inoh on 2011-04-23
Thanks for all the suggestions.  I will get to these as soon as I can.  Gave it to someone that can take them apart, but was only told what I already knew.  I have Ubuntu on an external USB HDD; may try that route so I don't have to use the live cd.

Thanks again everyone.  Will post an update when I can.

---

### Post by inoh on 2011-05-01
Just an update.  The following worked

sudo apt-get update
sudo apt-get install testdisk
sudo photorec

Used my Ubuntu External USB HDD to perform the operation.

Ran until until it stopped upon a segmentation failure, but recovered everything that I needed.  Thanks to all who helped.

---

