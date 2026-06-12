---
title: "bash help - if causes error"
date: 2011-07-22
forum: General Help
---

### Post by SeaKing on 2011-07-22
I tried to write a little bash script but the if condition makes problems somehow (it's slightly different from the syntaxes I'm familiar with).

The basic synatx is (the internet told me)

```
if [ condition ]; then
  do something
else
  do something
fi
```my code is now:

```

[line 1] #! /bin/bash
[line 3] read_current_iso=$(head -n 1 /home/virtual/Documents/PXE_ISOs/.current_image)
[line x] #some other stuff
[line 18]if[ -s $read_current_iso ]; then
[line 19]        echo $read_current_iso
[line 20]else
[line 21]        echo 'currently no image mounted'
[line 22]fi


```error report if the file is empty:
```

testbash.sh: 18: if[: not found

testbash.sh: 20: Syntax error: "else" unexpected

```error report if the file is filled:
```

testbash.sh: 18: if[: not found
content written in the file on line 1

```

---

### Post by diesch on 2011-07-22
There needs to be a space before the "*[*".

---

### Post by mcduck on 2011-07-22
You are missing a space between the if and the square bracket. Without the space, Bash thinks you are trying to execute a command "if[" and then complains that such thing doesn't exist.

---

### Post by SeaKing on 2011-07-22
Thanks and I've just read about how important spaces are :roll:

---

### Post by matt_symes on 2011-07-22
Hi

Don't use the inbuilt [ (test) command for a Bash shell. Use [[ and ]].

Read the Bash links in my signature for an explanation why.

Kind regards

---

### Post by SeaKing on 2011-07-22
and how would it looks like?

#! /bin/bash 
read_current_iso=$(head -n 1 /home/virtual/Documents/PXE_ISOs/.current_image)
#some other stuff [line 18]
if [[$read_current_iso != "" ]]; then 
echo $read_current_iso
else
echo 'currently no image mounted' 
fi

---

### Post by nothingspecial on 2011-07-22
> **SeaKing said:**
> and how would it looks like?

#! /bin/bash 
read_current_iso=$(head -n 1 /home/virtual/Documents/PXE_ISOs/.current_image)
#some other stuff [line 18]
if [COLOR="Red"][[$read_current_iso != "" ]][/COLOR]; then 
echo $read_current_iso
else
echo 'currently no image mounted' 
fi

No. It is important to understand that [[ is a command just like ls or cd or any other. It needs a space after it otherwise bash will think you are trying to run [[$read_current_iso rather than [[ with $read_current_iso as it's first argument.

While we are here, you should always quote your variables.

---

### Post by SeaKing on 2011-07-22
> **nothingspecial said:**
> 
While we are here, you should always quote your variables.

#! /bin/bash 
[COLOR=Red]READ_CURRENT_ISO=$(head -n 1 /home/virtual/Documents/PXE_ISOs/.current_image)[/COLOR]
#some other stuff [line 18]
if [[ [COLOR=Red]$READ_CURRENT_ISO[/COLOR] != "" ]]; then 
echo [COLOR=Red]$READ_CURRENT_ISO[/COLOR]
else
echo 'currently no image mounted' 
fi

and the feedback is, that [[ is unknwon ?!

the result I want to have with this condition is if the file is not empty the condition should be true

---

### Post by nothingspecial on 2011-07-22
Works for me
```

$ READ_CURRENT_ISO=blah
$ if [[ $READ_CURRENT_ISO != "" ]]; then echo $READ_CURRENT_ISO; else echo 'currently no image mounted'; fi
blah
$ READ_CURRENT_ISO=
$ if [[ $READ_CURRENT_ISO != "" ]]; then echo $READ_CURRENT_ISO; else echo 'currently no image mounted'; fi
currently no image mounted
$ 
```

I can't see what you are doing wrong, maybe I'm missing something.

---

