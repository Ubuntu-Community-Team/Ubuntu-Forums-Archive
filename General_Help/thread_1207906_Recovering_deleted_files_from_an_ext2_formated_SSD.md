---
title: "Recovering deleted files from an ext2 formated SSD drive"
date: 2009-07-08
forum: General Help
---

### Post by eks on 2009-07-08
Hello,

My wife was on a trip and was out of space on the /home partition of the 8gb SSD drive of our Aspire One.

Then, saved a couple of days of photos to /tmp...........

**How would one proceed to salvage as much files as possible on this situation?** She hasn't used much the computer since, and the /tmp partition is with all the rest of the file system, and has 2.2gb free (which at least 1gb is of those deleted photos).

I've tried:

```

foremost -v -t jpg -i /tmp -o /home/user/recover
```

But it seems its about to start but I'm not sure it does. The HD led does not flashes or anything, and there's no feedback on the screen, despite the -verbose option.

I'm taking a look at e2undel, magicrescue and recover. But I'm thinking if maybe would be better to try some specific "file recovery distro", so I can have the file system unmounted? I've so far found a recommendation for Puppy Linux from the eeebuntu forums.

---

### Post by michy99 on 2009-07-08
You definitely need to have the partition unmounted because every second you have it mounted, you risk having the files overwritten. You might give photorec a try. It is part of the testdisk package.

---

### Post by eks on 2009-07-08
Thanks!

I've just installed testdisk and the other packages on the live cd(/USB). I will try to run them on the netbook tomorrow.

---

