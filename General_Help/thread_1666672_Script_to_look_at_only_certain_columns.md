---
title: "Script to look at only certain columns"
date: 2011-01-14
forum: General Help
---

### Post by SuaSwe on 2011-01-14
Hi all,

Let's see if I can explain this in a comprehensible fashion!

Basically, I have a file that looks a little something like this:

```

abcd       efgh       ijkl       mnop
qrst       uvwx
yzab       cdef       ghij
klmn       opqr       stuv       xyza
bcde       fghi       
nopq       rstu

```

What I want to do is display *all* columns of the lines that have content listed in columns 3 and 4, e.g.:

```

abcd       efgh       ijkl       mnop
yzab       cdef       ghij
klmn       opqr       stuv       xyza

```

I unfortunately cannot grep for a certain string of numbers/letters as it varies in each column, and can't awk-print just $3 and $4 as I also need the content in $1 and $2 for the relevant lines.

Can anyone suggest anything? It's to be added into a larger script so the simplier the better. :)

---

### Post by DaithiF on 2011-01-14
```
awk '{ if($3) print $0 }'  /path/to/somefile
```

---

### Post by SuaSwe on 2011-01-14
Delay on forum caused multiple posts - please ignore!

---

### Post by SuaSwe on 2011-01-14
Delay on forum caused multiple posts - please ignore!

---

### Post by SuaSwe on 2011-01-14
Delay on forum caused multiple posts - please ignore!

---

### Post by SuaSwe on 2011-01-14
Delay on forum caused multiple posts - please ignore!

---

### Post by SuaSwe on 2011-01-14
That is a beauty - I knew awk (and the forums :D ) would come through! It's a big script so don't be surprised if I come running back here for further advice. ;)

Hmm... On a side note, is there a problem with the forums? It's very slow in loading and I've tried to post this about five times now, and each time it tells me I have to wait 20 seconds between posts, even after waiting a couple of minutes.

(Also hence the reason for my forum spamming - sorry about that! :D)

---

### Post by hawkmage on 2011-01-14
Not that this approach is any better but I would have don this:
```
awk 'NF>2 {print $0}'  /path/to/somefile
```

---

### Post by SuaSwe on 2011-01-14
Thanks for that as well! Either one of those can be used in my case, so will play around. :)

---

