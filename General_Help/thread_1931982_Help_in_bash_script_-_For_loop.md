---
title: "Help in bash script - For loop"
date: 2012-02-26
forum: General Help
---

### Post by JCM_Pico on 2012-02-26
Hi there,

I'm trying to make a script to compare all the files within a folder with the previous created one with the diff command.... and remove it if its equal 

Something like 

```
diff file1 file2
diff file2 file3
diff file3 file4
```

But I cant find a way to make the for loop to go throw the files.... 

I under stand that I can feed the file list with

```
 [COLOR=#808080]*#!/bin/bash*[/COLOR] [COLOR=#000000]**for**[/COLOR] [COLOR=#c20cb9]**i**[/COLOR] [COLOR=#000000]**in**[/COLOR] 'ls -l /folder/* [COLOR=#000000]**do**[/COLOR] 
...
done
```

But how can I say to bash to start in i+1 and to feed the comand like
```
diff $i-1 $i

```


Any idea

---

### Post by sudodus on 2012-02-26
This is the syntax to have an incremental for-loop

```
for (( i=1; i<=20 ; i++ )) ; do echo $i $((i-1));done
```

---

### Post by JCM_Pico on 2012-02-26
> **sudodus said:**
> This is the syntax to have an incremental for-loop

```
for (( i=1; i<=20 ; i++ )) ; do echo $i $((i-1));done
```

that works fine with number... rigth??? but if I have something like

for i in 'file_a' 'file_b' 'file_c' 'file_d'

How can I do it?

---

### Post by sudodus on 2012-02-26
> **JCM_Pico said:**
> that works fine with number... rigth??? but if I have something like

for i in 'file_a' 'file_b' 'file_c' 'file_d'

How can I do it?
> ```
diff file1 file2
diff file2 file3
diff file3 file4
...
```
can be implemented with
```
diff "file$i" "file$((i+1))"
```
in the for-loop

---

### Post by JCM_Pico on 2012-02-26
But my files are not name with a simple increment.... and for all that I understand... that way I only can numerically increment file names.....

201202261850_lajes.jpg
201202261852_lajes.jpg
201202261854_lajes.jpg
201202261856_lajes.jpg
201202261858_lajes.jpg
201202261900_lajes.jpg
201202261902_lajes.jpg
201202261904_lajes.jpg
.
.
.
201202261806_lajes.jpg
.
.
.
201202261908_lajes.jpg
.
.
.
201202262010_lajes.jpg

---

### Post by sudodus on 2012-02-26
> **JCM_Pico said:**
> But my files are not name with a simple increment.... and for all that I understand... that way I only can numerically increment file names.....

201202261850_lajes.jpg
201202261852_lajes.jpg
201202261854_lajes.jpg
201202261856_lajes.jpg
201202261858_lajes.jpg
201202261900_lajes.jpg
201202261902_lajes.jpg
201202261904_lajes.jpg
.
.
.
201202261806_lajes.jpg
.
.
.
201202261908_lajes.jpg
.
.
.
201202262010_lajes.jpg
For ***diff*** to work you have to get pairs and shift the 'pairing'. How do you intend to do that? Can you sort the files alphabetically?

---

### Post by JCM_Pico on 2012-02-26
Found a way....

the name of the files is the time of the download and they are downloaded every 2 minutes... so instead of checking if they are the same at the end of the day I make it every 2 minutes - at the time of download... that way I simply do:

```
imgdate=$(date +%Y%m%d%H%M)
urlpath=""#############"

sleep 30
wget --tries=20 --continue "$urlpath" -O "$imgdate".jpg

lastimgdate=$(date --date='-2 minutes' +%Y%m%d%H%M)

if diff "$imgdate".jpg "$lastimgdate".jpg >/dev/null ; then
  rm "$imgdate".jpg
else
  echo Different
fi
```

And its solved....

Thanks any way :D

---

### Post by sudodus on 2012-02-26
[s]Is this a big one-off job, or will it be repeated many times? I mean, should the sorting be automatic, or could it be manual? Or are the files sorted already (for example by the time stamp?[/s]

Yes, that is a good solution. You need not keep a lot of files that are only copies :-)

---

### Post by Khayyam on 2012-02-26
"file1 file2 file3 file4" ... that looks "incremental" to me. Why do people insist on **not** posting the actual dataset, and/or code, they are working on.

Anyow, for this "example" (or future "loops") you need to -1 the number of actual files as they will be incremented +1 ... eg:

```
for (( i=1; i<=(($# -1 )); i++ )); do
    diff "file${i}" "file$((i+1))"
done
```Without the -1 the last +1 won't exist.

best ... khay

---

