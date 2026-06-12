---
title: "Questions"
date: 2010-08-23
forum: General Help
---

### Post by martinez6341 on 2010-08-23
what does desktop manager do?

What does $ do?

what is loop for in command line?

What is the best way to switch user? Using command line?

---

### Post by drpjkurian on 2010-08-23
Hi
Desktop manager is a GUI between you and the OS

---

### Post by anirudhtomer on 2010-08-23
I think u should first take a shell scripting lesson here
[http://bash.cyberciti.biz/guide/Main_Page](http://bash.cyberciti.biz/guide/Main_Page)

& "for" loop is a very common loop used in many languages...its working is the same here.

```
anirudh@anirudh-laptop: ~  [561] : $ > for x in 1 2 3
> do
> echo $x
> done
1
2
3
```

---

### Post by Vaphell on 2010-08-23
care to provide any example?

---

### Post by Perfect Storm on 2010-08-23
$ = user
# = root

or do you mean regarding scripting?

---

### Post by anirudhtomer on 2010-08-23
"su - username"  to switch user in a login shell
"su username" to switch user in a non login shell

---

### Post by Vaphell on 2010-08-23
or $ = variable
echo $PATH

---

### Post by anirudhtomer on 2010-08-23
$ does a lot of things.
its significance is that if u place it in front of any word..it will execute that on shell.

$ is also used in REGEX to check if the line ends with a particular word...
I mean $ has a large significance everywhere on LINUX...

---

