---
title: "Defining custom commands in .bashrc"
date: 2011-04-26
forum: General Help
---

### Post by salmontres on 2011-04-26
Hi guys,

I just learned about the 'alias' command and have been putting it to good use! However, I'd like to know if there is a way to define commands in the .bashrc or .bash_profile. For instance, I want to be able to type 'work' in a terminal and set up an interactive work environment on my universities cluster. (This is done with the command 'qsub -I -X'.) I tried the following in my .bashrc file:

alias work ='qsub -I -X'

But, of course this failed, as I don't have a command work already defined. How do I go about doing this? Also, I can't assign 'qsub' an alias, since it's used with different options quite extensively.

---

### Post by idoitprone on 2011-04-26
why is there a space between work and =

it should be alias work='qsub -I -X'

---

### Post by salmontres on 2011-04-26
Wow, that was silly. Removing the space did it for me.

Thanks idoitprone!

---

### Post by matt_symes on 2011-04-26
Hi

> **idoitprone said:**
> why is there a space between work and =

it should be alias work='qsub -I -X'

Spot on. Remove the space between work and = or bash will try to run two commands. This one **alias work** and then this one **alias ='qsub -I -X'**. Not what you want. Bash is pedantic about spaces.

> Also, I can't assign 'qsub' an alias, since it's used with different options quite extensively.

Cant you set up multiple alias for the different options for qsub ?

Something like *alias wix='qsub -I -X'* for instance.

BTW: From .bashrc

```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

If you create a file called .bash_aliases in your home directory and put your aliases in there, you can keep them all in one easy to find place.

Kind regards

---

### Post by salmontres on 2011-04-26
Hi Matt,

I really like that idea of creating a file for my aliases specifically. Can I create other .bash files to further customize my work environment? For instance, can I create a '.bash_pgi' to auto set up my environment to use PGI compilers?

---

### Post by matt_symes on 2011-04-27
Hi

> **salmontres said:**
> Hi Matt,

I really like that idea of creating a file for my aliases specifically. 

Remember to make it executable first. I should have mentioned that.

```
chmod 777 .bash_aliases
```

> Can I create other .bash files to further customize my work environment? For instance, can I create a '.bash_pgi' to auto set up my environment to use PGI compilers?

Yes you can. You will have to add something similar to what is in .bashrc to source your other files though, like the code to source the .bash_aliases file. And remember to make them executable.

Kind regards

---

