---
title: "Authentication Keys (stored?)"
date: 2009-08-06
forum: General Help
---

### Post by Elep.Repu on 2009-08-06
I can copy my /etc/apt/sources.list, but where are the keys stored 
that I imported with apt-key add?

---

### Post by michy99 on 2009-08-06
/var/lib/apt/keyrings/ubuntu-archive-keyring.gpg or possibly other files in that same folder.

---

### Post by drs305 on 2009-08-06
Here is a way to find out what files changed recently. In your case, you could add a key, and then see what files on your computer changed in the past 1 minute.
```

sudo find / -type f -cmin 1

```

As an example, I added a new key with this command "gpg --keyserver keyserver.ubuntu.com --recv 437D05B5" and the following files changed on my system:
> 
/var/log/auth.log
/var/log/ConsoleKit/history
/var/run/console/myname
/var/run/ConsoleKit/database
/home/myname/.gnupg/pubring.gpg
/home/myname/.gnupg/trustdb.gpg
/home/myname/.gconfd/saved_state

So in this case the information was stored in my .gnupg folder.

---

### Post by michy99 on 2009-08-06
> **drs305 said:**
> Here is a way to find out what files changed recently. In your case, you could add a key, and then see what files on your computer changed in the past 1 minute.
```

sudo find / -type f -cmin 1

```

As an example, I added a new key with this command "gpg --keyserver keyserver.ubuntu.com --recv 437D05B5" and the following files changed on my system:

So in this case the information was stored in my .gnupg folder.

The command you used imported the key to your personal keyring, but not to the apt keyring. To do that you would enter:```
gpg --export --armor 437D05B5 | sudo apt-key add -
``` After which the find command would give something like:```
/var/run/sudo/mike/0
/var/log/auth.log
/etc/apt/trusted.gpg
/etc/apt/trusted.gpg~
```So it looks like they are stored in /etc/apt/trusted.gpg

---

### Post by Elep.Repu on 2009-08-06
Is it counterintuitive to re-add the gpg's on possible reinstallations, or does the /home store them all sufficiently? 
I have a separate /home partition, so nothing's changing there..
I have a script to just >to the ect/apt/sources So, if the gpgs are stored in /home I am fine correct?

I'm not sure on the apparmor stuff, or what the difference is.

---

