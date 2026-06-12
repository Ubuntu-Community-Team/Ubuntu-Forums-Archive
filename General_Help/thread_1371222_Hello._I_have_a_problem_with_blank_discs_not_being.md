---
title: "Hello. I have a problem with blank discs not being recognized."
date: 2010-01-03
forum: General Help
---

### Post by Confirmed on 2010-01-03
Hello, this is my first post here. I have been using Ubuntu for a long time but never signed up here, so I am looking forward to meeting some new friends. :)

I asked this question on LinuxQuestions.org and didn't get any replies, so I have come here.

**Some prerequisites:**
[LIST]
I am running Ubuntu 9.10 Karmic Koala and am using the Brasero Disc Burner utility with DVD-RW discs.
[*]I have an EZ-DUB Lite-On eZAU422 external DVD/CD Rewritable drive hooked up to my Acer Aspire One D250-1026 netbook via USB cable.
[/LIST]

**Here's the description of my problem:**
Everything works normally when a disc with something on it is put in; it mounts and functions perfectly.

But after I blank the DVD-RW with Brasero, I can't use the disc at all. It doesn't mount, isn't read and is basically not even there. All I wanted to do is perform the rather trivial task of burning an ISO to a disc so I could try Sabayon Linux.

**I have attached 3 thumbnails/pictures of my problems:** [LIST]
The far left (1st) image shows what happens when I try to do anything when a blanked DVD-RW is in the drive.
[*]The middle one (2nd) depicts what happens when I insert any disc with content on it.
[*]And the far right (3rd) one displays two Terminals showing the output of: ```
dmesg | tail
mount 
```
[LIST]
[*]The left Terminal shows the output of those commands when a disc with content is inserted.
[*]The right Terminal shows what happens when I put in a blank one.
[/LIST]
[/LIST]

*If any additional information is required, or if you would like me to post text instead of pictures, do not hesitate.*

Thank You Very Much, your fellow Ubuntu user,

~ Andrew :KS

---

### Post by AnotherDave on 2010-01-06
There are a bunch of threads here with exactly the same problem, the cd/dvd burner does not recognize blank disks. I started having this problem too with Jaunty and the same story now with Karmic. 

But I have two machines, and two dvd burners.

I can put either burner in my Jaunty/Karmic machine, and it will not recognize a blank disk -- not using Brasero, and not using K3b. I can put either burner in my Debian machine and it will work flawlessly under Squeeze.

---

### Post by khelben1979 on 2010-01-06
What brand of the discs have you tried?

Do your system have [DVD+RW Tools]("http://linuxappfinder.com/package/dvd+rw-tools") installed?

---

### Post by AnotherDave on 2010-01-07
> **khelben1979 said:**
> What brand of the discs have you tried?

Me? Mine were made in northern Ubuntuland, on de Nile.

---

