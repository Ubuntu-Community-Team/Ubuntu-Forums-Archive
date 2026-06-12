---
title: "Create bulk files via terminal"
date: 2010-02-10
forum: General Help
---

### Post by squareff255 on 2010-02-10
K, I'm gonna be honest, I don't have a practical purpose for this, but I was just wondering if, for example, I'm using my terminal in my home folder and I want to create a bunch of files:
asdf.txt
asdf2.txt
asdf3.txt
asdf4.txt
etc...
So, I was wondering if that's possible. I tried:
```

$ asdf[1-20].txt

```
but that just created a file called asdf[1-20].txt... so anyway, thanks in advance for the help!

---

### Post by K7522 on 2010-02-10
```

#!/bin/bash
export loop="1"
export loopEnd="20"
while [ $loop -gt 0] && [ $loop -le $loopEnd ]
do
touch /home/K7522/asdf`echo $loop`.txt
loop=$[loop+1]
done
exit 0

```

To explain this, you create a file named, say, createfiles.sh and you plug that code in there. Save it and right click, go to properties, permissions and set it as executable.

Then you simply run it in terminal and it will create the files with incrementing numbers based on the $loop variable. Adjust loopEnd to the number of files you want, adjust the touch line to make sure it's going where you want it and let it go to town.

---

### Post by sisco311 on 2010-02-10
or```

for i in $(seq 1 20); do
  > file${i}.txt
done

```

---

### Post by K7522 on 2010-02-10
Learn something new every day! Great stuff sisco.

---

### Post by sisco311 on 2010-02-10
> **K7522 said:**
> Learn something new every day! Great stuff sisco.

touch updates  the  access  and modification times of each FILE to the current time. If the file doesn't exist it's created empty.

it's very slow:
```
sisco@acme:~/xtmp$ rm file*
sisco@acme:~/xtmp$ time for i in $(seq 1 10000); do touch file${i}.txt; done

[COLOR="Red"]real	0m38.425s
user	0m11.809s
sys	0m22.695s[/COLOR]
sisco@acme:~/xtmp$ rm file*
sisco@acme:~/xtmp$ time for i in $(seq 1 10000); do > file${i}.txt; done

[COLOR="Green"]real	0m0.620s
user	0m0.380s
sys	0m0.187s[/COLOR]


```

another option is the c style for loop:
```
for (( i=1; i<=10000; i++ )); do 
  > file${i}.txt
done
```

---

### Post by falconindy on 2010-02-10
No need to call an external program.
```
$ time touch file{1..10000}

real    0m0.168s
user    0m0.025s
sys     0m0.121s
```

---

### Post by sisco311 on 2010-02-10
> **falconindy said:**
> No need to call an external program.
```
$ time touch file{1..10000}

real    0m0.168s
user    0m0.025s
sys     0m0.121s
```

d'oh! you're right. :redface:

---

### Post by squareff255 on 2010-02-13
Wow! Thanks guys! I need to learn more about shell programming. :)

---

