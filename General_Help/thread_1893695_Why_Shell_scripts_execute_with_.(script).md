---
title: "Why Shell scripts execute with ./(script)"
date: 2011-12-10
forum: General Help
---

### Post by blakeljb on 2011-12-10
Used to run unix scripts and just getting back into it on linux but can't figure out why all the scripts I've done need to have a ./"script name" instead of just "script name" when starting the script from the directory where the script is. Am I doing something wrong, have something set up wrong or ?????
 
Thanks

---

### Post by mutley89 on 2011-12-10
Bash uses the PATH variable to find the directories to search in for what program to run.  This doesn't include the current directory, therefore you need to explicitly specify it.

---

### Post by killermist on 2011-12-10
Alternately, in .bashrc, you can add this line near the end:
```
PATH=.:"${PATH}"
```
That will include "." in your path so whatever directory you're in is in the path (also as the first path hit, so a program in the working directory COULD override something in /bin or /usr/bin while you're there).

---

### Post by Dangertux on 2011-12-11
Another alternative would be creating a link in your /usr/local/bin as such

```

sudo ln -s script /usr/local/bin/script

```

Hope this helps.

---

### Post by jwbrase on 2011-12-11
> **blakeljb said:**
> Used to run unix scripts and just getting back into it on linux but can't figure out why all the scripts I've done need to have a ./"script name" instead of just "script name" when starting the script from the directory where the script is. Am I doing something wrong, have something set up wrong or ?????
 
Thanks

As has been said, it can be changed by modifying .bashrc (or the appropriate configuration file for whatever shell you're using, I use zsh instead of bash, for instance) to add the current directory to your $PATH variable.

The reason ./ is not included by default in your path is that there are some potential security issues. Most of these can be solved by placing ./ at the end of your path, rather than the beginning, however, and it might be debated how much they apply to personal desktops (as opposed to multiuser systems). 

> **killermist said:**
> Alternately, in .bashrc, you can add this line near the end:
```
PATH=.:"${PATH}"
```
That will include "." in your path so whatever directory you're in is in the path (also as the first path hit, so a program in the working directory COULD override something in /bin or /usr/bin while you're there).

It's better to place ./ at the end of your path with

```
PATH="$PATH:."
```

to avoid some of the potential security issues that come from having it at the beginning of your path (such as the issue with a program in the working directory being executed instead of a system file in /bin or /usr/bin).

---

### Post by kamaji792 on 2011-12-11
Thanks for that **jwbrase** I always wondered why it was considered a security issue.

I usually create a personal bin directory:
```
mkdir ~/bin
```

and add it to the path in the **.bashrc** file:
```
PATH=$HOME/bin:$PATH
```

Then put any scripts I run regularly in that directory.

atb k

---

