---
title: "Zsh shell and apt-get"
date: 2010-05-23
forum: General Help
---

### Post by kempy1000 on 2010-05-23
Hi

I have just started using the zsh shell to see what its like and so far I like it. 

However one anoyance is that if I type:
```

sudo apt-get install plymouth-*

```
I get package not found.

If I do the same in a bash shell I get the option to install the the packages matching the wildcard.

Why does zsh shell do this? and is it possible to fix it?

Thanks
Chris

---

### Post by gmargo on 2010-05-23
You should have copied your error message.
You probably got "zsh: no matches found: plymouth-*" for an error message.

Use single or double quotes to prevent zsh from attempting to interpret the "*".  You should also do that for bash.  You have discovered a difference between the two shells default behavior when an unquoted regex has no matches.

```

sudo apt-get install "plymouth-*"

```

---

