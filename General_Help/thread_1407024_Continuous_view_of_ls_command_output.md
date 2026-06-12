---
title: "Continuous view of ls command output"
date: 2010-02-14
forum: General Help
---

### Post by Zilioum on 2010-02-14
My server is currently copying a large amount of date. I periodically check how much has already been copied by using the "ls" command in the destination folder. Is there a way so that ls kind of self updates itself? Like in a log or so? Or like when using cp -v?

Cheers

---

### Post by Satoru-san on 2010-02-14
here is something even better, I will make it a loop in a second, but here is the command 

```
du -h /path/to/folder
```throw this in an sh file

```

#! /bin/bash
while [ 1 ]
do
           du -h /path/to/folder;
           sleep 60
done

```

Opps forgot to mention what this does, it will tell you EXACTLY how many megabytes have been copied.

---

### Post by Zilioum on 2010-02-14
Looks very interesting, thanks. It will do very nicely for this. Is there a way to loop any command (just out of curiosity)? Or a quicker way? Because this is not very fast, so if its just a small task, its already done before your done with the script.

---

### Post by OliW on 2010-02-14
Just use the **watch** command.

```
watch -n 1 ls -l
```

That will refresh every second.

---

### Post by sandyd on 2010-02-14
> **Zilioum said:**
> Looks very interesting, thanks. It will do very nicely for this. Is there a way to loop any command (just out of curiosity)? Or a quicker way? Because this is not very fast, so if its just a small task, its already done before your done with the script.
```

#! /bin/bash
while [ 1 ]
do
XXXXXXXXXXXXXXX
done

```
forever looop
```

#! /bin/bash
while [$x<4]
do
XXXXXXXXXXXXXXX
$x= x+1
done

```
while loop 3 times.

oh, and alittle mod
will log to filesize.log which will be in your home.
```
#! /bin/bash
while [ 1 ]
do
           du -h /path/to/folder; >> ~/filesize.log
           sleep 60
done
```

---

### Post by Zilioum on 2010-02-14
Perfect, was looking for something like this. Thanks a lot to all of you!

---

### Post by Satoru-san on 2010-02-14
> **carlee said:**
> 
oh, and alittle mod
will log to filesize.log which will be in your home.
```
#! /bin/bash
while [ 1 ]
do
           du -h /path/to/folder; >> ~/filesize.log
           sleep 60
done
```

erm.

```
#! /bin/bash
while [ 1 ]
do
           du -h /path/to/folder >> ~/filesize.log;
           sleep 60
done
```
;)

---

### Post by OliW on 2010-02-14
I'll add with watch, you can have it highlight changes in the output:

```
watch -60 --differences ls -l
```

This is particularly useful with slow iterations where a few things change.

---

### Post by Satoru-san on 2010-02-14
> **OliW said:**
> I'll add with watch, you can have it highlight changes in the output:

```
watch -60 --differences ls -l
```This is particularly useful with slow iterations where a few things change.
Wow, I am adding watch to my arsenal, I haven't ever used it before

---

### Post by gansvv on 2011-01-07
```
watch -n 1 --differences du -h
```

Perfect to monitor changes in your current directory every 1sec! Thanks!

---

