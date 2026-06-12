---
title: "Permissions question"
date: 2011-07-01
forum: General Help
---

### Post by ClientAlive on 2011-07-01
I'm recovering someone's data of an old ide drive for them. It's an NTFS file system on that drive. I used the dd command to make a raw image of that drive onto my external ubd drive but now I see that the owner and group of that file is root.

```

. . . root:root . . .

```

Is this going to cause that person problems when I give his data to him and he tries to access or do anything with it?

By the way, I think the reason it has those permissions is that I used Ubuntu 10.04 live to make the image and I had to log in as root to execute the command.

Thanks in advance for any help.

---

### Post by prodigy_ on 2011-07-01
Short answer: no, it won't cause any problems.

---

### Post by ClientAlive on 2011-07-01
> **prodigy_ said:**
> Short answer: no, it won't cause any problems.


Oh good! Someone came along. I've just had the whole thing sitting there while I try to find out more.

So the guy will be able to open and manipulate things in that image if I just burn it to a disk?

I might use file-roller to extract the data first though. I can't imagine that would change the answer though.

---

### Post by prodigy_ on 2011-07-01
> **ClientAlive said:**
> So the guy will be able to open and manipulate things in that image if I just burn it to a disk?
Sure. No matter if your friend uses Linux or another OS. If he uses Linux he can also take ownership of this file with **chown** command.

---

### Post by ClientAlive on 2011-07-01
> **prodigy_ said:**
> Sure. No matter if your friend uses Linux or another OS. If he uses Linux he can also take ownership of this file with **chown** command.


Right on. Thanks man.

Have a great weekend!

---

