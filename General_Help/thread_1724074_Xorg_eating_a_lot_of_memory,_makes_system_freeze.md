---
title: "Xorg eating a lot of memory, makes system freeze"
date: 2011-04-07
forum: General Help
---

### Post by frostwyrm333 on 2011-04-07
Xorg takes 700+ mbs of ram, then in matter of hours it fills the swap and then system basically stops responding or whatever. And because its constantly allocating, it degrades perforamce horribly.

Ubuntu 10.10
Xorg 1:7.5+6ubuntu3

Interesting thing is I never had this problem before, recently one of my ram modules broke (2+2 GB) and now I have only one, but it still doesnt explain the memory overuse. Windows 7 works perfectly fine.

---

### Post by Buntumatic on 2011-04-07
That's called memory leak. Some app is going berserk, use **top** to find out the culprit.

---

### Post by frostwyrm333 on 2011-04-07
Well, that exactly what I did, it climbs towards something of a 30%, then it stops because there is nothing left and then it starts to clutter swap and destroy peformance of everything else.

---

### Post by Buntumatic on 2011-04-08
> **frostwyrm333 said:**
> Well, that exactly what I did, it climbs towards something of a 30%, then it stops because there is nothing left and then it starts to clutter swap and destroy peformance of everything else.
It? What is it? What is the name of process?

---

### Post by frostwyrm333 on 2011-04-08
Well, as I said:

[http://img706.imageshack.us/i/xorg.png/](http://img706.imageshack.us/i/xorg.png/)

---

### Post by Buntumatic on 2011-04-08
Does it happen if Firefox is not running? 

My first suspect would be some Firefox add-on or conflicting add-ons maybe.

---

### Post by frostwyrm333 on 2011-04-09
I wasnt doing anything out of the ordinary, anything could probably cause it, but if I close everything, the Xorg memory wont be freed. I need to logout entirely.

I think it has something to do with that ram I took out, since thats when the problem started.

---

### Post by Buntumatic on 2011-04-09
Xorg is the parent process, you are here asking for help, why can't you answer a simple question.

[B]Does it happen if Firefox is not running?
[/B]

---

