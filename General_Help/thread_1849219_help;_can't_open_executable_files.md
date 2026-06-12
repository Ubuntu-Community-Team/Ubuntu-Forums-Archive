---
title: "help; can't open executable files?"
date: 2011-09-24
forum: General Help
---

### Post by vikash_chandola on 2011-09-24
see screnshot I was trying to open eclipse an unknown mesage appear. last day i start it finely. there was no problem.jre is installed in my computer,
Is it due to update. Today i update my computer.

---

### Post by MG&amp;TL on 2011-09-24
Could you try in a terminal:

```
 
cd ~/Desktop/eclipse
./eclipse 
```And see whether anything happens?

If that doesn't work, try:

```
cd ~/Desktop/eclipse
chmod +x eclipse
./eclipse
```

---

### Post by logiblocs on 2011-09-24
It may just be easier to
```
sudo apt-get install eclipse
```

---

### Post by vikash_chandola on 2011-09-24
> **MG&TL said:**
> Could you try in a terminal:

```
 
cd ~/Desktop/eclipse
./eclipse 
```And see whether anything happens?

If that doesn't work, try:

```
cd ~/Desktop/eclipse
chmod +x eclipse
./eclipse
```
Oh thanks dude second one worked.
can you explain this command work so that i use it for other programs also.specially second line that is **chmod +x eclipse**

---

### Post by sanderd17 on 2011-09-24
read this page: [http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

But it would be even better if you read the entire tutorial.

chmod +x isn't explained, but it's just an alternative way of using chmod (as you see, adding the 'x' bit for every user).

---

### Post by dino99 on 2011-09-24
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by MG&amp;TL on 2011-09-24
```
chmod +x 
```

makes a file, binary or script executable. Although if you're talking about the IDE, then get the repository one. Much easier.

---

### Post by vikash_chandola on 2011-09-24
> **sanderd17 said:**
> read this page: [http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

But it would be even better if you read the entire tutorial.

chmod +x isn't explained, but it's just an alternative way of using chmod (as you see, adding the 'x' bit for every user).
thanks friends. You also save one more software that is qtiplot. a graph drawing software now i can also use that software with this commands(run in terminal by making slight change)

---

