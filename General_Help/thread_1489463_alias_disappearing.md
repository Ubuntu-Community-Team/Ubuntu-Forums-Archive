---
title: "alias disappearing"
date: 2010-05-21
forum: General Help
---

### Post by shai3421 on 2010-05-21
I've inserted an alias in bash via the
"alias NAME=VALUE" command and it worked fine.

But after awhile (there's been a restart also) I tried to use the alias again and it didn't work, upon checking the alias list I saw that it was no longer defined.

Why did it disappear and how can I make it permanent?

The alias, in case it is relevant to someone, was:
alias cpulimit="sudo cpulimit --exec=dynamips --limit=70"

Anyone?

---

### Post by DaithiF on 2010-05-21
Hi, 
where did you define it?  if on the command line then the alias only lasts for the duration of that shell.  To make it permanent, add it to your .bashrc file

---

### Post by shai3421 on 2010-05-21
Yeah it was on the command line, and I tried to change the .bashrc file but there were 4 files ending with .bashrc so I gave it up after not finding the alias section in some of them.

I figured it would be enough to use the alias command to configure it.

Now I will take another look at those .bashrc files.

Thanks.

---

### Post by Blackbird_13 on 2010-05-21
Another option is to create all your aliases in a separate file called .bash_aliases. You'll still need to find the correct .bashrc file in order to uncomment the section as follows:

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

---

### Post by shai3421 on 2010-05-21
Okay, I got it to work. :)

Apparently it requires a log out.

---

### Post by pebo on 2010-05-21
> **shai3421 said:**
> Okay, I got it to work. :)

Apparently it requires a log out.You can ```
source ~/.bashrc

```as well to save logging out ;)

---

