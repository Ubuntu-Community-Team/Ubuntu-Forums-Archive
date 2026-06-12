---
title: "sudo apt-get update not working"
date: 2011-12-02
forum: General Help
---

### Post by sam7777 on 2011-12-02
when i try to update my ubuntu 11.04 machine it looks for an IP which was used earlier by me. seems like it is cached somewhere in my machine.
my question is when we execute the command **sudo apt-get update** what is/are the file(s) it looks for?
i checked **sources.list** file and it has no problem.

Also i can't install software from s/w center too.

Any help regarding this will be greatly appreciated.Thank you.

---

### Post by faixan on 2011-12-02
if you had a proper proxy server setting earlier, 
try this

```

:~ export $http_proxy=''

```

and then run the commands you were trying.

---

