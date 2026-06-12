---
title: "How to run script on shutdown?"
date: 2010-03-13
forum: General Help
---

### Post by Cenoforums on 2010-03-13
Hi,

I have a bash script I need to run when I shutdown my computer. I tried referencing it in /etc/gdm/PostSession/Default, but weirdly it only runs on a logout, not a shutdown. I think this used to work in Jaunty but not anymore. Any ideas?

---

### Post by dcstar on 2010-03-13
> **Cenoforums said:**
> Hi,

I have a bash script I need to run when I shutdown my computer. I tried referencing it in /etc/gdm/PostSession/Default, but weirdly it only runs on a logout, not a shutdown. I think this used to work in Jaunty but not anymore. Any ideas?

The etc/rc0.d folder is full of things that are all run at shutdown (rc6.d for reboot).

---

### Post by Cenoforums on 2010-03-16
Thx for the reply. Is that the same folder that contains the scripts that run during the shutdown process, which you can actually read output from during shutdown? I was looking for something much more basic that worked both on shutdown and reboot...

---

### Post by Cenoforums on 2010-03-24
bump. Any point in the right direction would be appreciated.

---

