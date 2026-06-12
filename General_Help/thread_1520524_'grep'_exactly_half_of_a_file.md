---
title: "'grep' exactly half of a file?"
date: 2010-06-29
forum: General Help
---

### Post by rifak on 2010-06-29
hey everyone,
so i have a data file of a couple thousand lines. for example, my file will look like this (condensed of course):

```

something something 100 something 1 2 3
something something 101 something 4 5 6 
something something 101 something 7 8 9
something something 102 something 10 11 12
something something 100 something -1 -2 -3
something something 101 something -4 -5 -6
something something 101 something -7 -8 -9 
something something 102 something -10 -11 -12

```

notice how the 100-103 start over at exactly half, but with different corresponding numbers. now, say i want to focus in on the lines that have the 101 attached. i want to grep the first 101's, output it to a file, then grep the second 101's and output it to a different file. also, i dont necessarily need to grep exactly half, because just greping the 'first' occurrence of something then outputting it to a file, then greping the 'second' occurrence of something then outputting it to a different file would also do the job. can this be done? thanks in advanced.

---

### Post by lukeiamyourfather on 2010-06-29
The command "wc" returns information about a file. The first number returned is the line count. Divide this by half and use it as an argument for "head" which returns the first ten lines of a file, or the number specified. It'll take some bash scripting to glue them together. For more info use "man" like "man wc" and "man head" to learn more about each command. There might be a native way to read just half a file but I'm not sure of one. Cheers!

---

### Post by amauk on 2010-06-29
```
#!/bin/bash

INPUT_FILE="/path/to/file"

IFS=$'\n'

NUM_LINES=$(cat "$INPUT_FILE" | wc -l)
MID_POINT=$(expr "$NUM_LINES" / 2)

TOP_HALF=$(cat "$INPUT_FILE" | head -$MID_POINT)
BOT_HALF=$(cat "$INPUT_FILE" | tail -$MID_POINT)

for ENTRY in $TOP_HALF; do
	# Do whatever processing you want
	# for first half of file
done

for ENTRY in $BOT_HALF; do
	# Do whatever processing you want
	# for second half of file
done
```

---

### Post by DaithiF on 2010-06-29
Hi, I think this may work:
```
sed -n '/101/,/101/p;/101/!q' testfile
```

---

### Post by DaithiF on 2010-06-29
gah, no it won't!

try this:
sed -n '/101/,$p' testfile | sed -n '/101/!q;p'

---

