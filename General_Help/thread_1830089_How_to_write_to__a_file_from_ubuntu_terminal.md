---
title: "How to write to  a file from ubuntu terminal?"
date: 2011-08-21
forum: General Help
---

### Post by MGTHEBOSS on 2011-08-21
I have created a file newfile.txt using:
touch newfile.txt
Now I want to write to that file from terminal i.e whatever I will type after the $ will be written to the file ----
this is what I want.
How can I do that?

---

### Post by sanderd17 on 2011-08-21
```
echo "xyz" > newfile.txt
```

will do the trick

---

### Post by raja.genupula on 2011-08-21
the post given by sanderd17 is the exact answer for you .

nothing but echo "xyz" will produce the output as xyz .

the " > " used to forward that output to the file you have given after the "> " .

you can use " cat " command to display the data of the file .

one more thing is " >> " . if use 
$echo "xyz" > newfile.txt
$echo "abc" >> newfile.txt
 
now your file going to have the previous output (xyz) and present output (abc). but if you go for ">" then every time new update will be in the file . old one will erased .

---

### Post by MGTHEBOSS on 2011-08-21
> **sanderd17 said:**
> ```
echo "xyz" > newfile.txt
```will do the trick
That's OK but if you read my post carefully you will find that that's not what I want exactly.

---

### Post by dave01945 on 2011-08-21
just type

```
nano newfile.txt
```

or you can use

```
vim newfile.txt
```

seconds takes abit of learning to use but it's worth it

```
vimtutor
```

will tell you the basics

but from reading your post what sanjerd put is what you asked for
either using > to replace or >> to append

---

### Post by sanderd17 on 2011-08-21
> **MGTHEBOSS said:**
> That's OK but if you read my post carefully you will find that that's not what I want exactly.

So you don't want to use other commands? 

This is already done for you, it's stored to the file .bash_history.

---

### Post by raja.genupula on 2011-08-21
still i didnt get him . was he means what ever after $ ....man . what a post . ok is there any special purpose behind this ? actually is it really possible ?

---

