---
title: "Remove frm $PATH"
date: 2010-04-18
forum: General Help
---

### Post by akssps011 on 2010-04-18
I have set a PATH as
export PATH=$PATH:/usr/exportabc/bin

How can I remove this from $PATH in bash.

echo $PATH gives

```


/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/exportabc/bin:/usr/exportefg/bin:/usr/exportabc/bin/marble


```

---

### Post by kerry_s on 2010-04-18
have you tried "export PATH=$PATH"

---

### Post by akssps011 on 2010-04-18
> **kerry_s said:**
> have you tried "export PATH=$PATH"

But wouldn't that remove everything from $PATH ? ( wouldn't it do some harm ?)
That's wy I wanted to remove only the path I added.

Edit: export PATH=$PATH Doesn't work

---

### Post by john newbuntu on 2010-04-18
I am assuming that you want to remove ":/usr/exportabc/bin" from $PATH.  Use something like:

PATH=$(echo $PATH | sed -e 's#:/usr/exportabc/bin##')

---

