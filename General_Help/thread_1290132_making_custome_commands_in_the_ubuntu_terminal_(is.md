---
title: "making custome commands in the ubuntu terminal (is it possible?)"
date: 2009-10-13
forum: General Help
---

### Post by FromDutch on 2009-10-13
Hi everyone, (my apologies if this isn’t the right sub-forum)



I’ve recently started working with Linux and I use ubuntu on my home desktop. I was wondering if it’s possible to write custom commands for the terminal.
I manly use putty (I never really touch gnome) * 

So whenever I try to search/install a package I type “sudo aptitude search/install [package name]” 

Is it possible to simplify this by wrighting a script? 

So when I type “scoobydoo [package name]” it automatically searches/installs the packages am looking for?
 


Thanks in advance~ a general linux nublet :)

---

### Post by wojox on 2009-10-13
sure their called Shell aliases:[https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux)

---

### Post by zer0x on 2009-10-13
Hi,

Yes there is :D

'alias' (man 1 bash)

```

       alias [-p] [name[=value] ...]
              Alias with no arguments or with the -p option prints the list of
              aliases in the form alias name=value on standard  output.   When
              arguments  are supplied, an alias is defined for each name whose
              value is given.  A trailing space in  value causes the next word
              to be checked for alias substitution when the alias is expanded.
              For each name in the argument list for which no  value  is  sup&#8208;
              plied,  the  name  and  value  of  the  alias is printed.  Alias
              returns true unless a name is given for which no alias has  been
              defined.
```


HTH

zer0x

---

### Post by justleen on 2009-10-13
I've added the following to ~/.bashrc to achive that..```

alias aptinstall='sudo apt-get -y install'
alias aptsearch='sudo apt-cache search'
alias aptdel='sudo apt-get remove'


```

you could add more if you want to..

---

### Post by FromDutch on 2009-10-13
wow, thanks for the fast replys guys. 

ill test them out right now :)

---

### Post by diafanos on 2009-10-13
> **justleen said:**
> I've added the following to ~/.bashrc to achive that..```

alias aptinstall='sudo apt-get -y install'
alias aptsearch='sudo apt-cache search'
alias aptdel='sudo apt-get remove'


```

you could add more if you want to..

what it's annoying with these aliases is that they don't support tab completion, so they are not too handful when you don't know the exact name of a package.

Does anyone know any workaround?

---

### Post by justleen on 2009-10-13
> **diafanos said:**
> what it's annoying with these aliases is that they don't support tab completion, so they are not too handful when you don't know the exact name of a package.

Does anyone know any workaround?

How do you mean, they dont support tab-completion? They do..
apti<TAB> will give me "aptinstall"
Yes, they dont complete the package name, but neither will apt-get install <tab> give you the full package list! 
Thats is why there is such a thing as apt-cache search!

---

### Post by diafanos on 2009-10-13
> **justleen said:**
> Yes, they dont complete the package name, but neither will apt-get install <tab> give you the full package list! 


if you do apt-get install gnome- <tab>, then if there is just one available package which name starts with gnome- it will complete it.
If there are more then one packages starting with gnome- then if you press <tab> twice, you get the full list.

Try it ;)

---

### Post by justleen on 2009-10-13
> **diafanos said:**
> if you do apt-get install gnome- <tab>, then if there is just one available package which name starts with gnome- it will complete it.
If there are more then one packages starting with gnome- then if you press <tab> twice, you get the full list.

Try it ;)

I stand utterly corrected.. *blush*

Im looking into /etc/bash_completion now, see if thats hackable to get alliases doing the same thing.

---

### Post by diafanos on 2009-10-13
Good luck...

I'm in front of a windows XP monitor...unable to help you :(

---

### Post by justleen on 2009-10-13
LoL, thnx.. But im not the OP :)

---

