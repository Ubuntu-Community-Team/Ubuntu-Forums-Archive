---
title: "dpkg --get-selections"
date: 2010-06-02
forum: General Help
---

### Post by cmcanulty on 2010-06-02
When I get a list of my packages  using
```
dpkg --get-selections
``` it starts with the letter n,I never get the a-m, part of the list. I need a little help on this.Below is start of list it goes through to z
```
netcat-openbsd					install
network-manager					install
network-manager-gnome				install
network-manager-pptp				install
network-manager-pptp-gnome			install
noteedit					install

```

---

### Post by darolu on 2010-06-02
This happens because the list is too large to be displayed; you can use "more" to print one page at a time:
```
dpkg --get-selections | more
```
Another alternative is to print it to a file:
```
dpkg --get-selections > mylist.txt
```

---

### Post by vevel on 2010-06-02
Hmm -- how about trying the complete dpkg path, and piping to 'less' or 'more' ?

```
/usr/bin/dpkg --get-selections | more

```

---

### Post by cmcanulty on 2010-06-02
Oh thanks that was all it needed.

---

