---
title: "How much RAM am I actually using?"
date: 2006-04-04
forum: General Help
---

### Post by theycallmemorty on 2006-04-04
Does anyone know something I can run from the command line that will tell me how much memory my system is currently using?

I've used 'free -o' and 'top' but those don't count correctly because they include shared modules. (According to them I'm using up 690 of 768 MB when I start up in the morning :-k)

---

### Post by Monster_user on 2006-04-04
Just type 'free', without the -o.

Notice what it says on the second line (buffers/cache). That will list what is actually being used by running programs, and is not just cached.

**Note:*** I do not use Breezy, but rather Dapper Drake, and other distros.*

---

### Post by GeneralZod on 2006-04-04
This is actually a pretty tricky question.  This link covers quite a bit of the ins and outs of process memory usage, including the difficulties caused by shared libraries:

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

---

### Post by mcduck on 2006-04-04
I recommend 'free -m' to get more easy-to-read results. This gives the numbers in MB's instead of KB's :)

The important line is the '-/+ buffers/cache', as that shows how much there is memory available for programs to use (the 'used' in first line will most of the time be almost as much as you have RAM available, because free memory is used as cache)

---

