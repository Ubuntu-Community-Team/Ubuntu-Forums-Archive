---
title: "Bash - Calling functions within functions and variables"
date: 2010-02-07
forum: General Help
---

### Post by bakegoodz on 2010-02-07
I have a bash script that has about 5 functions, for use with a menu. I have started to have about 12 lines of code that so far I need to duplicate about 3 times, I thinking about putting it into separate function. So I want to call a function within a function and still have the two variables (created inside the first function) with their data from the first function transferred to the called function. Any ideas or code examples?

Sorry I'm not quite ready to make my code public, since it's an good idea that I have yet to be see duplicated, and I feel protective of it. Yes it is working, I just want to make the bash code more efficient before everyone starts eye balling it. Also I want to released to the public via my own web site.

---

### Post by gmargo on 2010-02-08
You can pass multiple arguments to shell functions.  Try this shell script:
```

#!/bin/sh

greet3() {
   msg1=$1
   msg2=$2
   echo $msg1 $msg2
}

greet2() {
   msg=$1
   greet3 $msg "World"
}

greet1() {
   greet2 "Hello"
}

greet1

```

---

