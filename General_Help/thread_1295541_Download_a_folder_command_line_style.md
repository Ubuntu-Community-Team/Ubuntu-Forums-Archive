---
title: "Download a folder command line style"
date: 2009-10-19
forum: General Help
---

### Post by Superdude_123 on 2009-10-19
How do I transfer a folder (with files) from Server A to Server B, by using command line commands via SSH? It should be noted that the source server (where the file is now) isn't running on default port 22.

---

### Post by Giblet5 on 2009-10-19
```
rsync -aurptd /home/somedir/ host2:/home/somedir
```

That will transfer (or update changes to) /home/somedir on both systems. If this be over the intertubes, I'd add a -z option for compression.

---

### Post by Superdude_123 on 2009-10-19
So how do I write that host 2 is at port 123?

---

### Post by Giblet5 on 2009-10-19
> **Superdude_123 said:**
> So how do I write that host 2 is at port 123?

Add the option: ```
-rsh='ssh -p123'
```

Rsync is like bacon: there's nothing it can't do.

---

### Post by Superdude_123 on 2009-10-19
So the hole command would be:

rsync -aurptd /home/somedir/ host2:/home/somedir -rsh='ssh -p123' ?

---

### Post by Giblet5 on 2009-10-19
> **Superdude_123 said:**
> So the hole command would be:

rsync -aurptd /home/somedir/ host2:/home/somedir -rsh='ssh -p123' ?

I dropped a '-' there... Sorry.

Well, I'd put the options first, as in
```
rsync -aurptd --rsh='ssh -p123' /home/somedir/ host2:/home/somedir
``` but either would likely work.

And ```
rsync -aurptd -e 'ssh -p123' /home/somedir/ host2:/home/somedir
``` will do exactly the same thing, using the -e equivalent syntax.

---

### Post by Sam on 2009-10-19
SSH equivalent would be:
```
scp -r -P 123 /path/to/dir user@host:/path/to/dest
```

But rsync is better if the host supports it (because it updates only what needs to be updated and can preserve permission/ownership/timestamps/etc).

---

### Post by Giblet5 on 2009-10-19
> **Sam said:**
> SSH equivalent would be:
```
scp -r -P 123 /path/to/dir user@host:/path/to/dest
```

But rsync is better if the host supports it (because it updates only what needs to be updated and can preserve permission/ownership/timestamps/etc).

And, the scp form always copies while rsync only copies the changes.

That's really handy if you're backing up over a 300 baud modem.

---

### Post by falconindy on 2009-10-19
> **Giblet5 said:**
> And, the scp form always copies while rsync only copies the changes.

That's really handy if you're backing up over a 300 baud modem.
Except that rsync essentially has to download a manifest of the destination files in order to calculate the changes. This can add a fair bit of overhead and transfer time, depending on the size of your seed (as I unfortunately found out using rsync with Amazon S3).

---

