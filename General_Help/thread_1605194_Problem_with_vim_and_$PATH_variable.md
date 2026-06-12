---
title: "Problem with vim and $PATH variable"
date: 2010-10-25
forum: General Help
---

### Post by sbarmeier on 2010-10-25
Hello,  I have a problem with vim. I am trying to compile a TeX (actually ConTeXt) document with vim. I have installed the latex-suite for vim. When I try to run  :!context --nonstopmode %  vim tells me that /bin/bash doesn't contain context, which is correct. However, my $PATH variable contains all directories, including the directory containing the context script. (Oddly enough, my $PATH variable doesn't include /bin/bash explicitly.)  The terminal executes the command without any problem, of course, since the terminal looks at the $PATH variable. vim doesn't seem to use the $PATH variable. How can I tell vim to consult the paths in the $PATH variable?  Many thanks, Sev

---

### Post by DaithiF on 2010-10-25
$PATH should be a list of directories not files, so /bin/bash should not be in there.  VIM does inherit whatever $PATH is set in your environment.  If you do:
```
:echo $PATH

```in vim, what is reported?

---

