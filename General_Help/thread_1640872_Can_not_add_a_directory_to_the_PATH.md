---
title: "Can not add a directory to the PATH"
date: 2010-12-08
forum: General Help
---

### Post by jmvidalvia on 2010-12-08
Hi!
After trying to add a directory to the PATH, I get the message that the folder doesn't exist.
Is there anything wrong I am doing?
Thanks a lot

```
jm@jm-ThinkPad-X200s:/usr/jm_scripts$ export PATH=$PATH:/usr/scripts
jm@jm-ThinkPad-X200s:/usr/jm_scripts$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/scripts:/usr/scripts: No existe el archivo o directorio

```

---

### Post by nothingspecial on 2010-12-08
That`s because your directory is /usr/jm_scripts and not /usr/scripts

---

### Post by jmvidalvia on 2010-12-08
> **nothingspecial said:**
> That`s because your directory is /usr/jm_scripts and not /usr/scripts

Thank you very much.
Now I realize that the message was not refering to the new folder I was trying to add, but to the default PATH.
This is what I get after re-booting (no Exports in .bashrc)

```
jm@jm-ThinkPad-X200s:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No existe el archivo o directorio

```

Obviously I checked all folders and they are there.
:-k

---

### Post by sisco311 on 2010-12-08
$PATH is replaced by the value of the PATH variable (/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games), which is not a file. ;)

So, if you want to print the value of the PATH variable, use:
```
echo $PATH
```

---

### Post by jmvidalvia on 2010-12-08
> **sisco311 said:**
> $PATH is replaced by the value of the PATH variable (/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games), which is not a file. ;)

So, if you want to print the value of the PATH variable, use:
```
echo $PATH
```

Many thanks.
:oops::oops::oops::oops::oops::oops:

PS: can someone please remove this thread?

---

