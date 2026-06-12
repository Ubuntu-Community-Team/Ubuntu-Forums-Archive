---
title: "confusing bash behavior"
date: 2010-09-02
forum: General Help
---

### Post by d3v1150m471c on 2010-09-02
I have 2 files. the first file echo's a line in the second file. each line in the second file is an ascii character. it looks something like this

```

a
b
c
d
e
f
g
!
@
#
$
%
&
*

```the problem is whenever my first file, the executable hits the "%" character in file 2, instead of printing the character it prints all the files in my home directory...:)

here is the first file. can someone tell me what I am doing wrong? Thanks in advance

```

#!/bin/bash
export NUM="1"

QWERTY() {
while
  if [ $NUM -lt 93 ]; then
      echo `head -"$NUM" characters | tail -1`
      NUM=`expr $NUM + 1`
  else
      echo `head -"$NUM" characters | tail -1`
      NUM="1"
  fi
do
  sleep .0001
done
}

QWERTY


```

---

### Post by d3v1150m471c on 2010-09-02
i'm an idiot. it was an '*', not a '%' lol
found a way around it though

---

