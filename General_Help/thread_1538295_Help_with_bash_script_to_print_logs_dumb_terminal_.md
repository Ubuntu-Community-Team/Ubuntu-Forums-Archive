---
title: "Help with bash script to print logs dumb terminal style"
date: 2010-07-24
forum: General Help
---

### Post by Daemonite on 2010-07-24
Even though I suppose this isn't Ubuntu exclusive, I hope its an ok place for this question.

I am trying to find a way to display log files in the way that tail -f does but have it print character by character and play a tiny wav file for each character. The idea that this would resemble hollywood movie computers.

So far I have this:

```

#!/bin/bash
# data file
if [ "$1" != "" ]; then
    INPUT="$1"
else INPUT=/var/log/messages
fi 
while IFS= read -r -n1 char
do
    echo  -n "$char"
    sleep .05
    aplay -q -N scroll.wav &
done < "$INPUT"

```There are several problems with it. Most formatting gets stripped out, mainly newline, so it all runs together. Also, it quits at the end of the file, I am not sure how I could make this function like tail -f, where if new information is added to the file it would show on screen.

I appreciate any help.

---

### Post by DaithiF on 2010-07-25
Hi,
1. the problem with the newline is that although you're telling read to read 1 character at a time, read itself has still read the full line and effectively discarded the newline at the end (while delivering you one character at a time from that line)
so to keep newlines in your output you'll need two loops, one to read one line at a time, and an inner loop to output each character in that line, and after each inner loop you output a new line yourself.

so:
```
IFS=
while read line
do
  echo "$line" | while read -r -n1 char
  do
     echo -n "$char"
     # etc...
  done
  echo
done < $INPUT
```2. For continually reading the input, easiest to just use tail -f in your script, so:
```
done < <(tail -f "$INPUT")
```the complete script looking like:
```
#!/bin/bash
# data file
if [ "$1" != "" ]; then
    INPUT="$1"
else INPUT=/var/log/messages
fi 
IFS=""
while read line
do
    echo "$line" | while read -r -n1 char
    do
        echo -n "$char"
        sleep .05
        aplay -q -N scroll.wav &
    done
    echo
done < <(tail -f "$INPUT")

```

---

### Post by Daemonite on 2010-07-25
Thank you very much! I never thought about how read would read the line then process it like that.

I had tried something like you put for the tail -f, but apparently didn't have it quite right.

Thanks again. Works perfectly.

---

