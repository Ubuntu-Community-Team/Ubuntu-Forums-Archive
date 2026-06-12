---
title: "Bash parameters with-c switch ?"
date: 2011-03-11
forum: General Help
---

### Post by matt_symes on 2011-03-11
Hi

From the man page for bash...

> -c string 

If the -c option is present, then commands are read from string. If  there are arguments after the string, they are assigned to the positional parameters, starting with $0.

```
matthew@matthew-laptop:~$ bash -c "echo $0; echo $1; echo $2; echo $3" a b c
bash



matthew@matthew-laptop:~$ 
```

What am i missing here ? :confused:

Kind regards

---

### Post by TeoBigusGeekus on 2011-03-11
Try with single quotes.

---

### Post by matt_symes on 2011-03-11
Hi Teo

```
matthew@matthew-laptop:~$ bash -c "echo $0; echo $1; echo $2; echo $3" 'a' 'b' 'c'
bash



matthew@matthew-laptop:~$ 
```

I've tried double quotes as well

```
matthew@matthew-laptop:~$ bash -c "echo $0; echo $1; echo $2; echo $3" "a" "b" "c"
bash



matthew@matthew-laptop:~$ 
```

I have no idea what i am doing wrong here. ](*,)

Kind regards

---

### Post by TeoBigusGeekus on 2011-03-11
I meant
```
bash -c 'echo $0; echo $1; echo $2; echo $3' a b c
```

---

### Post by matt_symes on 2011-03-11
Hi

You, sir, are the man. That must have been the only combo i did not try (it was distilled from a must larger command i was trying to run).

Thanks again. :D

Kind regards

---

### Post by TeoBigusGeekus on 2011-03-11
You're welcome mate.
Bash is a bit tricky with subshells (or child shell if you prefer).
For an explanation, see this
[http://stackoverflow.com/questions/1711970/cant-seem-to-use-bash-c-option-with-arguments-after-the-c-option-string]("http://stackoverflow.com/questions/1711970/cant-seem-to-use-bash-c-option-with-arguments-after-the-c-option-string")

---

### Post by matt_symes on 2011-03-11
Hi

> **TeoBigusGeekus said:**
> You're welcome mate.
Bash is a bit tricky with subshells (or child shell if you prefer).
For an explanation, see this
[http://stackoverflow.com/questions/1711970/cant-seem-to-use-bash-c-option-with-arguments-after-the-c-option-string]("http://stackoverflow.com/questions/1711970/cant-seem-to-use-bash-c-option-with-arguments-after-the-c-option-string")

Thanks Teo. 

Thanks for the link as well because one of the things i was doing in the subshell was sed character replacement. 

That was why i was using double quotes. In the end i was able to escape the variables.

For anybody else interested....

```
matthew@matthew-laptop:~$ bash -c "echo \$0; echo \$1; echo \$2; echo \$3" a b c
a
b
c

matthew@matthew-laptop:~$ 
```

Once again, thanks a lot.

Kind regards

---

