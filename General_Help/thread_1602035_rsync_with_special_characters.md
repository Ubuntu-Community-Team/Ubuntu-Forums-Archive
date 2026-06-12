---
title: "rsync with special characters"
date: 2010-10-20
forum: General Help
---

### Post by tenmilez on 2010-10-20
I ran a command on my macbook pro
```

rsync --verbose --human-readable --stats --ignore-existing --recursive ~/Movies ~/TV\ Shows christopher@192.168.1.141:/raid5storage/samba

```
and it worked for all my movies, except for one where I have duplicates now. If I run
```

/raid5storage/samba/Movies$ ls -l ./D*
-rw-r--r-- 1 christopher christopher 1205042803 2010-10-20 21:22 ./Déjà Vu.m4v
-rw-r--r-- 1 christopher christopher 1205042803 2010-10-18 22:09 ./Déjà Vu.m4v

```
How do I tell these two files apart and keep this from happening?

When I ran the command from the terminal on my mac it lists the file names as it's operating and spit out
```

Movies/De?\#201ja?\#200 Vu.m4v

```
and now that title shows up funky on my xbox via uShare so what I'd really like is to get rid of that one and keep rsync from from fiddling with special characters.

---

