---
title: "AppArmor parser error"
date: 2011-01-12
forum: General Help
---

### Post by g.a. on 2011-01-12
During the boot I read the following

```
AppArmor profiles failed to load
```

the dmesg command does not give any information and so the apparmor log.
The following holds

```
sudo /etc/init.d/apparmor start
 * Starting AppArmor profiles
AppArmor parser error in /etc/apparmor.d/usr.bin.evince at line 1146: missing an end of line character? (entry: /usr/bin/totem)
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                                                             [ OK ]
```

but the file is much smaller than 1146 lines.

Any suggestion?

I'm running 

```
uname -a
Linux trinity 2.6.31-22-generic #70-Ubuntu SMP Wed Dec 1 23:51:13 UTC 2010 i686 GNU/Linux

```

and 

```
sudo aptitude show apparmor
Package: apparmor
State: installed
Version: 2.3.1+1403-0ubuntu27.4

```

thanks in advance,
g.

---

### Post by takezero on 2013-04-16
I know this post is old, but for the benefit of anyone else arriving via a Google search (like I did) I thought I'd respond.

Make sure any abstractions (e.g. /etc/apparmor.d/abstractions/user-tmp in my case) always end with the assumption that they'll be chained to another ruleset, so instead of:

```

# global tmp directories
/tmp/ rw,
/opt/tmp/ rw

```

you'd want:

```

# global tmp directories
/tmp/ rw,
/opt/tmp/ rw,

```

(note the trailing comma on the last line).

---

### Post by papibe on 2013-04-16
Please don't reply on old threads. It is much better to create a new one. Feel free to link this one if you want.

From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

**Thread Closed**.

---

