---
title: "bash backquotes join output"
date: 2011-02-07
forum: General Help
---

### Post by nnn= on 2011-02-07
I was trying to redirect command output to a variable and realized that all the lines were joined. I tested this additionally with an example:```
echo "The contents of this directory are " `ls -l` > dir.txt
``` and all the lines were joined in the resulting file. What can I do to preserve separate lines?

---

### Post by slooksterpsv on 2011-02-07
```

echo "The contents of this directory are: $(ls -l)" > temp.txtx

```

That's what I did. I think that commands run in ` doesn't preserve formatting. Also with echo, I can't do \n so I'd do:
```

printf "The contents of this directory are:\n$(ls -l)" > temp.txt

```

---

### Post by nnn= on 2011-02-07
Thanks, that helped me very much.

---

