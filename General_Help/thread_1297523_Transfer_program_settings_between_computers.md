---
title: "Transfer program settings between computers"
date: 2009-10-21
forum: General Help
---

### Post by MFGorilla on 2009-10-21
Several months ago I installed ubuntu as a dual boot on my main computer and loved it!  Now, I've finally gotten my hands on another computer and installed Ubunu 9.04.

Now I am wondering if there is a way of transferring settings, etc. from the dual boot machine to the other ubuntu box.  Specifically I want to transfer my email and calendar from Thunderbird and account info from Pidgin.

Thanks.

---

### Post by Giblet5 on 2009-10-21
Can you establish a network connection between the two systems?

Let's say that the old system is system-A and the new one is system-B.

We'll assume your username is rick on both.

On system-A, install the ssh server: ```
sudo apt-get install openssh-server
```

When that's done, log into system-B. Bring up a terminal window.

```
sudo rsync -aurvpt [ip address of system-A]:/home/rick/ /home/rick
```

That will synchronize your "rick" account on System-B with the same account on system-A. Files. Folders. File permissions. File timestamps. Settings. Everything.

It's not a perfect synchronization: files on system-B that don't exist on system-A, or are newer on system-B, will not be touched.

Rsync simply makes a matched copy.

---

### Post by Roasted on 2009-10-21
rsync is a good call, mostly because the hidden files/folders in your home directory are what contain your program settings.

Hidden files/folders begin with a period in front of them, so .amarok is where your amarok settings are, etc.

If all else fails, you could simply USB flash drive them to the other computer as well. This, of course, depends on the size of them.

---

