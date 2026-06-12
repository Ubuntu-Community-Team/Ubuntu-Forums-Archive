---
title: "a shell script i made gives an output file i didn't ask it to give"
date: 2009-07-15
forum: General Help
---

### Post by chriskin on 2009-07-15
the script is this one 
```
#!/bin/bash
x=1 
while [ x > 0 ] 
do
    xwinwrap -ni -o 0.4 -fs -s -st -sp -b -nf -- mplayer -wid WID -nosound  "/home/christos/Documents/5 cms per second.mkv"
done
```

and it gives an empty file everytime it runs, named 0 

how can i make this stop?

---

### Post by sisco311 on 2009-07-15
> **chriskin said:**
> the script is this one 
```
#!/bin/bash
x=1 
while [ x **> 0** ] 
do
    xwinwrap -ni -o 0.4 -fs -s -st -sp -b -nf -- mplayer -wid WID -nosound  "/home/christos/Documents/5 cms per second.mkv"
done
```

and it gives an empty file everytime it runs, named 0 

how can i make this stop?

stop *asking* bash to create the file. :)

[COLOR="Red"]x[/COLOR] [COLOR="Blue"]> 0[/COLOR] = [COLOR="Red"]run command x(bash: x: command not found)[/COLOR], [COLOR="Blue"]create file 0[/COLOR]

take a look at the syntax of the while loop:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_02.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_02.html") 

and read the man page of the test command:
```
man [
```

if you want an infinite loop, then try something like:
```
while [ 1 ]; do ...
``` 

```
while [ 1 -gt 0 ]; do ...
```
or
```
while true; do ...
```
or 
```
until [ ]; do ...
```
or 
```
for ((;;)); do...
```
or
```
while ((1)); do ...
```

---

### Post by chriskin on 2009-07-15
> **sisco311 said:**
> stop *asking* bash to create the file. :)

[COLOR=Red]x[/COLOR] [COLOR=Blue]> 0[/COLOR] = [COLOR=Red]run command x(bash: x: command not found)[/COLOR], [COLOR=Blue]create file 0[/COLOR]

take a look at the syntax of the while loop:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_02.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_02.html) 

and read the man page of the test command:
```
man [
```if you want an infinite loop, then try something like:
```
while [ 1 ]; do ...
``````
while [ 1 -gt 0 ]; do ...
```or
```
while true; do ...
```or 
```
until [ ]; do ...
```or 
```
for ((;;)); do...
```or
```
while ((1)); do ...
```

hehe, i was just translating from a language we were taught in high school , and thought bash would work the same way

thank you :)

---

