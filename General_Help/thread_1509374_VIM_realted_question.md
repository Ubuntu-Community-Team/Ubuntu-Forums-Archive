---
title: "VIM realted question"
date: 2010-06-14
forum: General Help
---

### Post by NikitaUtiu on 2010-06-14
I write sources in VIM and i use the following settings:
set tabstop=4
set expandtab
set autoindent

And I have got some questions.

1:Is there any way I could do, so when I press backspace to delete an entire tab instead of individual spaces ?

2:Is there anything to do to delete a tab if I insert a closed curly bracket.
e.g.
```
int main (void) {
} // <- and this one gets perfectly aligned  
```

---

### Post by denarced on 2010-06-20
In VIM, type:
```

:h mapping

```

---

### Post by denarced on 2010-06-20
> **NikitaUtiu said:**
> 
1:Is there any way I could do, so when I press backspace to delete an entire tab instead of individual spaces ?

It does delete the entire tab if there indeed is a tab.
Check out in vim:
```

:h expandtab

```

---

