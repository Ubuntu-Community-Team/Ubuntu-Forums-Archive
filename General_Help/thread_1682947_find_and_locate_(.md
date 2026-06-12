---
title: "find and locate :("
date: 2011-02-06
forum: General Help
---

### Post by eidasadie on 2011-02-06
so ive been having some trouble with find and locate and theres got to be a way to find files efficiently in ubuntu im probs doing it wrong. 

the common scenario: i want to find a file say..my 310 to yuma movie.. but i forget what the exact file name is called. it must be something with yuma in the name and i know somewhere buried in my external affectionately known as /media.

```
find /media -iname "yuma"
```nothing

```
find /media -iname "*.avi
```whoa tmi

locate doesnt seem to be any better

can yall help me find my files if i dont remember exactly what their called

thanks

---

### Post by TeoBigusGeekus on 2011-02-06
Try
```
find /media -iname *yuma* 2>/dev/null
```

---

### Post by tredegar on 2011-02-06
**locate** is good for finding partial matches, and is much faster than **find**.

But the database needs to be updated.

Normally this happens daily as a cron job.

But if you have a recent file you need to locate, or it is on a recently mounted drive, then you'll need to update the **locate** database first:
```
sudo updatedb
```
then **locate yuma | grep /media**

That will just list the files **locate** finds with **yuma** in the name  and the path to the file contains **/media** (which is where you are interested in looking).

---

### Post by Vaphell on 2011-02-06
do you have that external drive mounted when you run find command?

---

### Post by asmoore82 on 2011-02-06
`locate` is extremely fast because it uses a pre-defined index.
But, if your external media is not connected during the indexing,
`locate` won't be able to find anything.

`find` is slower but does an active search with up-to-the-second results.

Everyone makes the same mistake with `find` at first, I did exactly the same too :D.
A find by extension is like 2nd nature: "*.avi"
But, for a full text search by filename, we try no wildcards at all: "yuma"
What we really need is 2 wildcards: "*yuma*"
```
find /media -iname "*yuma*"
```

---

### Post by gmargo on 2011-02-06
Since external drives tend to be quite slow, it makes sense to only do the search once.  Cache the result and grep on that.
```

$ find . -print > List.txt

```Now grep for what you think it might be called
```

$ grep -i yuma List.txt | grep 310

```Now next week when you're looking for Batman, just grep List.txt again. You only need to update List.txt when you've been adding or moving things around.

---

