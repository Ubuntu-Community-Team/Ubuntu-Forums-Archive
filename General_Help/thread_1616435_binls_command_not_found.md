---
title: "/bin/ls command not found"
date: 2010-11-08
forum: General Help
---

### Post by J2R on 2010-11-08
I'm wondering whether my server has been hacked by someone trying to cover their tracks. When I log in now, I get a message saying "bash: /bin/ls: No such file or directory", and although 'which ls' tells me it's '/bin/ls', it is as if the command does not exist. Note that this NOT a path issue: I get the error when typing '/bin/ls' (and '/usr/bin/ls', which I thought worth trying). I tried to 'sudo chmod +x /bin/ls' and the operation was not permitted.

OK, so thinking I'd somehow hosed things, I did 'sudo apt-get install --reinstall coreutils', hoping to reinstall ls etc. I get this:

```
Preparing to replace coreutils 8.5-1ubuntu3 (using .../coreutils_8.5-1ubuntu3_amd64.deb) ...
Unpacking replacement coreutils ...
dpkg: error processing /var/cache/apt/archives/coreutils_8.5-1ubuntu3_amd64.deb (--unpack):
 unable to create `/bin/cat.dpkg-new' (while processing `./bin/cat'): Permission denied
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/coreutils_8.5-1ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas what might be going on, and can I rescue things without a complete reinstall?

(This is Ubuntu Server Maverick Meerkat, I should say).

---

### Post by wojox on 2010-11-08
Go to /var/cache/apt/archives and very carefully, do a dpkg -i of the problematic package.

```
sudo dpkg -i coreutils_8.5-1ubuntu3_amd64.deb
```

---

### Post by J2R on 2010-11-08
This is what  get:

```
dpkg: error processing coreutils_8.5-1ubuntu3_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 coreutils_8.5-1ubuntu3_amd64.deb
```

I can see from the auth.log that there have been dozens of break-in attempts over the last couple of days, so I'm increasingly thinking it's been hacked.

---

### Post by skillet-thief on 2010-11-08
FWIW, I had a server compromised once, and this was how we noticed it, some strange output at the command line, but I'm not sure that it was /bin/ls. Is ls the only program doing that?

---

### Post by J2R on 2010-11-08
Sorry, ignore that last post, I wasn't in the right directory. This is what I get:

```
(Reading database ... 72327 files and directories currently installed.)
Preparing to replace coreutils 8.5-1ubuntu3 (using coreutils_8.5-1ubuntu3_amd64.deb) ...
Unpacking replacement coreutils ...
dpkg: error processing coreutils_8.5-1ubuntu3_amd64.deb (--install):
 unable to create `/bin/cat.dpkg-new' (while processing `./bin/cat'): Permission denied
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 coreutils_8.5-1ubuntu3_amd64.deb

```

---

### Post by J2R on 2010-11-08
> **skillet-thief said:**
> FWIW, I had a server compromised once, and this was how we noticed it, some strange output at the command line, but I'm not sure that it was /bin/ls. Is ls the only program doing that?

The only one I've discovered so far, but I haven't looked in depth yet.

---

### Post by skillet-thief on 2010-11-08
It might be time to start looking for rootkits. I used chkrootkit, but that was several years ago. There may be something better now.

---

### Post by djhedges on 2012-02-21
A little late but another good solution in case someone else stumbles across this post.

```
sudo apt-get install --reinstall coreutils
```

---

### Post by oldos2er on 2012-02-22
Closed, necromancy.

---

