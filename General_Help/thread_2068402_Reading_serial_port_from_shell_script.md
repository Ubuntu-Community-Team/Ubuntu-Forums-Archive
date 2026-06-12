---
title: "Reading serial port from shell script"
date: 2012-10-09
forum: General Help
---

### Post by stage1v8 on 2012-10-09
Hi Folks,

I am working on a project that has a microcontroller sending data via the serial port that I want to use in a shell script.  I can see the variable on screen using cat /dev/ttys1 but I want to take it a step further and use the data as variables in a shell script.

Can anyone point me in the direction of how this can be done?

The data consists of a string of 3 numbers every 30 seconds followed by EOL characters.  I want to have each of the numbers in a separate variable.

Cheers

J

---

### Post by HiImTye on 2012-10-09
if you can give us some sample output, then we can give you an idea of how to format it ;)

---

### Post by stage1v8 on 2012-10-09
Hi,

Its pretty basic. On screen it looks like

101921

This is the microcontroller sending 10 19 21 followed by ascii 13,10 for a new line. It does this every 30 seconds with the 3 values changing each depending on the sensors attached to the microcontroller.

I have complete control of the data thats sent so thinking that putting some delimiters in the string might help. Something like:

10,19,21

Cheers

J

---

### Post by dargaud on 2012-10-09
I'd be curious to see solutions written entirely in shell scripts as I've tried and failed to do this before. Using the stty command to configure the port is notoriously tricky and it's difficult to deal with input vs output vs communications errors in a script. 

Personally I'd recommend using C.

---

### Post by stage1v8 on 2012-10-09
> **dargaud said:**
> Personally I'd recommend using C.

Was hoping that it would be a bit longer before someone told me that :)

I may have to go down the C route or maybe a bit of python but would like to give shell scripting a go first if its going to be possible.

J

---

### Post by HiImTye on 2012-10-09
if you could set the output to an output such as:
```
var_a=##
var_b=##
var_c=##
```
then you could just make bash set them as variables like so:
```
. /dev/ttys1
```
otherwise you could use sed to sort them into variables like:
```
cat /dev/ttys1 | sed 's|^\([0-9][0-9]\)\([0-9][0-9]\)\([0-9][0-9]\)|var_a=\1\nvar_b=\2\nvar_c=\3|' > out.txt
. out.txt
```

which will produce output in the fashion of:
```
tye@T:~$ echo 'var_a=12
var_b=34
var_c=56' > out.txt
tye@T:~$ . out.txt
tye@T:~$ echo $var_a $var_b $var_c
12 34 56
```

anyway, then you just need a loop such as:
```
while :; do
 sleep 29.999 # sleep for just under 30 seconds, to account for system hiccups.
 cat /dev/ttys1 | sed 's|^\([0-9][0-9]\)\([0-9][0-9]\)\([0-9][0-9]\)|var_a=\1\nvar_b=\2\nvar_c=\3|' > out.txt
 . out.txt
 script_containing_other_instructions.sh $var_a $var_b $var_c &
done
```

---

### Post by stage1v8 on 2012-10-15
Hi,

Thanks for suggestions.  After much messing around I have finally got the output from cat /dev/ttys1 to be:

var1=13
var2=16
var1=13
var2=16

When I try to use ". /dev/ttys1" I get:

root@temp:~# . /dev/ttys1
var2=13: not foundline 2:
var1=16: not foundline 3:
var2=13: not foundline 4:

Any suggestions?

Cheers

J

---

