---
title: "get script to run in alt-f2"
date: 2011-01-07
forum: General Help
---

### Post by rustysail on 2011-01-07
Hey,

I have a few bash script in ~/.bin

I want to be able to run them both the command line and from if I use the alt-f2 command prompt.  I happen to use gmrun.

I know I can do this by hardlinking each file to /usr/local/bin but I would rather be able to just put my scripts in ~/.bin

Any ideas.  Thanks

---

### Post by efflandt on 2011-01-07
If you put your scripts in **~/bin** (without the dot) that will automatically be in your PATH the next time you login.  So you just have the directory name slightly wrong.

```
efflandt@natty-ssd:~$ echo $PATH
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by ajgreeny on 2011-01-07
You can do it from Alt+F2 run dialog by using the command in the box ```
bash -c "/path/to/file.sh"
``` This works wherever the script is in your home, but I'm not sure what happens if the script will only run with root privileges.

---

