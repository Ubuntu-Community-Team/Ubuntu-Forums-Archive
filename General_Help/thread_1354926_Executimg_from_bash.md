---
title: "Executimg from bash"
date: 2009-12-14
forum: General Help
---

### Post by pfdevil on 2009-12-14
Hello,

I downloaded eclipse. Now I want to configure the executable to run from bash by typing a command like:

```
eniac@eniac:~$ eclipse 
```

How would I go about accomplishing this.

Thanks

---

### Post by nothingspecial on 2009-12-14
```
mkdir ~/bin
```

Rename the executable to eclipse

```
mv eclipse ~/bin
```

```
bash
```

---

### Post by pfdevil on 2009-12-14
Hello,

Thanks for the reply, but I have tried most of the basics.

I've tried to create a symbolic link, but for some reason it will not execute.

The file that I am trying to create a link to is a shell script that is usually executed as ./script

---

### Post by Physical Hook on 2009-12-14
Add an alias:

```
alias eclipse='/home/user/eclipse/launcher.sh'
```

** Just an example.

---

### Post by nothingspecial on 2009-12-14
You need to put it in your path.

~/bin and /usr/bin are in your path. But ubuntu doesn`t install with a ~/bin directory, so you have to create one.

Or just put it in /usr/bin, it`s just safer in your home directory but it doesn`t matter.

If you want to execute it with eclipse you have to change the name to eclipse.

---

