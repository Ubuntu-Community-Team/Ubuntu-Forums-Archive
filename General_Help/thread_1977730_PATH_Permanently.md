---
title: "PATH Permanently"
date: 2012-05-10
forum: General Help
---

### Post by felipeabrao on 2012-05-10
Hello,

I am using the command

```
export PATH=$PATH:/usr/local/texlive/2011/bin/i386-linux

```

but if I close the terminal and open it again, the shortcut becomes inactive. Do you know how to let it permanent?

Thank you in advance,

Felipe

---

### Post by sudodus on 2012-05-10
> **felipeabrao said:**
> Hello,

I am using the command

```
export PATH=$PATH:/usr/local/texlive/2011/bin/i386-linux

```

but if I close the terminal and open it again, the shortcut becomes inactive. Do you know how to let it permanent?

Thank you in advance,

Felipe
Append the command line to the file
```
~/.bashrc
```

---

### Post by felipeabrao on 2012-05-11
Thank you very much, sudodus,

the problem was solved following your tip!

Felipe

---

