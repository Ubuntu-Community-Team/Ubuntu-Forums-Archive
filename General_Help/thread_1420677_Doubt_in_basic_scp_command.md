---
title: "Doubt in basic scp command"
date: 2010-03-03
forum: General Help
---

### Post by jsriz on 2010-03-03
I Have this file named -c at a local server (which got it name by mistake when i ran wget command with -c)
I am not able to scp this file into my system as it is trying to take -c as an attribute to the scp command.here is the command that i ran:
```

scp -c myuser@mylocalip:

```

---

### Post by lloyd_b on 2010-03-03
> **jsriz said:**
> I Have this file named -c at a local server (which got it name by mistake when i ran wget command with -c)
I am not able to scp this file into my system as it is trying to take -c as an attribute to the scp command.here is the command that i ran:
```

scp -c myuser@mylocalip:

```
Try putting the "-c" in quotation marks - that should keep scp from seeing it as a parameter.

Lloyd B.

---

### Post by jsriz on 2010-03-03
> **lloyd_b said:**
> Try putting the "-c" in quotation marks - that should keep scp from seeing it as a parameter.

Lloyd B.
Nope still considers it as a parameter as still the same op:
```

usage: scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 [...] [[user@]host2:]file2

```

---

### Post by foldingstock on 2010-03-03
Before you attempt to transfer that file, you need to name it something else. "-c" as a filename is going to give you a lot of trouble. 

If you don't have anything else in that directory that ends with "c," try "mv *c somenewname."

---

### Post by jsriz on 2010-03-03
> **foldingstock said:**
> Before you attempt to transfer that file, you need to name it something else. "-c" as a filename is going to give you a lot of trouble. 

If you don't have anything else in that directory that ends with "c," try "mv *c somenewname."
Nope that returns :
```

mv: invalid option -- c
Try `mv --help' for more information.

```

---

### Post by undecim on 2010-03-03
```
mv -- -c c
```will rename "-c" to "c" so that you can transfer it.

---

### Post by bodhi.zazen on 2010-03-03
I would also advise you rename the file , the - character is problematic

You may rename it with the -- option

```
mv -- -c some_other_name
```

Edit: beaten by [undecim]("http://ubuntuforums.org/member.php?u=623644")

---

### Post by jsriz on 2010-03-03
> **bodhi.zazen said:**
> I would also advise you rename the file , the - character is problematic

You may rename it with the -- option

```
mv -- -c some_other_name
```Edit: beaten by [undecim]("http://ubuntuforums.org/member.php?u=623644")
Solved thanx a ton guyz
Again solved in about an hour of posting...

---

