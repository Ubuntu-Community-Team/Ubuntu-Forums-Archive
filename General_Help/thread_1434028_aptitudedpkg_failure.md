---
title: "aptitude/dpkg failure"
date: 2010-03-19
forum: General Help
---

### Post by ilembitov on 2010-03-19
Hi, all.

Looks like my package manager was severely screwed. Any package manager-related command I try to run results in the following message in the console:

```

E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

```

Anything - aptitude, apt-get.

I removed all my sources.lists, I tried running apt-cache clean (it's what I could google up). It didn't help. Can anyone help me with this one? This is really serious. Not only am I unable to do anything with packages (update, remove, install), but the machine is really slow because of this.

---

### Post by Rocket2DMn on 2010-03-19
Hi, you should be able to generate a new sources.list file here: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

I haven't used that site myself, but I tested it out and it looks OK.  There used to be something similar on another site that I know worked well, but they took it down.  You will take the generated text that gives you and put it in the sources.list file, then run
```
sudo apt-get update
```
Then you can go about doing upgrades or installing software.

---

### Post by ilembitov on 2010-03-19
Didn't help. Here is what I got:

```


  GNU nano 2.0.9                                    File: /etc/apt/sources.list                                                                              

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ru.archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse

###### Ubuntu Update Repos
deb http://ru.archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://ru.archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu karmic partner



```

Works the same way. It gives the same error message.

---

### Post by Helix7 on 2010-03-19
Check the permissions of the /etc/apt/sources.list

mine are 

-rw-r--r--   1 root root  2919 2010-03-19 16:35 sources.list


Just a thought

---

### Post by ilembitov on 2010-03-19
> **Helix7 said:**
> Check the permissions of the /etc/apt/sources.list

mine are 

-rw-r--r--   1 root root  2919 2010-03-19 16:35 sources.list


Just a thought

Looks fine to me:

```

-rw-r--r-- 1 root root 595 2010-03-20 02:31 /etc/apt/sources.list

```

Am I wrong?

---

### Post by Helix7 on 2010-03-19
yes that looks right to me. what do you get when you run 

> sudo dpkg --configure -a> sudo dpkg --auditI am just wondering if something got messed up in the dependencies for apt-get


Edit: I was looking around and i found this thread might help

[http://www.linuxforums.org/forum/ubuntu-help/104741-solved-package-manager-errors.html](http://www.linuxforums.org/forum/ubuntu-help/104741-solved-package-manager-errors.html)

---

### Post by gmargo on 2010-03-19
> **ilembitov said:**
> **E: The package lists or status file could not be parsed or opened.**


Package lists live in /var/lib/apt/lists/.
The status file is /var/lib/dpkg/status.
So check the /var/lib/apt/lists/ and /var/lib/dpkg/ directories.

---

### Post by ilembitov on 2010-03-19
> **Helix7 said:**
> yes that looks right to me. what do you get when you run 

I am just wondering if something got messed up in the dependencies for apt-get


Edit: I was looking around and i found this thread might help

[http://www.linuxforums.org/forum/ubuntu-help/104741-solved-package-manager-errors.html](http://www.linuxforums.org/forum/ubuntu-help/104741-solved-package-manager-errors.html)

Well, it told me it couldn't read the available and state files, so I moved them to a different location for backup and created empty files instead of them. Now it only gives me "E: Read error - read (5: Input/output error)" message and the dpkg --audit doesn't produce any output. the other command also doesn't say anything.

---

### Post by Rocket2DMn on 2010-03-19
If your sources.list file is ok, then /var/lib/dpkg/status may be messed up - try overwriting it with a backup from /var/backups (e.g. the latest: /var/backups/dpkg.status.0)
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.old
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
sudo apt-get update
```

---

### Post by ilembitov on 2010-03-20
> **Rocket2DMn said:**
> If your sources.list file is ok, then /var/lib/dpkg/status may be messed up - try overwriting it with a backup from /var/backups (e.g. the latest: /var/backups/dpkg.status.0)
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.old
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
sudo apt-get update
```

Well, it did seem to have some positive effect - the old error messages are out, the new are in =)

Now I get

```
E: Couldn't configure pre-depend libc6 for findutils, probably a dependency cycle.

```

every time I try to do something. apt-get install -f, aptitude safe-upgrade - anything.

---

### Post by gmargo on 2010-03-20
Can you provide the list of non-fully-installed packages?
```

dpkg -l | grep -v ^ii

```

---

### Post by ilembitov on 2010-03-20
> **gmargo said:**
> Can you provide the list of non-fully-installed packages?
```

dpkg -l | grep -v ^ii

```

```
ilembitov@ilembitov-laptop:~$ sudo dpkg -l | grep -v ^ii 
dpkg-query: parse error, in file '/var/lib/dpkg/status' near line 1948 package 'module-init-tools':
 EOF during value of field `Maintainer' (missing final newline)

```

---

### Post by gmargo on 2010-03-20
Open /var/lib/dpkg/status in a text editor and see what's going on with that line.  Was the file truncated there?  Do you need to go back to a prior backup file?

---

### Post by ilembitov on 2010-03-21
> **gmargo said:**
> Open /var/lib/dpkg/status in a text editor and see what's going on with that line.  Was the file truncated there?  Do you need to go back to a prior backup file?

OK, it never ends... The file really was truncated, so I reverted to a -old file. Now I get this error:

```
E: Internal Error, Could not perform immediate configuration (2) on libattr1
```

whenever I try to run upgrade from Synaptic or Update Manager. When I try to run aptitude safe-upgrade from console, it just says it can't read extended_states file. Which I restored (previously I have emptied it after making a backup), but the message is the same. How do I fix this file?

The funny thing is, that while aptitude sees that there are updates pending, apt-get doesn't, even if I try to refresh the lists with apt-get update.

---

### Post by gmargo on 2010-03-21
Again, what are the results of 
```

dpkg -l | grep -v ^ii

```

---

### Post by ilembitov on 2010-03-21
> **gmargo said:**
> Again, what are the results of 
```

dpkg -l | grep -v ^ii

```

Sorry, forgot to mention it. There aren't any. Even without grepping.

---

### Post by slotto on 2010-06-09
> **Rocket2DMn said:**
> If your sources.list file is ok, then /var/lib/dpkg/status may be messed up - try overwriting it with a backup from /var/backups (e.g. the latest: /var/backups/dpkg.status.0)
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.old
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
sudo apt-get update
```


I LOVE this forum! This helped a BUNCH! I had a similar problem of a missing status file.
Thanks everyone!
Steve

---

