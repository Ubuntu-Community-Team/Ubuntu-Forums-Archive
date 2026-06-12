---
title: "weird tab autocomplete and ls behaviour"
date: 2012-09-16
forum: General Help
---

### Post by newbuntus on 2012-09-16
I've just installed ubuntu on our family comp, and I'm having a slight problem with tab autocomplete and the "ls" command. Here are some examples: 

$ ls /dev (lists devices but does not show hard drives)
$ ls /de<TAB> = /dev/ (another 2 tabs shows all devices including hard drives as expected)
$ sudo mount /de<TAB> = /dev/fd0 (if I erase "fd0" after "/dev/" and type sd<TAB><TAB> it lists nothing)
$ mount /de<TAB> = /dev/fd0 (if I erase "fd0" after "/dev/" and type sd<TAB><TAB> it shows all my hard drives)

So, can anyone explain the inconsistent behavior with regards to listing hard drives and how I might fix it? Cheers.

---

### Post by dcstar on 2012-09-16
> **newbuntus said:**
> I've just installed ubuntu on our family comp, and I'm having a slight problem with tab autocomplete and the "ls" command. Here are some examples: 

$ ls /dev (lists devices but does not show hard drives)
$ ls /de<TAB> = /dev/ (another 2 tabs shows all devices including hard drives as expected)
$ sudo mount /de<TAB> = /dev/fd0 (if I erase "fd0" after "/dev/" and type sd<TAB><TAB> it lists nothing)
$ mount /de<TAB> = /dev/fd0 (if I erase "fd0" after "/dev/" and type sd<TAB><TAB> it shows all my hard drives)

So, can anyone explain the inconsistent behavior with regards to listing hard drives and how I might fix it? Cheers.

[LIST=1]
[*]Works fine on my system, all devices displayed.
[*]Same - as expected.
[*]Autocomplete only ever works for the first command, which is "sudo" in this case.
[*]Same - as expected.
[/LIST]

---

