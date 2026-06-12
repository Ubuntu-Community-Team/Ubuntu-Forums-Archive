---
title: "Tab space in gnome-terminal"
date: 2009-08-14
forum: General Help
---

### Post by oakdeveloper on 2009-08-14
Hi,

I want to change the tab spacing in gnome-terminal from 8 to 4. Where do I change this?
Please help me..

Thanks,
Babu

---

### Post by DaithiF on 2009-08-14
hmm, i don't think gnome-terminal has a setting for tabwidth.  Whatever applications you are running **within** gnome-terminal may, though.  What application(s) are you running where you want to change the tabspacing?  

For example, in vim you would do:
:set tabstop=4

---

### Post by oakdeveloper on 2009-08-14
Yes! I have done that in Vim. But I want the tab space to be 4 when editing using the "cat > filename" command.

---

### Post by DaithiF on 2009-08-15
Hi,
cat doesn't allow you to configure tabspacing.  You could use the expand command instead.
```
expand -t 4 somefile
```

```
man expand
``` for more info

---

