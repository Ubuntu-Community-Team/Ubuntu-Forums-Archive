---
title: "How to fix 'broken software index'?"
date: 2010-06-05
forum: General Help
---

### Post by whitefort on 2010-06-05
Hi.  I'm unable to use synaptic or update manager.  There appears to be a package that's gone wrong, but I can't find any way to uninstall it.

Does the following make sense to anyone?

> john@lookingglass:~$ sudo apt-get remove psb-kernel-headers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  psb-kernel-headers
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 471kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 164674 files and directories currently installed.)
Removing psb-kernel-headers ...
No diversion `any diversion of /usr/include/drm/drm_sarea.h', none removed
No diversion `any diversion of /usr/include/drm/drm.h', none removed
No diversion `any diversion of /usr/include/drm/drm_hashtab.h', none removed
No diversion `any diversion of /usr/include/drm/i915_drm.h', none removed
rm: cannot remove `/usr/include/drm-linux-libc': Is a directory
dpkg: error processing psb-kernel-headers (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 psb-kernel-headers
E: Sub-process /usr/bin/dpkg returned an error code (1)
The problem seems to be psb-kernel-headers, but I've no clue how to get rid of it.

I'd be really grateful if anybody can point me in the right direction to fix this.  Otherwise I think I'm looking at a complete re-installation of Ubuntu, and I'd rather avoid that hassle... Also, I'd really like to learn a bit more about what's gone wrong and how to fix it.  thanks!

PS - I've also tried 'sudo apt-get -f install', but it just gives a message similar to that above.

---

### Post by elliotn on 2010-06-05
Use sudo apt-get install -f

Or sudo amptitute update

Am not sure it'll work

---

### Post by whitefort on 2010-06-05
Thanks - I already tried sudo apt-get install -f, and my computer has no idea what sudo amptitute update is  (neither do I!)

I'm wondering if it will do terrible damage if I go rooting around in the file system and try to delete stuff manually...

---

### Post by elliotn on 2010-06-05
Just try it

---

### Post by phr33k-dc on 2010-06-05
dnt worry that is not a malicious command. give it ago

---

### Post by wojox on 2010-06-05
It's aptitude not amptitute

How did you get that kernel?

---

### Post by Leppie on 2010-06-05
> **elliotn said:**
> Or sudo amptitute update
that should be:
```
sudo aptitude update
```
try the following:
```
sudo dpkg --purge --force-remove-reinstreq psb-kernel-headers
```

---

### Post by whitefort on 2010-06-05
Ok...  I'll probably REALLY regret this further down the line, but I just went into  /var/lib/dpkg/info and deleting everything that included the name of the package that was causing the problem.  Then the next time I ran apt-get -f install, it seemed to fix everything.

Update manager and synaptic seem to be working fine again.  I'm not recommending this to anyone (I found the suggestion on a Google search).  For all I know, deleting those files might cause me major problems later.

But for now, I'm marking the thread solved.

Thanks, everybody.

---

### Post by charlie-sierra on 2010-06-07
I got the same problem, after reading through the files listed in /var/lib/dpkg/info , i realized that the problem was the post-removal-script for psb-kernel-headers.
To solve it, simply
```

cd /var/lib/dpkg/info
sudo vim psb-kernel-headers.postrm

```and then change the line
```
rm -f /usr/include/drm-linux-libc
```to
```
rmdir /usr/include/drm-linux-libc
```The next time you try to remove psb-kernel-headers, you shouldn't get any errors.

---

