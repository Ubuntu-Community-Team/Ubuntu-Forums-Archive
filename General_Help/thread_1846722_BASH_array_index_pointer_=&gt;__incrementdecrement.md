---
title: "BASH array index pointer =&gt;  increment/decrement array[$i+1]"
date: 2011-09-19
forum: General Help
---

### Post by dragonetti on 2011-09-19
Sorry if this isn't the correct place to ask.
 
I am running an ubuntu VPS and I only have terminal access to it.
I am beginning to write scripts which is gradually going better and better.
 
But now I am really dumbfounded by this problem.
 
I want to access an array like this
 
```
 
myvar=${versionnumber[$i-1]}

```
 
But I keep getting the following error:
 
"bad array subscript"
 
Is it possible to access an array like this:
 
```
 
myvar=${versionnumber[$i-1]}

```
 
Or is there another way?
 
I also tried
 
```

x=$(( $i - 1 ))
versionnumber[$x]

```
 
 
Thank you

---

### Post by TeoBigusGeekus on 2011-09-19
It works here:
[PHP]#!/bin/bash
versionnumber=( 1 2 3 4 5 )
i=4
myvar=${versionnumber[$i-1]}
echo $myvar[/PHP]
Output:
[PHP]$ ./test
4
[/PHP]
Have you added the #!/bin/bash at the top your script?
Also, don't run it with
```
/path/scriptname
```
but with
```
bash /path/scriptname
```

---

### Post by sisco311 on 2011-09-19
"bad array subscript" means "index out of range" :)

$i-1 is too low or too high.

BTW, $i-1 is in an arithmetic context so you don't have to use $:
```
echo "${array[i-1]}"
```

---

### Post by TeoBigusGeekus on 2011-09-19
> **sisco311 said:**
> "bad array subscript" means "index out of range" :)

$i-1 is too low or too high.

BTW, $i-1 is in an arithmetic context so you don't have to use $:
```
echo "${array[i-1]}"
```

Exactly what I was saying...:biggrin:

---

### Post by dragonetti on 2011-09-20
OOOH!!
 
Thank you guys!!!!!

---

