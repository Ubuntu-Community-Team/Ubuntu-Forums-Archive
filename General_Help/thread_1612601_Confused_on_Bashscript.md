---
title: "Confused on Bashscript"
date: 2010-11-03
forum: General Help
---

### Post by Lamez on 2010-11-03
I am working on this
```

#!/bin/bash

ask(){
	clear;
	echo "M to mount, U to unmount: \c"
	read x
	return $x;
}

if [ask == m*]; then
	echo "mount command"
elif [ask == u*]; then
	echo "unmount"
else
	ask
fi

```

I have tried reading some tutorials on this, cannot figure it out. Can you guys help?

I think it is pretty obvious on what I want it to do.

---

### Post by blur xc on 2010-11-03
I did some quick research and found that you can only return an integer from 0 - 255 from a bash function (I'm more than ready to be corrected though).  A function appears (layman's udnerstanding) to run like a mini script.  All scripts (or commands in bash, I guess) return an exit value after running.  You can see this exit value by entering echo $? after running any shell command.  Normally, 0 is the "it all ran ok w/o errors" exit code.  So, if I were to guess, you'd need to change your code to something like "Enter a 0 for mount, or 1 for unmount" or add a few lines to your function like if m then y = 1, else y = 0 type statements, and return y....  

I hope that makes sense.

BM

---

### Post by Lamez on 2010-11-03
I know what a function is. I am just trying to get my if block to work. I have ammended my code to this:
```

#!/bin/bash
echo "1 to mount, 0 to unmount: \c"
read x


if ("$x" == 1); then
	echo "mount command"
elif ("$x" == 0); then
	echo "unmount"
else
	echo "Unknown input"
fi

```

Now I get something like this in my output:
> 
test: 12: 1: not found
test: 12: 1: not found


---

### Post by rifak on 2010-11-03
this works for me:

```

#!/bin/bash
echo "1 to mount, 0 to unmount: \c"
read x


if [ "$x" == 1 ]; then
	echo "mount command"
elif [ "$x" == 0 ]; then
	echo "unmount"
else
	echo "Unknown input"
fi

```

you need square brackets for your if argument. also, a space after and before the square brackets is needed.

---

### Post by Lamez on 2010-11-03
When I try running what you have I get this:
```

lamez@studio:~/Desktop$ sh test
1 to mount, 0 to unmount: 1
[: 12: 1: unexpected operator
[: 12: 1: unexpected operator
Unknown input

```

---

### Post by Lamez on 2010-11-03
I got it with this:
```

#!/bin/bash
echo "1 to mount, 0 to unmount: \c"
read x


if [ "$x" = 1 ]; then
	echo "mount command"
elif [ "$x" = 0 ]; then
	echo "unmount"
else
	echo "Unknown input"
fi

```

---

### Post by blur xc on 2010-11-03
Also this works for me:

```
#!/bin/bash
echo "1 to mount, 0 to unmount: \c"
read x


if [ $x  -eq 1 ]; then
    echo "mount command"
elif [ $x -eq 0 ]; then
    echo "unmount"
else
    echo "Unknown input"
fi
```

BM

---

