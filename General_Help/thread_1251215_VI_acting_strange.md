---
title: "VI acting strange"
date: 2009-08-27
forum: General Help
---

### Post by neoform on 2009-08-27
Hi, I just installed Ubuntu Server 8 and found vi to be acting strangely (compared to vi on Fedora, CentOS and OSX).

When I use the 'a' command to enter text, pressing the arrow keys results in "C", "D", "B" and "A" to get entered. This makes editing almost impossible..

Am I doing something wrong here?

---

### Post by jerome1232 on 2009-08-27
vi does this for me too, but vim doesn't, even though on my system they seem to both call vim anyways.

That is wierd.

---

### Post by jonobr on 2009-08-27
+1 and interesting,

I tested this on Debian and Ubuntu and got the result you mention.

When testing it, it did remind me that I had seen this before when editing files, but I did not pay it much attention.

When I just invoke vi i get the vim frontpage which I think is what was referred to below.

---

### Post by armageddon08 on 2009-08-27
Install vim. That should work.

---

### Post by neoform on 2009-08-27
>Install vim. That should work.

Yeah, I posted on superuser.com and someone pointed out that i needed to do: apt-get install vim

That fixed it. :)

---

### Post by Gen2ly on 2009-08-27
Odd though that vi is broke, vi isn't that much different than vim.

---

### Post by Iowan on 2009-09-15
Maybe that's one of the m-provements? :-k

---

