---
title: "Bash shell help"
date: 2011-02-23
forum: General Help
---

### Post by michaelkhan3 on 2011-02-23
Im using an if statement in the bin ash shell and it isnt working.

```

if (( 5000 > $available_blocks  ))
then echo "WARNING Disk space low, "$pct_used" is used"
fi

```

I don't think its a problem with the if. When i use that code it creates a file with name of the value $available_blocks instead of using the '>' sign for comparing the 2 numbers.


Any help is appreciated.

---

### Post by Wtower on 2011-02-23
The if statement by itself is correct. I can think of two possible problems:

a. You have specified #!/bin/sh instead of #!/bin/bash

b. The $available_blocks variable is not properly set.

Apparently you have isolated a coorect part of your script. The following example code is correct:

```
#!/bin/bash
pct_used=1
available_blocks=1
if (( 5000 > $available_blocks  ))
then echo "WARNING Disk space low, "$pct_used" is used"
fi

```

---

### Post by gmargo on 2011-02-23
Or use portable shell syntax:
```

if [ 5000 -gt $available_blocks ] ; then
    echo "WARNING Disk space low, $pct_used is used"
fi

```

---

### Post by i.r.id10t on 2011-02-23
> **gmargo said:**
> or use portable shell syntax:
```

if [ 5000 -gt $available_blocks ] ; then
    echo "warning disk space low, $pct_used is used"
fi

```

+1

---

### Post by Wtower on 2011-02-24
> **gmargo said:**
> Or use portable shell syntax:
```

if [ 5000 -gt $available_blocks ] ; then
    echo "WARNING Disk space low, $pct_used is used"
fi

```

Correct, but the script's problem is not the if syntax.

---

### Post by michaelkhan3 on 2011-02-25
Thanks every one for your answers.

The problem I had was that I was running the program using the command 'sh file_info' instead of 'bash file_info'

---

### Post by WorMzy on 2011-02-25
That's a common mistake n Ubuntu. On debian-based systems "sh" is a symlink to the dash shell, which is somewhat different to the bash shell. It's best to make sure that you explicitly declare in the shebang (#!) which shell your script requires.

---

