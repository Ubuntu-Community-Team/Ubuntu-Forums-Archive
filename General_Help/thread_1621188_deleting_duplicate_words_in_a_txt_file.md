---
title: "deleting duplicate words in a txt file"
date: 2010-11-14
forum: General Help
---

### Post by cry8wolf9 on 2010-11-14
i waas wondering if anyone knew of a script or program that removes duplicate words in a txt file. im making an install script and the install list has gotten a bit long so i want to ensure there are no duplicates in the file

---

### Post by dcstar on 2010-11-15
> **cry8wolf9 said:**
> i waas wondering if anyone knew of a script or program that removes duplicate words in a txt file. im making an install script and the install list has gotten a bit long so i want to ensure there are no duplicates in the file

Google has hundreds of thousands of them, here's one:

[http://programming.itags.org/unix-linux-programming/94445/](http://programming.itags.org/unix-linux-programming/94445/)

---

### Post by gmargo on 2010-11-15
```

sort -u

```Or if you don't want it sorted, it's a rather trivial perl script.
```

$ cat input.txt
eagle
abaciscus
eagle
baccalaurean
eagle
cabinetworking
cabinetworking
eagle
dacryelcosis
cabinetworking

$ perl -n -e 'print $_ unless $x{$_}++;' < input.txt 
eagle
abaciscus
baccalaurean
cabinetworking
dacryelcosis

```

---

