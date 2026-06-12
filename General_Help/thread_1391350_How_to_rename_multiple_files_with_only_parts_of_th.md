---
title: "How to rename multiple files with only parts of the original name in the new name"
date: 2010-01-26
forum: General Help
---

### Post by bwitherell on 2010-01-26
Hi,

Could someone help me find a way to rename a file to a different name containing parts of its old name?

For example:

Original file name: filename1.abc.xyz.some.other.stuff
Final file name: filename1.abc.xyz

The length of the file name is not constant
the abc.xyz is not constant but that format is (three numbers.three numbers)
the .some.other.stuff is not constant and its what i want to get rid of

Any help is appreciated.

Thank You!

---

### Post by tors on 2010-01-26
Hiya. Maybe create a script for the operation:

```
#!/bin/sh

files=`ls /path/to/files/`


for oldfilename in $files ; do

 newfilename=`echo $oldfilename | sed "s/\(.*\.[0-9][0-9][0-9]\.[0-9][0-9][0-9]\)\..*/\1/"`
 echo $newfilename

done

```

If it works, replace "echo $newfilename" with "mv $oldfilename $newfilename"

---

### Post by ibuclaw on 2010-01-26
> **tors said:**
> Hiya. Maybe create a script for the operation:

```
#!/bin/sh

files=`ls /path/to/files/`


for oldfilename in $files ; do

 newfilename=`echo $oldfilename | sed "s/\(.*\.[0-9][0-9][0-9]\.[0-9][0-9][0-9]\)\..*/\1/"`
 echo $newfilename

done

```


If it works, replace "echo $newfilename" with "mv $oldfilename $newfilename"

hmm... you can get simpler than that my friend...

Try the more obfuscated:
```
rename 's/^((.+?\.){2}.+?)\..*$/$1/' *
```

Regards
Iain

---

### Post by sisco311 on 2010-01-26
You can try one of the GUI bulk renaming tools:

[list]
[*]thunar (file manager)
[*]gprename (gtk)
[*]purrr (gtk)
[*]pyrenamer (gtk)
[*]gwenrename (qt)
[*]krename (qt)
[/list]

---

### Post by bwitherell on 2010-01-26
> **tinivole said:**
> hmm... you can get simpler than that my friend...

Try the more obfuscated:
```
rename 's/^((.+?\.){2}.+?)\..*$/$1/' *
```

Regards
Iain

I like that your way is only one line but I'm reluctant to use it since I can't make heads or tails of it. Could you provide a short explanation of how this works? Thanks.

---

### Post by Cresho on 2010-01-26
krename is the best

---

### Post by bwitherell on 2010-01-26
> **sisco311 said:**
> You can try one of the GUI bulk renaming tools:

[list]
[*]thunar (file manager)
[*]gprename (gtk)
[*]purrr (gtk)
[*]pyrenamer (gtk)
[*]gwenrename (qt)
[*]krename (qt)
[/list]

Thanks for the reply. But I need to do this with the cli not GUI. Thanks though.

---

### Post by ibuclaw on 2010-01-29
> **bwitherell said:**
> I like that your way is only one line but I'm reluctant to use it since I can't make heads or tails of it. Could you provide a short explanation of how this works? Thanks.

```
rename 's/^((.+?\.){2}.+?)\..*$/$1/' *
```
To break down:
```

/^((.+?\.){2}.+?)\..*$/


^             Match start of line
(             Start of Parenthesis $1
   (          Start Sub-Parenthesis
      .+?\.   Match any character 1+ times (non-greedy), followed by a period.
   ){2}       End of Sub-Parenthesis, Match it twice (ie:  "anything.anything." )
   .+?        Match any character 1+ times (non-greedy)
)             End of Parenthesis $1
\..*          Match a period, followed by anything 0 or more times.
$             Match end of line

```

So if we have:
```
anything.anything.txt.nowant.nowant
```
This will match:
```
^((anything.anything.)txt).nowant.nowant$
```
And returns $1,which is:
```
anything.anything.txt
```

Regards
Iain

---

### Post by bwitherell on 2010-02-05
> **ibuclaw said:**
> ```
rename 's/^((.+?\.){2}.+?)\..*$/$1/' *
```
To break down:
```

/^((.+?\.){2}.+?)\..*$/


^             Match start of line
(             Start of Parenthesis $1
   (          Start Sub-Parenthesis
      .+?\.   Match any character 1+ times (non-greedy), followed by a period.
   ){2}       End of Sub-Parenthesis, Match it twice (ie:  "anything.anything." )
   .+?        Match any character 1+ times (non-greedy)
)             End of Parenthesis $1
\..*          Match a period, followed by anything 0 or more times.
$             Match end of line

```

So if we have:
```
anything.anything.txt.nowant.nowant
```
This will match:
```
^((anything.anything.)txt).nowant.nowant$
```
And returns $1,which is:
```
anything.anything.txt
```

Regards
Iain

Thanks for the reply. That explanation helps a lot.

---

