---
title: "Simple Simple Script Help"
date: 2010-03-10
forum: General Help
---

### Post by FerretDefunct on 2010-03-10
I'm tinkering with scripts and learning the basics, I'm looking for one to generate a user list. Basically want I want it to do is accept an argument passed to it (user's name) and then take the first letter of the first name ($1) and the full last name ($2), convert them to lower case and combine them. I then want it to generate a numbered list of like 5 numbered names. In the end I wanted it to look like this work like this...

(Input)

$ myScript.sh User Name

(Output)

User: uname1
User: uname2
User: uname3
User: uname4
User: uname5

So far I've got it working to do the combination and lowering the case, but I'm stuck on generated the number list. Here's my script so far:

```

#!/bin/bash

a=$( echo $1 | cut -c1)

echo "User: ${a,}${2,,}"

```

---

### Post by DaithiF on 2010-03-10
Hi,
```
for i in {1..5}
do
echo name$i
done
```

---

### Post by FerretDefunct on 2010-03-10
Worked like a charm, thanks!

How would I go about generating a set number based on the argument passed in?

Say for example the input like:

$ myScript.sh User Name 6

Then have it do the same output but do 6 (or whatever number is passed to it in the command).

---

### Post by FerretDefunct on 2010-03-10
I tired doing:
```

for i in {1..$3}
```
...but no dice.

---

### Post by FerretDefunct on 2010-03-10
Got it:
```

for (( i = 1; i <= $3; i++ ))
```

---

### Post by DaithiF on 2010-03-10
Hi,
try
```
for i in $(seq 1 $3)
do
echo $i
done

```

---

