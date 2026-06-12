---
title: "display just the current directory in terminal:"
date: 2010-07-14
forum: General Help
---

### Post by magnetpest2k7 on 2010-07-14
Hello all,

when we navigate into directories withing directories the terminal displays the entire path right from the root. Now how to make it just show the current directory I am working in? 

For example

vineeth@vineeth-laptop:~/Desktop/linux_programming/python_programming/project_duplicate_zip_files$ 

as you can see that I am in the current project_duplicate_zip_files directory but it displays right from the root. how to just make it something like below:

vineeth@vineeth-laptop:/project_duplicate_zip_files$

---

### Post by goltoof on 2010-07-14
```
pwd
```enough for me :)

---

### Post by CharlesA on 2010-07-15
Open ~/.bashrc and find the line that looks like this:

```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    [COLOR="Red"]PS1='${debian_chroot:+($debian_chroot)}\u@\h:\**w**\$ '[/COLOR]
fi

```



To: ```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    [COLOR="Blue"]PS1='${debian_chroot:+($debian_chroot)}\u@\h:\**W**\$ '[/COLOR]
fi

```

Save and exit and you will be good to go. :-)

---

