---
title: "Command Question"
date: 2010-04-14
forum: General Help
---

### Post by mjc4043 on 2010-04-14
Hey all,

     I just ran gksudo nautilus from the alt-f2 window in ubuntu 9.10... however the first time I tried this I mistyped the word nautilus - anyway I entered my password and nothing happened.  I was just wondering if this command mistyped performed some other action such as creating a directory named [mistyped nautilus].  

-Michael

---

### Post by doas777 on 2010-04-14
not unless your mispelling of 'nautilus' was somthing like 'mkdir'.
gksu and sudo prompt for the password before checking to see if the command exists (what if the command is in a folder that has read and execute only for root?), so it will always prompt you, even if the following command is gibberish. 

no it prolly didn't execute anything, unless you misspell in a most unfortunate manner.
just be careful. ubuntu can be less forgiving of spelling mistakes than other OSs.

---

### Post by mjc4043 on 2010-04-14
Thanks for the quick response, the typo was not so unfortunate as to reformat my hard drive or equal something like mkdir.  It was closer to "gksudo nautalis",  who would have thought an english major could have such terrible spelling skills.  Anyway, I am learning. 

-Michael

---

### Post by 98cwitr on 2010-04-14
nah dont sweat it, you're fine.

---

