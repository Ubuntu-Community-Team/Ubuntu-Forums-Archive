---
title: "Is it safe to chown root directory for backup?"
date: 2010-05-29
forum: General Help
---

### Post by houserparker on 2010-05-29
Hi there,

I've run a backup using rsync to my home server a few times now and once rysnc has finished it returns an error message saying "error: couldn't copy all files code 2 and 3: see previous errors". It's only a hunch but I'm assuming this has to do with user privileges to files and folders in the root directory.

Is is safe to chown root directory?

Thanks,

---

### Post by jocko on 2010-05-29
> **houserparker said:**
> Is is safe to chown root directory?
No. It is NOT safe. I don't even think you will be able to boot if you change the permissions on the wrong files.

---

### Post by houserparker on 2010-05-29
Ok, thanks.

---

### Post by CharlesA on 2010-05-29
If rsync is having problems with permissions, just run it using sudo.

---

### Post by dlebauer on 2010-07-07
What if I did, make the terrible error of doing this: 
$ chown -R /

Is there a way to undo it?

---

### Post by Calash on 2010-07-07
> **dlebauer said:**
> What if I did, make the terrible error of doing this: 
$ chown -R /

Is there a way to undo it?

Unless you have a backup, no.

You could get the system working again after some work but you will be stuck in a nightmare of a system.  All it takes is 1 file to cause you minor headaches for months.

Reinstall would be quicker and give you a more reliable system.

---

### Post by warfacegod on 2010-07-07
```
sudo chown -R root:root /
```

That *might* work to set things right again but I suspect that it would just make a bad situation much worse.

---

### Post by v1ad on 2010-07-07
> **dlebauer said:**
> What if I did, make the terrible error of doing this: 
$ chown -R /

Is there a way to undo it?

how where you able to chown -R / without providing the username.

it would have to look like this

sudo chown -R username /

---

### Post by Telengard C64 on 2010-07-07
Please don't do this.

> **warfacegod said:**
> ```
sudo chown -R root:root /
```

That command would also change ownership of all files in the /home subdirectories. Users will have difficulties getting things done if they can't write to any files. In fact, I am pretty sure this would break a lot of applications which would not be able to write to their config files and logs.

---

### Post by v1ad on 2010-07-07
yes DONT DO THAT.

i was merely using it as an example and was wondering how did your command appear to work.

and instead of chown may addgroup, add it to the same group.

---

### Post by endotherm on 2010-07-07
> **dlebauer said:**
> What if I did, make the terrible error of doing this: 
$ chown -R /

Is there a way to undo it?

no, which is exactly why it isn't safe to do it for a backup. if you restore it, all your ownership will be messed up. since you can't recover the ownership info, the files themselves are largely useless, unless you are hunting for one specifically, and already know the ownership/permissions it should have once restored. 

personally I'd look into imaging the partition, rather than backing up the files in /.

---

### Post by warfacegod on 2010-07-07
> **Telengard C64 said:**
> Please don't do this.



That command would also change ownership of all files in the /home subdirectories. Users will have difficulties getting things done if they can't write to any files. In fact, I am pretty sure this would break a lot of applications which would not be able to write to their config files and logs.

Fixing the /home ownership afterward would be simple:

```
sudo chown -R username:usergroup /home/username
```

I'm still not suggesting running the first command I posted but, then again, chowning root shouldn't have been done in the first place.

---

