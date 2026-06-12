---
title: "Can ubuntu remember what drives are mounted?"
date: 2009-07-24
forum: General Help
---

### Post by starbase1 on 2009-07-24
I feel I am making good progress with understanding Ubuntu better, and getting what I want from it. The file system is begining to make sense to me!

One thing I would like though - I am using a dual boot machine, and a lot of useful stuff, (such as my music, videos, and photos), are not under the main Ubuntu file system, but on separate hard drives, (with different drive letters under windows).

Now I can mount them when I bring up the machine, but it would be really convenient if Ubuntu would remember where I was last time, so the drives are attached from the very start without me having to click around.

Is this possible?

Thanks,
Nick

---

### Post by wojox on 2009-07-24
Haven't used it but my buddy says it's great:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jasonsjunk on 2009-07-24
The answer is yes, you have to add the drives to your fstab file so they will be automatically mounted when the computer boots up.  

You can read up on fstab here:  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

and another good write up is here:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by bacil on 2009-07-24
add them to /etc/fstab
eg

```

<file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sd2              /windisk            -             -                   -               -

```

---

### Post by sisco311 on 2009-07-24
for windows(ntfs) partitions: [http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig")

or pysdm:
[GUI Fstab Editing with PySDM]("http://ubuntuforums.org/showthread.php?t=872197")

or manually edit fstab:
[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")

EDIT: i'm toooooo slooooooow ......... :)

---

### Post by starbase1 on 2009-07-24
Wow! So many helpful replies so fast - cheers guys!
:P

---

### Post by jasonsjunk on 2009-07-24
LOL, I am sooo bored at work tonight I am just sitting here browsing the new posts as they come up.  The hardest part is that I am at work using a POS Win2000 slow as hell computer instead of my smooth as silk fast Ubuntu box I have at home.

---

### Post by starbase1 on 2009-07-27
> **sisco311 said:**
> for windows(ntfs) partitions: [http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig")

or pysdm:
[GUI Fstab Editing with PySDM]("http://ubuntuforums.org/showthread.php?t=872197")

or manually edit fstab:
[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")

EDIT: i'm toooooo slooooooow ......... :)

It took me a couple of goes to get my head around it, but PySDM did the trick, thanks!

Nick

---

