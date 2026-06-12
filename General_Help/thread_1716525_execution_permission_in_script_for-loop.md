---
title: "execution permission in script for-loop"
date: 2011-03-28
forum: General Help
---

### Post by worldsayshi on 2011-03-28
I'm trying to create a script that executes the same executable with a list of input files from a given folder with a certain file extension. But executing inside a for-loop seems to cause problems. Below, JLc is my executable, .jl is the file extension I want to pick and my files are in testsuite/good/ 

This script (myTester):
```
#!/bin/sh
set -e
make bnfc
#./JLc testsuite/good/core001.jl
for i in $(testsuite/good/*.jl)
do 
        ./JLc $i
done
```

Gives this output:

```
./myTester: 8: testsuite/good/core001.jl: Permission denied
```

But if I uncomment "#./JLc testsuite/good/core001.jl" above and comment out the for loop it works fine. 
Why is this and how do I give executable permissions inside the loop?

PS: Replacing ./JLc with echo gives the same error.

---

### Post by worldsayshi on 2011-03-28
Ah. Reworking the for loop "header" solved this:
Changed "for i in $(testsuite/good/*.jl)" 
to
"for i in testsuite/good/*.jl"

Although I don't really see "why" this worked I set this to solved.

---

### Post by pl@yer on 2011-03-30
> **worldsayshi said:**
> Ah. Reworking the for loop "header" solved this:
Changed "for i in $(testsuite/good/*.jl)" 
to
"for i in testsuite/good/*.jl"

Although I don't really see "why" this worked I set this to solved.

It's because $() means execute what commands between the braces and the results are what is returned. 

So it will attempt to execute each file testsuite/good/*.jl and the result of each execution will be $i for the loop. 

this would also have worked
```

for i in $(ls testsuite/good/*.jl)

```

---

### Post by worldsayshi on 2011-03-31
I see. Thanks!

---

