---
title: "help !! tar: This does not look like a tar archive"
date: 2012-04-30
forum: General Help
---

### Post by huangweiqiu on 2012-04-30
I split a huge folder:~

[HTML]tar cvpf - somedir | split -b 50000m[/HTML]

and then,I transfered split files to another server and merge it:~

[HTML]cat x* > somedir.tar.gz[/HTML]

but when I tried to extract the file, it shows errors:~

[HTML]tar xvf tar xvf somedir.tar.gz 
tar: This does not look like a tar archive
 tar: Skipping to next header
 tar: Archive contains obsolescent base-64 headers 
tar: Error exit delayed from previous errors[/HTML]

---

### Post by erind on 2012-05-01
> **huangweiqiu said:**
> I split a huge folder:~

[HTML]tar cvpf - somedir | split -b 50000m[/HTML][...]
Maybe a typo, but it's missing '**-z**' option of *tar*,

```
tar cvpf**z** - somedir | split -b 50000m
```> and then,I transfered split files to another server and merge it:~
```
cat x* > somedir.tar.gz
```Try:

```
cat x* | tar xzpvf -

```

---

