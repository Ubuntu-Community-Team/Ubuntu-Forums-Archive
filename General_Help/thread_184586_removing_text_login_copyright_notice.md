---
title: "removing text login copyright notice"
date: 2006-05-30
forum: General Help
---

### Post by starkes on 2006-05-30
ahoy!

is there any way to remove or change the text that shows up when you log in while in text mode?

Currently, for me, and i'm sure most of everyone else, it's this copyright notice:

```

Linux starkenboxx 2.6.12-10-686 #1 Fri Apr 28 13:21:56 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Tue May 30 06:30:12 2006


```

I've definitely seen it enough already, and I want to either change it or remove it. Maybe get fortune to run instead.

Also, is there a way to change the text shown *before* you login as well? It just says Ubuntu 5.10 "Breezy Badger"... etc.

---

### Post by Gustav on 2006-05-30
It is possible (I saw the solution somewhere in the forums not long ago) but I don't remember how to do it :(

---

### Post by ranf on 2006-05-30
Have a look at /etc/issue and /etc/motd.
I don't know how to incorporate fortune.

---

### Post by BrowneR on 2006-06-14
to get a fortune cookie each time a bash shell is started simply add the following to the end of your /etc/bash.bashrc

```

#get a fortune cookie!
fortune

```

its that simple. will also work in X virtual terminals.

make sure you have the fortune package installed and there are also some optional fortune databases containing extra quotes etc.

---

