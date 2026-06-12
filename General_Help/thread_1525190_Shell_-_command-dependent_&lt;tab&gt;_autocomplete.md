---
title: "Shell - command-dependent &lt;tab&gt; autocomplete, can get in linux?"
date: 2010-07-06
forum: General Help
---

### Post by Zorgoth on 2010-07-06
I was using windows recently and noticed that in their command line, the autocomplete is in some ways a little more intelligent (although based on my short experience ours is more robust); for example, if you have a directory named blah and a file name bl, in Linux "cd bl <tab>" will result in "cd bl" while in Windows I get "cd blah" because it recognizes that blah and not bl is the appropriate argument to cd.  Similarly unrar will target rar files first.

I am not saying Windows command line is better; Windows command line is in general a piece of junk.  But is it possible to get this particular feature of the Windows command line in Linux?

---

### Post by sisco311 on 2010-07-06
It works for me. Is bash-completion installed and enabled on your system?
```
sudo apt-get install bash-completion
```

To enabale it edit /etc/bash.bashrc:
```
gksu gedit /etc/bash.bashrc
```
and comment out the relevant lines:
```

...
# enable bash completion in interactive shells
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
...
```

Start a new shell or source /etc/bash_completion:
```
. /etc/bash_completion
```

---

### Post by Zorgoth on 2010-07-06
Thank you, that worked great!

---

