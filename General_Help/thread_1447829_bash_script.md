---
title: "bash script"
date: 2010-04-05
forum: General Help
---

### Post by neiljansons on 2010-04-05
I am trying to write a bash script to output to a tab delimited .csv file.
But I can't figure out how to insert the tabs.
I tried searching and nothing I found seemed to work
I know that in a terminal session I can do Ctrl-V and then tab to insert a tab there but I can't see how that is relevant to a bash script.
I tried all sorts of combinations of \t and ^I but I am obviously missing something.

```

#!/bin/bash

ttab=$'\t'

var1="blah"
var2="blah2"
var3="blah3"
var4="blah4"

echo $var1$ttab$var2$ttab$var3$ttab$var4 > test.csv

```

The above only inserts a space in between the variables rather than a tab.

---

### Post by mickObrian on 2010-04-05
You have to put it as 'echo -e <text>'.

---

### Post by cjhabs on 2010-04-05
> **neiljansons said:**
> I am trying to write a bash script to output to a tab delimited .csv file.
But I can't figure out how to insert the tabs.
I tried searching and nothing I found seemed to work
I know that in a terminal session I can do Ctrl-V and then tab to insert a tab there but I can't see how that is relevant to a bash script.
I tried all sorts of combinations of \t and ^I but I am obviously missing something.

```

#!/bin/bash

ttab=$'\t'

var1="blah"
var2="blah2"
var3="blah3"
var4="blah4"

echo $var1$ttab$var2$ttab$var3$ttab$var4 > test.csv

```

The above only inserts a space in between the variables rather than a tab.

```

echo -e text'\x09'text

```

---

### Post by neiljansons on 2010-04-05
Thanks cjhabs
That did the job
It was the -e that made the difference
Obviously now I can use either \t or \x09 now that I know how to escape it.

```

#!/bin/bash

ttab='\x09'

var1="blah"
var2="blah2"
var3="blah3"
var4="blah4"

echo -e $var1$ttab$var2$ttab$var3$ttab$var4 > test.csv

```

---

### Post by mickObrian on 2010-04-05
I wish I knew it was the -e that made the difference.

---

### Post by neiljansons on 2010-04-05
Mick
You may have known that the -e made the difference but you didn't put it together.

all you said was 
> You have to put it as 'echo -e <text>'.
which wasn't able to help me on its own.

cjhabs was able to make the connection of the -e with the \t

thanks for trying anyway

---

