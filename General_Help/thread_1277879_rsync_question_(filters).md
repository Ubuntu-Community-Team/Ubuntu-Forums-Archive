---
title: "rsync question (filters)"
date: 2009-09-28
forum: General Help
---

### Post by undecim on 2009-09-28
(Using rsync 3.0.5 on Ubuntu Server 9.04 amd64)

I'm trying to change a snapshot script I've written to take the "important" directory from each users home directory and copy it to /var/user-backups/ (currently, it does this only to the /var/user-backups/current/ directory)

The problem is that I can't get rsync's filters to work like I want. From I read with man rsync, I should create the following filter rules: "+ */important/" and "- *", but no combination of those is working. 

I've been playing around with the filters using the -n and -v flags, but can't get what I need.

```
$ rsync -nv --filter="- */important/" /home/ /var/user-backups
```yields a list of every file in my home directory except the "important" directory, so I know that */important/ is the correct syntax to refer to the folders I want, but both...

```
$ rsync -nv --filter="+ */important/" --filter="- *"  /home/ /var/user-backups
```...and...

```
$ rsync -nv  --filter="- *" --filter="+ */important/"  /home/ /var/user-backups 
```...give me empty lists! Does order not matter? or am I completely missing something? I just want every /home/*/important/ folder, but including any "- *" rule (as i've seen at the end of every example) gives me nothing at all, and without it, I just get every file in my home directory.

---

### Post by StuartN on 2009-09-29
I think you need something more like **--filter "+ /home/**/important/*, - /home/**/*"** because your filter rule must specifically include the entire path to be included.

---

### Post by undecim on 2009-09-29
This still gives me an empty list...
```
undecim@midnight:~$ rsync -nv --filter "+ /home/**/important/*, - /home/**/*"  /home/ /var/user-backups/
skipping directory .

sent 8 bytes  received 12 bytes  40.00 bytes/sec
total size is 0  speedup is 0.00 (DRY RUN)
undecim@midnight:~$ 
```

---

