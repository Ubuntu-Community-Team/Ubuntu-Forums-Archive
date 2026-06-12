---
title: "help renaming some files."
date: 2012-05-12
forum: General Help
---

### Post by spiritech on 2012-05-12
I have some files named with the following format.

File_Name/Then_Eleven_Digit_Code.mp4

there are quite a few files all with a different eleven digit code followed by .mp4
the code is situated at the end of the file name and before the .mp4

i would like to remove the eleven digit code and just leave the .mp4 at the end. i tried using gprenamer.
i used the following format under the remove/replace tab

remove ***********.mp4 and replace with .mp4

i though it would except the wild card options for each character in the of the code. it didnt work.

is there another way of doing this?

spiritech.

command line options excepted. :)

---

### Post by cmont899 on 2012-05-12
how about

```
for each in `ls File_Name`; do 
    newname=`echo $each | sed 's/[1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9]//g'`
    mv $each $newname
done

```

or as a oneliner:
```
for each in `ls File_Name`; do newname=`echo $each | sed 's/[1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9]//g'`; mv $each $newname; done

```

---

### Post by cmont899 on 2012-05-12
> **cmont899 said:**
> how about

```
for each in `ls File_Name`; do 
    newname=`echo $each | sed 's/[1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9]//g'`
    mv $each $newname
done

```or as a oneliner:
```
for each in `ls File_Name`; do newname=`echo $each | sed 's/[1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9][1-9]//g'`; mv $each $newname; done

```

realised that wouldn't catch the zeros:
```
for each in `ls File_Name`; do 
    newname=`echo $each | sed 's/[[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]]//g'`
    mv $each $newname
done

```

---

### Post by spiritech on 2012-05-12
> **cmont899 said:**
> realised that wouldn't catch the zeros:
```
for each in `ls File_Name`; do 
    newname=`echo $each | sed 's/[[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]][[:digit:]]//g'`
    mv $each $newname
done

```


the code has both numbers and letters in it. i was also after a way to do it all in one go. 

example

MyFilef84u9s4kmg5.mp4

there must be a way to use a the wildcard * for each character of the code. so maybe i could remove the whole thing by searching for the expression ***********.mp4  then simply add the .mp4 back in with gprenamer. i just dont know the right program that can do this.

---

### Post by steeldriver on 2012-05-12
how about just removing the last 11.3  (15 characters total) directly in bash using the 
```
${parameter:offset:length}
``` syntax, and then replacing the suffix?

```
for f in `ls *.mp4`; do mv $f ${f:0:${#f}-15}.mp4; done
```

---

### Post by spiritech on 2012-05-12
> **steeldriver said:**
> how about just removing the last 11.3  (15 characters total) directly in bash using the 
```
${parameter:offset:length}
``` syntax, and then replacing the suffix?

```
for f in `ls *.mp4`; do mv $f ${f:0:${#f}-15}.mp4; done
```

yes that would work fine. will the code above do all the files in that dir in one go?
and does that have to be done with a bash script. if not do i enter bash when i am in the required dir.

---

### Post by papibe on 2012-05-12
Hi spiritech.

You can also use the command 'rename'. For instance:
```
rename 's/[0-9]{11}\.mp4$/.mp4/'  *
```
Regards.

---

### Post by steeldriver on 2012-05-12
^^^ ah yes, that's much neater - although I think we would need to use the pattern [0-9a-z-A-Z]{11} to catch the alphanumeric sequence:

```
$ rename 's/[0-9a-zA-Z]{11}\.mp4$/.mp4/'  *
```or even just match *any* 11-character sequence terminated by .mp4:

```
$ rename 's/.{11}\.mp4$/.mp4/'  *
```But to answer your question above, if you did want to use my previous suggestion you would type

```

for f in `ls *.mp4`; do mv $f ${f:0:${#f}-15}.mp4; done

```exactly as shown at the command prompt, after cd'ing to the directory where you want to change files

Any of these should catch all the *.mp4 files in the current directory (but not descend to subdirectories, if you need to change files below the current dir we will need a bit more work)

---

### Post by spiritech on 2012-05-12
Thank you for your help. the rename one worked for me. :)

---

