---
title: "grep not picking up/finding my search string"
date: 2011-06-08
forum: General Help
---

### Post by helloise on 2011-06-08
i did a normal grep -r "No file chosen" *
but i get: 

grep: phoenix/web/sfProtoculousPlugin: No such file or directory


i dont understand? i know that string is somewhere...but cannot find it so i thought i'll grep it but then i get that message.

can some-one please help?
thank you

---

### Post by seawolf167 on 2011-06-08
Maybe?

```
grep -r -i "No file chosen" .
```

---

### Post by helloise on 2011-06-08
nope is still get: grep: phoenix/web/sfProtoculousPlugin: No such file or directory

---

### Post by tapi0n on 2011-06-08
perhaps it's in a folder above your current location?

---

### Post by helloise on 2011-06-08
nope...i am in the correct directory :) the problem lies else where but dont know where if i grep -r 'chosen ' *  i get output but as soon as ido a grep on: "file chosen" i get that strange message

---

### Post by Rubi1200 on 2011-06-08
Perhaps drop the recursive switch and just use the i option?

---

### Post by helloise on 2011-06-08
i see now i have a simlink:

sfProtoculousPlugin -> ../../../../../../../usr/share/php/symfony/plugins/sfProtoculousPlugin/web
 that does NOT exist that is why i get phoenix/web/sfProtoculousPlugin: No such file or directory

but why it does not find my string i dont know can it be something to do with this plugin?

---

