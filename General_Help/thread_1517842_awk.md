---
title: "awk"
date: 2010-06-25
forum: General Help
---

### Post by ankit.vader on 2010-06-25
This may not be the right place to post this, but i really need help.

i have a file dconfig with following contents

Dimension=3
low1=1
low2=2
low3=3
high1=4
high2=5
high3=6

i want to separate low and high values, and store it in an array using shell. For this i used awk and did this
```

cat dconfig | grep 'high' | awk '{FS="="}{print $2}'

```
and the output i got is this

5
6

i cannot see '4'. same thing happens with low values. what is wrong?

---

### Post by ankit.vader on 2010-06-25
bump

---

### Post by Arand on 2010-06-25
> **ankit.vader said:**
> (snip)
```

cat dconfig | grep 'high' | awk '{FS="="}{print $2}'

```
(snip)

I've never come to terms with awk, but you could use something like this instead:```
cat dconfig | grep 'high' | cut -d "=" -f 2
```- arand

---

### Post by coslo on 2010-06-25
You forgot the BEGIN block. It shoud read

```
awk 'BEGIN{FS="="}{print $2}'
```

---

### Post by ankit.vader on 2010-06-25
```

awk 'BEGIN{FS="="}{print $2} 
```

thx a lot, that works. i always used to think that BEGIN is of no use. :)

---

### Post by bodhi.zazen on 2010-06-25
use the -f flag

cat | grep is poor forum, just grep

Wrong

cat file | grep bar

just

grep bar file

along those lines, no need to use grep with awk either ...

```
awk -F "=" '/high/ {print $2}' dconfig
```

---

### Post by coslo on 2010-06-25
> **ankit.vader said:**
> ```

awk 'BEGIN{FS="="}{print $2} 
```thx a lot, that works. i always used to think that BEGIN is of no use. :)

At some point you may also want to reconsider END{} ;) 
Cheers

---

