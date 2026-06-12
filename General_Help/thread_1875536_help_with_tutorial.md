---
title: "help with tutorial"
date: 2011-11-04
forum: General Help
---

### Post by dan0804smith on 2011-11-04
so i am using this tutorial:

[http://ubuntuforums.org/archive/index.php/t-527934.html](http://ubuntuforums.org/archive/index.php/t-527934.html)

can sombody walk me through step by step how to do this?

the user nam is daniel and it is in "downloads"

so far i have sudo cp aleksPack10.jar/daniel/downloads/java-6-sun-0.00/jre/lib/ext/
it not working

i know this is a very noob thing but please help me

---

### Post by haqking on 2011-11-04
> **dan0804smith said:**
> so i am using this tutorial:

[http://ubuntuforums.org/archive/index.php/t-527934.html](http://ubuntuforums.org/archive/index.php/t-527934.html)

can sombody walk me through step by step how to do this?

the user nam is daniel and it is in "downloads"

so far i have sudo cp aleksPack10.jar/daniel/downloads/java-6-sun-0.00/jre/lib/ext/
it not working

i know this is a very noob thing but please help me

wasnt it all covered in your previous thread on same subject [http://ubuntuforums.org/showthread.php?t=1849567](http://ubuntuforums.org/showthread.php?t=1849567)

---

### Post by fdrake on 2011-11-04
there is a space between the 2 paths, you mistyped.
it should be:
```

sudo cp aleksPack10.jar /daniel/downloads/java-6-sun-0.00/jre/lib/ext/

```
post here the result of your command please. make sure you are in the same directory (with the terminal) where alekPack10.jar file is located.

---

### Post by haqking on 2011-11-04
> **fdrake said:**
> there is a space between the 2 paths, you mistyped.
it should be:
```

sudo cp aleksPack10.jar /daniel/downloads/java-6-sun-0.00/jre/lib/ext/

```
post here the result of your command please. make sure you are in the same directory (with the terminal) where alekPack10.jar file is located.

it is likely to be Downloads and not downloads also, as *nix is case sensitive

---

### Post by lisati on 2011-11-04
> **haqking said:**
> wasnt it all covered in your previous thread on same subject [http://ubuntuforums.org/showthread.php?t=1849567](http://ubuntuforums.org/showthread.php?t=1849567)

My thoughts exactly. Posting multiple threads on the same problem *can* dilute the community's efforts to help.

---

### Post by fdrake on 2011-11-04
> **haqking said:**
> it is likely to be Downloads and not downloads also, as *nix is case sensitive

well having a Daniel folder in the root file system shows that (s)he is following a standard hierarchy-file-system... i don't know what is this all for ..you probably know more then me from the previous thread.

---

