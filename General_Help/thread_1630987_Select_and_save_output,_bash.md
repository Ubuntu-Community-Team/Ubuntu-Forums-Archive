---
title: "Select and save output, bash"
date: 2010-11-26
forum: General Help
---

### Post by filipwa on 2010-11-26
I am writing a script where I need to save one specific line to a file. The output from the program I am running consist of several thousands of lines but I only need the last one. 

See example below:

ITER   RES   LIFT    DRAG      MOMENT
949    -5.48 0.553   0.00431   0.0253
950    -5.50 0.553   0.00432   0.0253 
SAVING RESIDUALS: "data.res"
CONVERGENCE REACHED.

The only unique line here is the one saying "CONVERGENCE REACHED" and the one I need to select and save is the one two lines above it.

Would it be possible to use "grep" to select that line? In that case what syntax should be used? If that is not possible how should it be done?

Suggestions are much appreciated!

---

### Post by Paddy Landau on 2010-11-26
You don't make clear how you know which line to save. Is it always the third line from the bottom? Or the last line starting with '9'? What are the criteria?

---

### Post by filipwa on 2010-11-26
It is not the third line form the bottom, it is the 2nd line form the line CONVERGENCE REACHED... (There are a lot of other information displayed after that line)
The calculation converges after a different number of iterations every time.

---

### Post by Paddy Landau on 2010-11-26
This will require some programming. The basic structure would be as follows (I've thrown this together, so you'll need to do the testing and adjusting as needed).
```
#!/bin/bash

LINE1=''                                             # One line back.
LINE2=''                                             # Two lines back.

yourfancyprogram |                                   # Run your program and pipe it to a set of commands.
    while read LINE                                  # Read the next line.
    do
        if [[ ${LINE} == 'CONVERGENCE REACHED.' ]]   # Test for the end point.
        then
            echo "${LINE2}" >placetosave.txt         # Save two lines back.
            break                                    # Finished searching.
        fi
        LINE2="${LINE1}"                             # Move the line back.
        LINE1="${LINE}"                              # Save the new line.
    done

cat placetosave.txt                                  # Echo the line found.
```

---

### Post by filipwa on 2010-11-26
Thanks, it works like a charm!
You really saved my day ;)

---

### Post by DaithiF on 2010-11-26
grep does this kind of thing rather easily:
```
yourprogram | grep -B 2 "CONVERGENCE REACHED" | head -1

```

or if you want to roll your own solution, awk would be a good candidate:
```
yourprogram |  awk '{line[NR]=$0} /CONVERGENCE REACHED/ { print line[NR-2] }'
```

---

### Post by Paddy Landau on 2010-11-26
> **DaithiF said:**
> grep does this kind of thing rather easily:
Hey, that's cool! Much better than my solution.

---

