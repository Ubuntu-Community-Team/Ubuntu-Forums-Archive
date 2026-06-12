---
title: "What is wrong with this combination of watch and awk?"
date: 2010-08-17
forum: General Help
---

### Post by Arachan on 2010-08-17
Greetings,

I have a small problem in a script I am trying to write. The script line is 

```
watch -n0.5 " aticonfig --odgc | grep load | awk '{print $4 }' "
```

This should print a number and then a %. However watch seems to ignore the awk and print the whole line that grep would show, 

```
GPU load :    3%
```

Does anyone one why this happens? Do I have the syntax wrong? 

Thanks,
Arachan.

---

### Post by DaithiF on 2010-08-17
try:
```
watch -n0.5 " aticonfig --odgc | grep load | awk '{print \$4 }' "

```

its shell expansion, since your whole command is enclosed within "", the shell expands any $x terms, since you don't have any variable named '4', $4 expands to nothing, and awk just prints the whole line

---

### Post by DaithiF on 2010-08-17
some examples to illustrate:
```
> x=hello
> echo '$x'        # no expansion, single quotes
$x

> echo "$x"       # expansion, double quotes
hello

> echo "'$x'"      # single quotes within double quotes get expanded
'hello'

```

---

### Post by Arachan on 2010-08-18
Greetings,

Thanks a lot, that did the trick.

Arachan.

---

### Post by Arachan on 2010-08-18
Greetings, 

Can I use watch like this?

```
var1=$(watch -t -n0.5 " aticonfig --odgc | grep load | awk '{print \$4 }'")
echo "$var1"
```

This will potentially make var1 change every half second. Can I have a variable like this?

Thanks,
Arachan.

---

### Post by DaithiF on 2010-08-18
No, not like this.  when you execute a subprocess that subprocess has no way to affect the environment (e.g. set variables) of the parent.

you could have your repeating command write its value to a file that you read whenever you need to access the current value.

e.g. run this command (substitute something useful for the echo somevalue piece) to write a value to a file every 30 seconds
```
while [ 1 ]; do echo "somevalue" > ~/.markerfile && sleep 30; done &
```

then when you want to access the current value in a script or from the command line
```
read var < ~/.markerfile
echo $var

```

if this is something you want always running then more robust to do the first part as a cronjob.

---

### Post by Arachan on 2010-08-18
Greetings,

I have another question. Sorry about all the questions, this is one of my first scripts. 

I now have a script which reads

```
watch -t -n0.5 " aticonfig --odgc | grep load | awk '{print \$4 }' > /home/arachan/Desktop/gt"
```If I run that in a terminal and then run my other script in a separate terminal 

```
var1=$(cat /home/arachan/Desktop/gt)
var1=${var1%\%}
echo "$var1"
if [ "$var1" > 10 ]; then
    echo greater than 10
fi
```Why does the if part always seem true (always echos "greater than 10").

Thanks,
Arachan.

---

### Post by DaithiF on 2010-08-18
for numeric comparisons its better to use (( ))
if (( var1 > 10 )); then 

when using [ ] or [[  ]], > is for string comparisons, use -gt for numbers:
if [[ var1 -gt 10 ]]; then

---

### Post by Arachan on 2010-08-18
Greetings,

Thanks a lot for you help. My finished scripts to beep when my GPU gets hotter than 50C are:

Script 1

```
#!/bin/bash
watch -t -n0.5 " aticonfig --od-gettemperature | grep Sensor | awk '{print \$5 }' > /home/arachan/Desktop/gt"
```

Script 2
```

#!/bin/bash
var1=$(cat /home/arachan/Desktop/gt)
var1=${var1%\.00}
if (( "$var1" > 50 )); then
    beep; else
    echo cool enough "(""$var1""C)"
fi
```

Thanks,
Arachan.

---

