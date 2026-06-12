---
title: "store file in bash."
date: 2012-06-17
forum: General Help
---

### Post by spiritech on 2012-06-17
how can i store a file in bash, in a similar way i store a word or phrase. example:

f=word

echo $f

word

i would like to do this with a file.

spiritech.

---

### Post by SeijiSensei on 2012-06-17
```
echo $f > /path/to/some/file
```

---

### Post by codemaniac on 2012-06-17
> **spiritech said:**
> how can i store a file in bash, in a similar way i store a word or phrase. example:

f=word

echo $f

word

i would like to do this with a file.

spiritech.

Do you want to store the filename in a bash variable or the file contents ?


```
FILENAME=myfile.dat

cat $FILENAME
```

To store the file contents on a bash variable 
```
FILE=$(cat myfile.dat)

echo $FILE
```

---

### Post by sisco311 on 2012-06-17
Sounds like an XY problem. ;)

The data is already in the file. Why would you want to store it in a variable?

If you want to parse the file line by line, then check out BashFAQ 001 (link in my sig).

Oh, and don't use **f="$(< filename)"** or **f="$(cat filename)"**  (BashPitfalls 41).

---

### Post by spiritech on 2012-06-17
> **sisco311 said:**
> Sounds like an XY problem. ;)

The data is already in the file. Why would you want to store it in a variable?

i just wanted to know if it was possible to store a whole file as a variable without having to write it out.

> **sisco311 said:**
>  If you want to parse the file line by line, then check out BashFAQ 001 (link in my sig).

Oh, and don't use **f="$(< filename)"** or **f="$(cat filename)"**  (BashPitfalls 41). 

seems to me that f=filename then cat $f is the same as doing cat filename.

does the variable get stored in the ram or hard drive?

---

### Post by codemaniac on 2012-06-17
> **spiritech said:**
> 
seems to me that f=filename then cat $f is the same as doing cat filename.



Yes they are same .But imagine a scenario where in a script you have used a filename "oldfile.dat" 10 k times ,and some other day you have to change the filename to "newfile.dat" in your script .

Hence it is always suggested not to hard code the filename and use a variable FILENAME instead to avoid mass substitution .

---

### Post by codemaniac on 2012-06-17
> **sisco311 said:**
> 
Oh, and don't use **f="$(< filename)"** or **f="$(cat filename)"**  (BashPitfalls 41).

Hello sisco311 ,

Thanks for pointing that out .
That was only for examples sake , No way one should do it on a production script , considering the pitfalls under the hood .

There are "1?" ways to parse a file contents . ;)

---

### Post by spiritech on 2012-06-17
> **codemaniac said:**
> Yes they are same .But imagine a scenario where in a script you have used a filename "oldfile.dat" 10 k times ,and some other day you have to change the filename to "newfile.dat" in your script .

Hence it is always suggested not to hard code the filename and use a variable FILENAME instead to avoid mass substitution .

ok. thankyou.

does the variable get stored in the ram or hard drive? i guess it is ram.

---

### Post by sisco311 on 2012-06-17
> **codemaniac said:**
> Yes they are same .But imagine a scenario where in a script you have used a filename "oldfile.dat" 10 k times ,and some other day you have to change the filename to "newfile.dat" in your script .

Hence it is always suggested not to hard code the filename and use a variable fILENAME instead to avoid mass substitution .

fixed ;)

Only environment variables (EDITOR, SHELL, ...) and internal shell variables (BASH_VERSION, RANDOM, ...) shall be capitalized. All other variables names shall contain at least one lowercase letter. This convention avoids accidentally overriding internal and environmental variables.

---

### Post by sisco311 on 2012-06-17
> **spiritech said:**
> ok. thankyou.

does the variable get stored in the ram or hard drive? i guess it is ram.

Usually in the RAM.

---

### Post by codemaniac on 2012-06-18
> **sisco311 said:**
> 
Only environment variables (EDITOR, SHELL, ...) and internal shell variables (BASH_VERSION, RANDOM, ...) shall be capitalized. All other variables names shall contain at least one lowercase letter. This convention avoids accidentally overriding internal and environmental variables.

Not written in the stone though .The UPPER case convention suits best for me and have been using it for a long time .


Yeah , needs to be careful when i use the user variable names that somehow resembles to the ENVIRONMENT ones .

---

