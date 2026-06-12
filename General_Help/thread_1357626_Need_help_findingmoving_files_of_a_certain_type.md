---
title: "Need help finding/moving files of a certain type"
date: 2009-12-17
forum: General Help
---

### Post by mailman1175 on 2009-12-17
Not really sure where to post this, so feel free to move it if need be…

I have a large music directory with a number of subdirectories (three or four levels deep). I'd like to recursively search the entire music directory for all files of a given type (*.wma) and move them to another directory already created.

It would seem that the command line's the best place to do this, but my command line fu isn't nearly well-developed enough to know where to begin. I've done a fair bit of Googling and searching of the forum, but it's kind of like finding a needle in a haystack.

Any help is much obliged.
JM

---

### Post by D3ath on 2009-12-17
```
find <start directory> -iname "<all my files type>" -exec cp {} <target_dir> \;
```

---

### Post by mailman1175 on 2009-12-17
> **D3ath said:**
> ```
find <start directory> -iname **"<all my files type>"** -exec cp {} <target_dir> \;
```

Does the bolded section above look like ".wma", "wma", or "*.wma"?

---

### Post by D3ath on 2009-12-17
> **mailman1175 said:**
> Does the bolded section above look like ".wma", "wma", or "*.wma"?

Yes what ever you would be looking to copy over... In your case "*wma". Instead you might wanna switch out the "cp" with "mv" if you are looking to totally move the file out of there folders.

---

### Post by Barriehie on 2009-12-17
NM!

Might want to change the cp (copy) to mv (move) to select the desired operation, this is the part after -exec.

Barrie

---

### Post by D3ath on 2009-12-17
> **Barriehie said:**
> NM!

Might want to change the cp (copy) to mv (move) to select the desired operation, this is the part after -exec.

Barrie

Yea I just noticed that in my last post I tried to specify that one. lol

---

### Post by mailman1175 on 2009-12-17
Thanks guys! Worked like a charm!

---

### Post by Barriehie on 2009-12-17
> **mailman1175 said:**
> Thanks guys! Worked like a charm!

Find is a really cool command; it can make mgmt so much easier!

Barrie

---

### Post by mailman1175 on 2009-12-17
> **Barriehie said:**
> Find is a really cool command; it can make mgmt so much easier!

Barrie

I figured I'd have to use find, I just didn't know what to put with it. So I understand the syntax a little better, does the -exec variable allow execution of mv when the find string is found to be true?

---

### Post by Barriehie on 2009-12-17
> **mailman1175 said:**
> I figured I'd have to use find, I just didn't know what to put with it. So I understand the syntax a little better, does the -exec variable allow execution of mv when the find string is found to be true?

Yes, the matched filenames are acted upon, from the starting dir, by find building a command string.  -execdir does pretty much the same thing except it executes the command from the dir where the file is found.

When I first discovered find, via the forum!, I would test it by using ls for the command and then pipe to a file to peruse the affect of my command use, i.e. *find /home/barrie -iname *.tgz -mtime +31 -exec ls {} \; > /home/barrie/Desktop/filez*.  This would find all files in my home dir ending with .tgz , case insensitive, that were older than 31 days and list them on the desktop in a file named *filez*.

Barrie

---

