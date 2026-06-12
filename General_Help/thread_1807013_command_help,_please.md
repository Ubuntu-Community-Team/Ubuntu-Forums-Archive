---
title: "command help, please"
date: 2011-07-18
forum: General Help
---

### Post by Diametric on 2011-07-18
Hello,

I am looking for a command that accomplished the following:

1. Test the size of a given file
2. If file size is greater than 0
3. touch myfile

Can anyone help me with what the appropriate command chain would be?

I am configuring my DNS server and want to test some data.

Thanks!

---

### Post by zero2xiii on 2011-07-18
Auhm,

Yea... A feeeew things:

1. Command? Say what? progrmaing language? Bash? PHP? something else?

2. File size greater than zero what? bytes I asume? As in eg an empty text file?

3. Please give more info on HOW you wish to use this?

---

### Post by Diametric on 2011-07-18
Sorry, but yes, my question is specific to bash command line

Also, the test is for whether the file is empty or not

I am creating a package where, during the install process, I want to test the above conditions and if size is greater than zero, I want to create another file.

---

### Post by sisco311 on 2011-07-18
```
if [ -s 'foo' ]
then
  > 'bar'
fi
```

---

### Post by Diametric on 2011-07-18
that makes sense. Thank you for your reply.  I'll give this a try and see what happens.

Cheers!

---

### Post by Diametric on 2011-07-20
This is what finally ran correctly:

```
if [ -s /home/username/myfile ]; then 
         mv /home/username/myfile  /home/username/myfile.bak 
         touch /home/username/myfile.itworked 
fi  
```

Many thanks for the help!

---

### Post by sisco311 on 2011-07-20
Glad it worked.

If you want to create a new empty file, then you should use > instead of touch. It's much faster than touch and if the file exist it is truncated to zero size. touch updates the file's atime and mtime and if the file does not exist, it's created empty. 

```
[sisco@acme xtmp]$ time for i in {1..10000}; do touch "$i"; done

real	[color=red]2m0.121s[/color]
user	[color=red]0m2.856s[/color]
sys	[color=red]0m5.956s[/color]

```
```
[sisco@acme xtmp]$ time for i in {1..10000}; do > "$i"; done

real	[color=green]0m1.658s[/color]
user	[color=green]0m0.213s[/color]
sys	[color=green]0m0.127s[/color]

```

---

### Post by enimeizoo on 2011-07-20
> **zero2xiii said:**
> 

2. File size greater than zero what? bytes I asume? As in eg an empty text file?



Actually that doesn't matter, since 0b = 0B = 0kB = ...
Sorry, I had to.

---

### Post by zero2xiii on 2011-07-20
> Sorry, I had to.

Haha no problem. Some one had to ask the question :biggrin:

---

