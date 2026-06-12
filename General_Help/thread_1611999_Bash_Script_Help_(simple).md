---
title: "Bash Script Help (simple)"
date: 2010-11-02
forum: General Help
---

### Post by steevven1 on 2010-11-02
I am writing a bash script, and I need a way to have "if" check if a command returned any output or no output at all. That's all I need the conditional to be.

For example, I'd like to execute some command IF "grep string somefile" returns anything at all, but not to execute the command if the grep returned nothing.

Explanations of what the commands you use mean would be very helpful, rather than just an "answer."

Thanks in advance!

---

### Post by cgroza on 2010-11-02
I don't know bash, but i know python. You could assign the command to a vaiable and  then check if its empty or not. 

$variable = command
if variable == ""
#do something

---

### Post by Miyavix3 on 2010-11-02
If you wrote it in python it would look something like this...

```

from os import system
x = system("ls | grep "string")
if x != "":
    print x

```

replace what's in system() with whatever you want to run.

Edit: I just tried this, and apparently if grep yields no results, it gives 256.

So I suppose you can do this

```

from os import system
x = system("ls | grep "string")
if x != 256:
    print x

```


On second thought, maybe you should do this in bash.

---

### Post by steevven1 on 2010-11-02
Yeah...I have to do this in bash. Thanks for the suggestion anyway though.

---

### Post by gsgleason on 2010-11-02
how about this:

```
if [[ -n "`command`" ]]; then
  echo "string has nonzero length"
else
  echo "string has zero length"
fi
```

read man page for "test" for more.
-z means string length is zero.  
-n means string length is non-zero.

those things around the command are back ticks, under the tilde.  IT will be equal to the standard output of whatever command(s) are within.

---

### Post by steevven1 on 2010-11-02
> **gsgleason said:**
> how about this:

```
if [[ -n "`command`" ]]; then
  echo "string has nonzero length"
else
  echo "string has zero length"
fi
```read man page for "test" for more.
-z means string length is zero.  
-n means string length is non-zero.

those things around the command are back ticks, under the tilde.  IT will be equal to the standard output of whatever command(s) are within.


Perfect! Thanks!

---

