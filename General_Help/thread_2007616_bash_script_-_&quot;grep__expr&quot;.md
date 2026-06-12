---
title: "bash script - &quot;grep | expr&quot;"
date: 2012-06-21
forum: General Help
---

### Post by sixteenornumber on 2012-06-21
:::EDIT::: if you are new to the thread, please start reading from my next post.

I using a "grep -c" to get the total number of hits.  unfortunately i need this number divided by 3.  How do I take the output from grep -c and run it through expr? I imagine the end product would look something like this.

```
#!/bin/csh  
/home/usr/.config/queue.22876 | grep -c /pool1/  ??? 
expr  ???  \/ 3 
```

---

### Post by Lars Noodén on 2012-06-21
Would this do it?

```

#!/bin/sh  
[s]A = $(/home/usr/.config/queue.22876 | grep -c /pool1/)[/s]
A = $(grep -c /pool1/ /home/usr/.config/queue.22876)
expr  $A \/ 3

```

Also, unless you have a special reason for using csh, it would be better to use sh:

[http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/](http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/)
[http://www.grymoire.com/Unix/CshTop10.txt](http://www.grymoire.com/Unix/CshTop10.txt)

---

### Post by kuifje09 on 2012-06-21
What to think of bash ....

try this and you see what I mean : 

echo $(( $( grep -c '/home' < /etc/passwd ) / 3 ))

---

### Post by dcottingham on 2012-06-21
I believe this works in either csh or bash:

expr `/home/usr/.config/queue.22876 | grep -c /pool1/` / 3

And I don't see any need to escape the /.

---

### Post by sisco311 on 2012-06-21
The title says bash, but you seam to use csh. In csh, I'd try something like:
```

set nr=`command | grep -c PATTERN`
@ nr = $nr / 3
printf '%d\n' "$nr"

```

---

### Post by sixteenornumber on 2012-06-21
> **sisco311 said:**
> The title says bash, but you seam to use csh...


sorry i had a few typos it should have been bash like the subject said. I don't have hardly and exp in scripting.

im still getting an error on line9, allow me to copy-pasta the entire script to clear everything up. 

```
#!/bin/bash
var1=a
while [ $var1 == a ]
do
     clear
     tail -n 50 /home/poop/.config/ghb/Activity.log.22876
     echo " "
     date
     a = $(more /home/poop/.config/ghb/queue.22876 | grep -c /pool1)
     expr $a \/ 3
     echo "files left in que..."
     sleep 20
done

```

---

### Post by markbl on 2012-06-22
I wont bother running this but by observation you need to remove the spaces around "=" in that "a = $(..." line.

Also, as said above, you don't need that expr rhubarb in modern bash.

E.g. just use
```

echo "There are $((a/3)) files left .."

```

---

### Post by dcottingham on 2012-06-22
I'm slightly concerned about the "more" in line 9. I'm not sure what "more" does in this context -- I think you wanted "cat". And grep doesn't need to read from stdin, so the line could be

a=$(grep -c /pool1 /home/poop/.config/ghb/queue.22876)

---

### Post by sisco311 on 2012-06-22
> **dcottingham said:**
> I'm slightly concerned about the "more" in line 9. I'm not sure what "more" does in this context -- I think you wanted "cat". And grep doesn't need to read from stdin, so the line **should** be

a=$(grep -c /pool1 /home/poop/.config/ghb/queue.22876)

fixed :)

more is a pager like less, most or pg. It displays text files. If its standard  output is not a terminal, more acts like cat(1) but precedes each file with its name if there is more than one.

In this light, I would like to redirect the OP to the following page: [http://partmaps.org/era/unix/award.html](http://partmaps.org/era/unix/award.html) :p

---

