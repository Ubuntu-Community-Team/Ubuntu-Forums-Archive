---
title: "Tar"
date: 2010-07-16
forum: General Help
---

### Post by puma1 on 2010-07-16
Using programs like tar. how is one supposed to know all of the switches for each app like tar. are they even called switches in linux, or something else like "options"? 

for example

$ tar cvpzf filename.tgz 

what does cvpzf stand for? why is it so cryptic?

---

### Post by cbraxton on 2010-07-16
> **puma1 said:**
> Using programs like tar. how is one supposed to know all of the switches for each app like tar. are they even called switches in linux, or something else like "options"?

$ man tar

> for example
$ tar cvpzf filename.tgz
 what does cvpzf stand for? why is it so cryptic?

c == Create tar archive
v == Verbose
p == Preserve permissions
z == Compress with gzip
f == Next arg is archive filename

Many of the commands in Ubuntu such as tar tend to be cryptic because they were originally designed on Unix systems 30-40 years ago when machine resources were scarce and expensive, and one frequently interacted with the system via a hardcopy terminal (such as ASR33 Teletype or DECwriter) and/or a slow serial link.

---

