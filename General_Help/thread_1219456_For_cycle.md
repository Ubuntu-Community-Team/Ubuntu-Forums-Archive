---
title: "For cycle"
date: 2009-07-21
forum: General Help
---

### Post by Pigkappa on 2009-07-21
I am trying to make a simple script using the command "for". I have found this example:

#!/bin/sh

for (( X=0; X<10; X++ ))
do
   echo $X
done

But it doesn't work (the error is "./6.sh: 3: Syntax error: Bad for loop variable"). I also found an example with the command "while":

#!/bin/sh

X=0

while [$X -le 5]
do
   echo $X
   X=`expr $X + 1`
done
And this doesn't work either. I found both of them on the page [http://www.mrwebmaster.it/linux/guide/cicli-for-while_267.html](http://www.mrwebmaster.it/linux/guide/cicli-for-while_267.html) (in Italian). All of the previous examples I tried were fully working. What is wrong with the two of these?

Thanks for your help. I'm not sure this is the right place for this thread, I just hope so.

---

### Post by t4thfavor on 2009-07-21
```

#!/bin/bash

for((x=0; x<10; x++))
do
        echo $x;
done;

```

Check this out.

[http://www.cyberciti.biz/faq/bash-for-loop/](http://www.cyberciti.biz/faq/bash-for-loop/)

---

### Post by Rocket2DMn on 2009-07-21
While the code the OP posted may be valid Bourne code, it needs to be noted that /bin/sh in Ubuntu is not Bourne - it is Dash.  It is a very condensed version of Bourne that doesn't have 100% backward compatibility.  For more reading, see [uwiki]DashAsBinSh[/uwiki].

I don't have access to a machine with real Bourne on it (like Solaris) right now to test out the original code snippet, sorry.

---

### Post by t4thfavor on 2009-07-21
Totally correct, that code does not work in /bin/sh However, it does work in bash.

Maybe you could try a 
```

for $x in $arraylist

do

```

---

