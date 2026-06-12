---
title: "FSCK FSCK_MAX_INST Environment Variable"
date: 2011-05-09
forum: General Help
---

### Post by Delphinus369 on 2011-05-09
Does anyone know what file I have to modify to set the environment variables for FSCK? I can't run FSCK on my file system because it runs out of memory after about 10 minutes. This variable sounds like it will solve all of my problems but I can't find the file to modify to set the variable or what parameters it takes (number? yes/no?, etc).

I would appreciate anyone's help as the device I'm trying to recover has a lot of information on it that I would really like to get back.

Thanks for any help.

---

### Post by marshmallow1304 on 2011-05-09
```
FSCK_MAX_INST="<value>" fsck <arguments>
```

FSCK_MAX_INST takes a number corresponding to the maximum number of file system checkers to run at once.  I've never used it, but it looks like you should try a low number to avoid running out of memory.

---

### Post by Delphinus369 on 2011-05-09
Thanks MarshMallow. I tried it with a 5 and 3 and it still failed with a memory allocation error. I'm trying it with a 1 now and hopefully that will successfully finish.

Do you know if fsck writes to a log any where? Maybe that memory allocation error isn't really what's causing it to abort.

Thanks again.

---

### Post by AlphaLexman on 2011-05-09
> **Delphinus369 said:**
> Do you know if fsck writes to a log any where? Maybe that memory allocation error isn't really what's causing it to abort.
See:
```
/var/log/fsck/
```

---

### Post by Delphinus369 on 2011-05-10
Well the command:

> sudo FSCK_MAX_INST="1" fsck -y -C /dev/md1


Has helped someone, it runs a little bit longer than it does without the variable but still errors out after about 20 minutes with a memory allocation error and nothing is written to /var/log/fsck or to dmesg.

The only good news is that the scan seems to be cumulative. So when it does run it's doing something and it picks up from that point the next time I run it. The bad news is, this is a 14 TB RAID array and I've been running it for two days and it's only at 0.5%.  This having to start it constantly is annoying to say the least.

I even went so far as to do a "manual" scan (no -y) and set a weight on the enter key to answer yes to all the questions but even that quits out after about 15 minutes with a memory allocation error. I just can't seem to figure out how to keep this scan running. I would think 2 gigs of RAM is enough for the system to run constantly but I guess not.

If anyone else has any other ideas I would greatly appreciate them.

Thanks.

---

