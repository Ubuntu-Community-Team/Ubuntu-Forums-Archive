---
title: "Question regarding terminal scripts"
date: 2010-05-19
forum: General Help
---

### Post by Hawk666 on 2010-05-19
I've been trying to find out how to use a user defined variable as an argument but can't seem to find anything. Basically what I want to do is ask the user for something then execute a given command using that something as an argument, I'm sure it's very simple but unfortunately the only programming experience I really have is HTML and a little VB.

---

### Post by ryan858 on 2010-05-19
You can use ***read*** to ask the user to input data into a variable. Then you can use *$<variable>* to call the variable. It can be used anywhere in a script, even within quotes.
[I]
Example:[/I]
```

#!/bin/bash

echo "What is your name?"
read name
echo "Your name is $name"


```I'll leave other implications, besides than telling a user his name, up to you to figure out.

You could also do:
```

#!/bin/bash

echo "What is your name?" && read name &&
echo "Your name is $name"

```**&&** basically just checks that the previous command exited with 0 (no errors) before going on to the next command. **||** is the opposite and checks that it exited with non-zero status (error) before going on. If the criteria aren't met then it exits.



As a matter of fact, just in the process of making this post, I used ***read*** to make a script to make template scripts for me.
```

#!/bin/bash

cp "/home/ryan/Templates/Shell Script" . &&
echo "
Enter a filename for your new script: " && read name &&
mv "Shell Script" $name &&
gedit $name &&
echo "
The new script has been created successfully.
"


```

---

### Post by Hawk666 on 2010-05-19
ah thats what i was doing wrong silly me, i was doing "read $variable" thanks alot

---

### Post by ryan858 on 2010-05-20
Yeah, I made that mistake my first time. I just got lucky and figured out that $ denotes a pre-defined variable is to be called. So I figured that *read $variable* would only call a non-existent variable into *read*, which would do nothing. Although maybe you can use *read $variable* to modify an existing variable... I'm going to try that real quick...

Nope. Never mind.

---

