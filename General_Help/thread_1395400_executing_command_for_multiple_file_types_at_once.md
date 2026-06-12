---
title: "executing command for multiple file types at once"
date: 2010-01-31
forum: General Help
---

### Post by tolanri on 2010-01-31
Hello, I'm trying to write simple command that would unrar from multiple filetypes in one command (.rar,partXX.rar, and .001), I tried this:
[B]
unrar e *.{part01.rar,r00,001}[/B]

however this command doesn't work properly

Any ideas how to do this? Thank you.

PS: I know it could be done easily using bash scripts, but I need one single command for this, if possible.

---

### Post by t4thfavor on 2010-01-31
Try 
```

unrar -e *.${part01.rar,r00,001}

```

That should work, but I have no way to test it.

---

### Post by tolanri on 2010-01-31
Gives

-bash: *.${part01.rar,r00,001}: bad substitution

---

### Post by tolanri on 2010-02-01
bump.

Noone have any idea?

---

### Post by HiImTye on 2010-02-01
how about
```
rar e part01.*
```or maybe
```
 unrar e part01.*${rar,r00,r001}
```

---

### Post by tolanri on 2010-02-01
> **HiImTye said:**
> how about
```
rar e part01.*
```or maybe
```
 unrar e part01.*${rar,r00,r001}
```

Thanks but it wouldn't do what I wanted. I worked around it with this command:

```
 find $1 \( -name "*.r00" -o -name "*.001" -o -name "*.part01.rar" \) -exec unrar e {} $1 \;
```

Works like a charm. Anyway, thank you for your advices.

---

