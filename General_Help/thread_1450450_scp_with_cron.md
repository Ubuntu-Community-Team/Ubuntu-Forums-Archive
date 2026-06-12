---
title: "scp with cron"
date: 2010-04-09
forum: General Help
---

### Post by Hell3fire on 2010-04-09
Hi!

I have made a small script which is taring a folder, scp it to another server before extracting:

```

#!/bin/bash


HOST='user@host';

rm files.tar

tar -czf files.tar the_files

scp files.tar $HOST:/home/user/
ssh $HOST 'tar -xzf files.tar';

```

This works all fine when running from the shell (and yes, I can use ssh/scp without password :)), but when I'm trying to run it from cron, it seems like only a small part of 'files.tar' (45kb or so) is sent to the HOST-server.

Any suggestions to my problem? :)

---

### Post by dcstar on 2010-04-09
> **Hell3fire said:**
> Hi!

I have made a small script which is taring a folder, scp it to another server before extracting:

```

#!/bin/bash


HOST='user@host';

rm files.tar

tar -czf files.tar the_files

scp files.tar $HOST:/home/user/
ssh $HOST 'tar -xzf files.tar';

```

This works all fine when running from the shell (and yes, I can use ssh/scp without password :)), but when I'm trying to run it from cron, it seems like only a small part of 'files.tar' (45kb or so) is sent to the HOST-server.

Any suggestions to my problem? :)
The second item should only run if the first exits successfully:
```
scp files.tar $HOST:/home/user/ && ssh $HOST 'tar -xzf files.tar'
```

---

### Post by Hell3fire on 2010-04-09
Thanks for reply! That's good to know :)

I found it out myself; adding 'cd /path/to/script/folder' to the beginging of the script made it work.

---

