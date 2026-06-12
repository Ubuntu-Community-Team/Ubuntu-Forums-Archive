---
title: "bash parameters and regular expressions"
date: 2009-07-11
forum: General Help
---

### Post by motoperpetuo on 2009-07-11
i'm writing a script, and i'm using the following code to verify that the user entered two parameters when invoking the script, no more and no less:
```

if [ ! $# -eq 2 ]
then
    echo "Please enter two paramters."
    exit 11
fi

```
thing is, i'm trying to let the user use * as a wildcard in the parameters. if the user enters this, for example:
```

./ren.sh *.txt *.bk

```
bash interprets every filename in the present working directory with a .txt extension as a parameter to the script. that is, if i have even one filename in the pwd with a .txt extension, i end up with three parameters and my script exits when it encounters the code above.

is there any good way to make bash stop seeing files in the pwd when i use a * in my script parameters? i've tried 'set -f' to turn off globbing at the start of the script, but that doesn't seem to do the trick.

---

### Post by Brandon Williams on 2009-07-11
There's nothing you can do in your script, since the * will have been interpretted and expanded by the command line interpreter before it ever executes your script.

Your primary options are either to require that the user quote or escape globbing patterns, or to use some special character sequence (e.g. "{}") to represent the globbing code and then replace it inside of the script. The command lines for these two options would end up looking like these:
```
option 1: ./ren.sh \*.txt \*.bk
option 2: ./ren.sh {}.txt {}.bk
```

---

### Post by motoperpetuo on 2009-08-09
> **Brandon Williams said:**
> There's nothing you can do in your script, since the * will have been interpretted and expanded by the command line interpreter before it ever executes your script.

Your primary options are either to require that the user quote or escape globbing patterns, or to use some special character sequence (e.g. "{}") to represent the globbing code and then replace it inside of the script. The command lines for these two options would end up looking like these:
```
option 1: ./ren.sh \*.txt \*.bk
option 2: ./ren.sh {}.txt {}.bk
```

sorry, i never said thanks for this info. i ended up using the @ symbol as a wildcard in my script. it worked fine. thanks!

---

