---
title: "C sharp mono file not found error"
date: 2011-09-28
forum: General Help
---

### Post by mao3 on 2011-09-28
Hey,

So, I'm using the following line in my C# code ```
string contents = System.IO.File.ReadAllText(@"/text");
``` and the file, text, is definitely in my home folder (so is my code), but when I try to run it, it tells me the file could not be found.  Anybody here also use mono and know how to make this work in Ubuntu?

Any help would be appreciated.  Also, if you know of any other relevant forums to ask this question in, just let me know and I'll ask it there also.

---

### Post by directhex on 2011-09-30
Do you want this to work relative to the current directory (i.e. ./text) or your home directory (~/text)?

---

### Post by mao3 on 2011-09-30
Thank you for replying.  Using "./text" worked.  I had already tried using "~/text" and it would actually try to read the file in folder home/username/username which doesn't exist.  Anyway, awesome, my problem is solved.

---

