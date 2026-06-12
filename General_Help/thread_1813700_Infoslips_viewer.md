---
title: "Infoslips viewer"
date: 2011-07-28
forum: General Help
---

### Post by tallanddaft on 2011-07-28
Hello All,

Not sure if this is the right place for this, please redirect if not. 

I'm new to Ubuntu, and was trying to install Infoslips viewer, using the instructions on their website. [http://www.infoslips.com/downloads.aspx](http://www.infoslips.com/downloads.aspx)

However, I couldn't open the root directory, and the more I looked at the instructions, the more there seemed something wrong with them, maybe that the terminal would default to the root?

Just wondering if these instructions looked legit to you guys.

Cheers,

Owain

---

### Post by sanderd17 on 2011-07-28
They assume an unsafe, old Linux way.

Linux used to have exactly one active root user and some other normal users. The only user that could install an application was the root user. This caused a lot of users to stay logged in as root and thus opening everything to malware.

That's why Ubuntu created the "sudo" command. Sudo stands for super-user-do. So that means you become root or super-user for one command.

So if you adapt those commands to the current way, you just need to place them in you home folder (which is /root for the root user and /home/username for other regular users) and execute the script with a "sudo" in front of it. So
```

sudo sh infoViewer_unix_1_0_0_3.sh

```

For the rest, I don't see anything weird, but off coarse you need to trust the application developers. When you give root rights to a command, that command can do anything, including formatting your computer.

---

