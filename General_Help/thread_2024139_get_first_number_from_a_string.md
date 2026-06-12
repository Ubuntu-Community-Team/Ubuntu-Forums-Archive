---
title: "get first number from a string"
date: 2012-07-13
forum: General Help
---

### Post by sd@ksu on 2012-07-13
I have a string like this suppose"
> 8 bla bla bla..
or
> 88 bla bla bla..
.................
Now I want to take out only the number out from that string. As you can see, head would not always work as the number in first place can be either 8,88,888,8888 etc. Is there a simple way out. I do not want to use 
```
awk '{print $1}'
``` 
and there is a reason for it. Can anyone help me out please? if there is a way i can pass the whole string to a variable or some function and then it will just return me the first part which is the number or before the white space..

---

### Post by Vaphell on 2012-07-13
```
$ x='333 bla bla bla'
$ echo ${x%% *}
333
$ echo "$x" | cut -d' ' -f1
333
$ echo "$x" | grep -o '^[0-9,.]*'
333
$ echo "$x" | sed -r 's/^([0-9,.]+).*/\1/'
333

```

---

### Post by mbeach on 2012-07-13
EDIT: nope, nevermind. Didn't read carefully enough.

---

### Post by Kopkins on 2012-07-13
Should be able to do this.

Example script:
```
 #/bin/bash
stringX=12345abcde

echo ${stringX:0:1}

exit

```

This is in the format: ${string:position:length}

That script above should yield the number 1. 

Have a look [here]("http://tldp.org/LDP/abs/html/string-manipulation.html").

Best of luck,
Kopkins

---

### Post by sisco311 on 2012-07-13
```

$ foo="8,888"$'\t'"blahh lasd sdfsdfsd"
$ printf '%s\n' "$foo"
8,888	blahh lasd sdfsdfsd
$ printf '%s\n' "${foo%% *}"
8,888	blahh
$ printf '%s\n' "${foo%%[[:blank:]]*}"
8,888 

```

---

### Post by steeldriver on 2012-07-13
well I don't see why you wouldn't want to use awk, but fwiw you could do the same in sed (print anything up to the first whitespace):

```
sed -rn 's/(^[^ \t]+)(.*$)/\1/p'
```or I think you could convert your string to an array in bash (using the default IFS which includes space and tab) and then get the first element of the array:

```
array=($string)

echo ${array[0]}
```

---

### Post by sd@ksu on 2012-07-13
Let me tell you the reason why i do not want to use awk..I have tried sed also..but did not work..
I have a data file, where each set of data starts with a string like this:
> #S number any-string 
Then the data follows. Now I use another program inside which I am doing all these..like getting that number and pass it on. That program has a cute little tool to invoke unix commands in this format:
> unix("cmd") or u cmd
...
That program uses macros which are written in this format: 
> a-macro ' commands '
...............
Now to do anything with single and double quotes I get in trouble and It seems I am a bit limited. THIS IS THE CONSTRAINT ON THE SITUATION.
e.g., I can write a bash script (NAME of script: **a-boring-test**) like (I have been trying these options for long time, long before I posted here): 
```
#!/bin/bash
function f1()
{
local _val1 _val2 _val3 _val4
_val1=$(grep \#S path-to-file|tail -1| sed 's|.*\([0-9]*\)$|\1|')
_val2=$(grep \#S path-to-file|tail -1|awk '{print $2}')
_val3=$(grep \#S path-to-file|tail -1| tail -c +4|head -c +4)

_val4=$(grep \#S path-to-file|tail --lines=1)

echo "val1=$_val1
val2=$_val2
val3=$_val3
val4=$_val4"
}

f1
exit 0
```
.......
This will be the output if I run it in a bash shell (not inside my data collection program where i have to invoke unix("cmd") for doing things in a bash shell inside that program):
> 
val1=
val2=8
val3=8  a
val4=#S 8  any string
....................
But if I put the same codes, line by line, in the program i am using via unix("cmd") it does not work always. The grep and tail thing will work. e.g. the first 2 lines will work, next 2 (with awk) would not and I think it has to do with that single double quote business..:
```

def test1 '
u grep \"#S\" path-to-file|tail -1
unix("grep \"#S\" path-to-file|tail --lines=1")
u grep \"#S\" path-to-file|tail -1|awk \'{print $2}\'
unix("grep \"#S\" path-to-file|tail --lines=1|awk \'{print $2}\'")
'

```
and gives this output: 
> 
#S 8  any string
#S 8  any string
awk: line 2: missing } near end of file
0


 The 0 and extra space corresponds to the response of 4th command in the code. 
........................
[COLOR="Red"]Now just now I have found a way..may be it will work...the script i wrote in first place:**a-boring-test**[/COLOR]...i can use it like 
```

unix("**a-boring-test**")

```
and it seem to work! If so I have a workaround. Let's see. Thanks to all of you for listening and trying to help/help.8)8)8)8)8)8)

---

