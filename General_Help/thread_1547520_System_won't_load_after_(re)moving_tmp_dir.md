---
title: "System won't load after (re)moving /tmp dir"
date: 2010-08-06
forum: General Help
---

### Post by darkmaxa on 2010-08-06
I've tried to move /tmp dir to another drive. So, I've deleted /tmp, created tmp dir on /mnt/Storage, and then make /tmp link on the root that points to /mnt/Storage/tmp

Just after that, I've run gedit and it started to make hundreds of new temp dirs in /mnt/Storage/tmp, and after few seconds the system was freezed.

After (hard) restart, the system couldn't boot anymore, even in recovery mode. So I've booted LiveCD, deleted /tmp link and created new empty /tmp dir on the root. Now, system is trying to load desktop, but after few blinks it says that can load only "in low graphics mode", but even that option doesn't work (just blank screen).

I can choose option to go to console, a /tmp dir is here, in /mnt there are mounted drives, so everything looks OK, but X server doesn't work anymore.

I'm new in Linux world, but I'm stunned that re(moving) tmp folder can cause complete system failure!?

---

### Post by dcstar on 2010-08-06
> **darkmaxa said:**
> 
...........
I'm new in Linux world, but I'm stunned that re(moving) tmp folder can cause complete system failure!?

System folder are specifically created for **exclusive** system use with specific permissions and attributes. /tmp is a system folder.

Why would you think that playing with something that you have no business touching would **not** cause problems?

---

### Post by darkmaxa on 2010-08-06
My mistake. In Windows any tmp folder or file (system or user created) can be safely deleted (almost) at any time.

Nevermind, can you help me with this?

---

### Post by darkmaxa on 2010-08-06
I've solved the problem.

If someone do same mistake, solution is to create new tmp dir, and then
```

sudo chown root:root /tmp
sudo chmod 1777 /tmp

```My Ubuntu is running without any problems now. :)

So, is there any safe way to move tmp folder? My Ubuntu is installed on SSD drive, so I've want to move all tmp folders to storage drive, to reduce writes to SSD.

---

