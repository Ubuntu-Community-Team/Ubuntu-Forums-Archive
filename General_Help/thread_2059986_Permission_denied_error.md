---
title: "Permission denied error"
date: 2012-09-19
forum: General Help
---

### Post by speedruntrainer on 2012-09-19
Hello.

Before I installed Ubuntu 12.10, I backupped the files: sources.list and the folder sources.list.d on my USB flash drive.
Then I installed Ubuntu 12.10.

I tried to copy the sources.list and sources.list.d in /ect/apt
but I get Permission denied.

What can I do?

Thanks.

---

### Post by drmrgd on 2012-09-19
Be sure to use 'sudo' when copying these files and folders as /etc/apt is owned by root.

---

### Post by speedruntrainer on 2012-09-19
Oh, ok, I didn't use the terminal, I will try.
I'll post back when I have problems.

Thanks for the reply.

---

### Post by drmrgd on 2012-09-19
You can use Nautilus too if you're more comfortable with it.  Just open Nautilus as root by running gksudo nautilus.

---

### Post by speedruntrainer on 2012-09-19
Thank you!
It works :)

---

### Post by drmrgd on 2012-09-19
Glad to help!

---

