---
title: "bash script help"
date: 2009-08-31
forum: General Help
---

### Post by vttay03 on 2009-08-31
Alright guys here's the deal - I often run this sequence of commands from the shell over and over:

```

pgrep conky
kill <insert PID from previous command>

```

Conky was just used as an example here - I use pgrep a lot to determine PIDs for different processes.  What's the easiest way to combine these two commands into a single line, or how can I combine the two into a bash script?

---

### Post by NoaHall on 2009-08-31
Why not just use 
```

killall conky

```

---

### Post by loomsen on 2009-08-31
foo=`pgrep $1`
for $foo; do kill -9 $foo; done

make a little script with something like the above and place it in ~/bin.

But it's probably easier using pkill ^^ which does exactly that.

---

### Post by vttay03 on 2009-08-31
thanks - both of these suggestions were exactly what i had in mind.

---

### Post by Gen2ly on 2009-08-31
I always like using 'pkill process'.

---

