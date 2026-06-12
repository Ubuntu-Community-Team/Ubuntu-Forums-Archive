---
title: "need ownership?"
date: 2010-12-23
forum: General Help
---

### Post by Bruce21 on 2010-12-23
hello everybody i just installed ubunto about a month or so ago and i installed java 6 jdk so i can make a few blackberry apps and when i try to run the program it just gives me the code. so i tried to edit the permissions so it will execute. but when i get there it tells me "you are not the owner so you can not change theses premissions" the owner is "root" i have a screen shot if you need it. so my question to you is how do i own this thing or become the "root"  [U]

[IMG]http://img840.imageshack.us/i/helpme.png/[/IMG]
[/U]

---

### Post by AlphaLexman on 2010-12-23
You should save the files in your 'home' directory, [/home/yourusername/] (~/)
and then you can use 'chmod' (change modifications) to make the file executable (+x)
```
chmod +x ~/executablefilename
```

---

### Post by Bruce21 on 2010-12-23
thank you, that fixed it.

---

