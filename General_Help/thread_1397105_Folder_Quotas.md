---
title: "Folder Quotas?"
date: 2010-02-02
forum: General Help
---

### Post by A&#11375;A on 2010-02-02
I was wondering if there was any way to impose a Quota on a folder where it would not permit more than a set amount of data stored in it.

I have space on a remote server, but it is limited, after a certain amount i start to get billed. I intend to just rsync the folder to the server and use this for backups, but i want to keep it as thought-free as possible so that i don't start running up charges.

Any help on this would be greatly appreciated.

---

### Post by yknivag on 2010-02-02
I've never worked out a way of applying quotas by folder (only by user).  However what you seek to do can be solved another way.

Create a partition on your disk the size of the "quota" (you may need to shrink and existing partition to make room to do this) then mount this partition as the folder that you want to give the quota too.  The end result is that the folder (incl sub folders etc) cannot get any bigger than the partition it sits on.

Hope this helps.

---

### Post by PeEllAvaj on 2010-02-02
Another technique would be to adjust the script you plan on using for rsync so that if the source size is greater than you want to put on the remote size, it doesn't rsync, and it notifies you in some way.

Would that accomplish what you are looking for?

---

### Post by A&#11375;A on 2010-02-02
> **PeEllAvaj said:**
> Another technique would be to adjust the script you plan on using for rsync so that if the source size is greater than you want to put on the remote size, it doesn't rsync, and it notifies you in some way.

Would that accomplish what you are looking for?

This would be much better than re-partitioning, the only issue is i'm new to rsync and i'd need help doing this. Any pointers or suggestions for resources on learning rsync scripting?

---

### Post by PeEllAvaj on 2010-02-03
I'm not an expert in this, so the following script wouldn't work, but it would be a start looking and trying it out:


```
#!/bin/bash
size = `du -s /path/to/folder`
if ["$size" -gt "10000"]
then
rsync -avz --whatever-you-use
else
echo "Didn't rsync, folder too big."
fi
```

---

