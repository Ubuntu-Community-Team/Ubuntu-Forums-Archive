---
title: "Unziping RAR files"
date: 2009-07-21
forum: General Help
---

### Post by babujbf on 2009-07-21
Hello..

I noticed unziping rar files that have passwords my computer doesn't ask me for the password and sometimes they come out corrupted.

What do I need to do to put in the password?

Thanks

---

### Post by Tibuda on 2009-07-21
RAR is a really strange format. If I'm not wrong, the password is only asked after the whole archive is uncompressed. This is why it is not hard to crack such files. Well, if the file is corrupt, it won't finish the uncompressing to ask you for the password.

I don't think it will work, but you can also try to extract the file using the terminal, passing the password as an argument:
```
unrar filename -p**password**
```

---

### Post by babujbf on 2009-07-21
I don't know in windows it asks you for the password before unziping..

---

