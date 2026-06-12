---
title: "AWK to replace line in a file, with contents of another file"
date: 2010-06-21
forum: General Help
---

### Post by tzjin anthony ks on 2010-06-21
Hi, all.

I have 2 files, say A and B.

There is one line in file A, which matches a pattern, and I'd like to replace it with the contents of file B.

Currently, the sequence I'm following is:
1. Finding the offending line number in file A using awk
2. head A upto that line > temp
3. cat B >> temp
4. tail A from that line >> temp

Just wondering if someone knows of an easier way.

Cheers.

Tzjin.

---

### Post by DaithiF on 2010-06-21
Hi,
You could do in sed this way:
```
sed '/pattern/{r filename
;d}' somefile

```
(thats a newline after filename -- it has to be split over 2 lines as the sed 'r' (read file) command expects the filename parameter to continue up until the next newline.

---

### Post by tzjin anthony ks on 2010-06-21
works great, except for one thing: how can i specify a variable instead of filename?

it's probably a combination of quotes, but i don't seem to be able to get it right.

thanks.

tzjin.

---

### Post by tzjin anthony ks on 2010-06-21
nope - nevermind - got it. double quotes instead of single quotes.

---

