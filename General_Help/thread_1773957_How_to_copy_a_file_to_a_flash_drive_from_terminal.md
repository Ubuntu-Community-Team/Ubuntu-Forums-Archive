---
title: "How to copy a file to a flash drive from terminal?"
date: 2011-06-02
forum: General Help
---

### Post by Goosemonkey on 2011-06-02
I'm new to the terminal, so how can I either copy a file (say, ~/file.txt) directly to the flash drive?

I know that I can use the command

```
sudo cp ~/file.txt ???
```

to copy it, but what goes in the question marks?

---

### Post by TeoBigusGeekus on 2011-06-02
Find out where your flash drive is mounted with
```
mount
```
, let's say /media/disk, and then give your command as
```
cp ~/file.txt /media/disk
```
You don't need sudo - I guess you're the owner of the flash drive.

---

