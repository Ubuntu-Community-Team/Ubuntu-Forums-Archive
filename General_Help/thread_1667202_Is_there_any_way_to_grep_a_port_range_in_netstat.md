---
title: "Is there any way to grep a port range in netstat"
date: 2011-01-14
forum: General Help
---

### Post by dodo3773 on 2011-01-14
Right now I have 
```
netstat --tcp --numeric |  cut -c 45-65 | sort -u | sed '/Foreign/d' | sed '/^$/d' | grep -e ':80' -e ':443'
```Which will show me all of my http stuff. I would like to continue to do this for Other protocols (email, ftp, etc..) The problem I have is that I cannot figure out how to grep something like :48620-:49150  I am not even sure that this is possible. If it is not then is there any way to create a list of those numbers in this format 

 -e ':48620'
 -e ':48621'
etc...

So that I can just dump that into my script? Also, will that seriously affect the performance of the script if I have to do it that way because of the length? I read somewhere that this sort of thing can be done with sed but I am not really sure. Thanks in advance.

---

### Post by Vaphell on 2011-01-14
can't you extract the port part and check if it's greater than $lower_boundary and lower than $upper_boundary?

---

### Post by Vaphell on 2011-01-14
what i meant was: write a multiline script so you can play with data freely, use variables and stuff

```
#!/bin/bash

lower=75
upper=90

#fifth column, skip first 2 rows (header)
sockets=$(netstat --tcp --numeric | awk 'NR>2 {print $5}' )

echo port range: $lower-$upper

for socket in $sockets
do
  ip=${socket%:*}
  port=${socket#*:}
  if (( $lower <= $port && $port <= $upper )) 
  then
    echo $socket \(port within range\)
  else
    echo $socket
  fi
done
```

---

### Post by dodo3773 on 2011-01-15
> **Vaphell said:**
> what i meant was: write a multiline script so you can play with data freely, use variables and stuff

```
#!/bin/bash

lower=75
upper=90

#fifth column, skip first 2 rows (header)
sockets=$(netstat --tcp --numeric | awk 'NR>2 {print $5}' )

echo port range: $lower-$upper

for socket in $sockets
do
  ip=${socket%:*}
  port=${socket#*:}
  if (( $lower <= $port && $port <= $upper )) 
  then
    echo $socket \(port within range\)
  else
    echo $socket
  fi
done
```

So the lower and upper are variables that you set yourself? Can "lower" and "upper" be anything as long as they are followed with =number? Also, how could I pull out the extra data that I do not need? What does 

 ```
for socket in $sockets
```mean? I am curious too about this

```
ip=${socket%:*}
port=${socket#*:}
```Thanks by the way.

---

### Post by Vaphell on 2011-01-15
> So the lower and upper are variables that you set yourself? Can "lower" and "upper" be anything as long as they are followed with =number?
yes, they are hardcoded at the beginning in my example
you create variables
```
variable=<value>
```
and use them with $ sign, eg
```
echo $variable
some_program $variable
```

you can also assign script parameters there, if you run your script with
```
my_script <lower> <upper>
```
then you can assign parameter values to 'lower' and 'upper' variables
```
lower=$1
upper=$2
```
$1 = first param, $2 = 2nd param

> Also, how could I pull out the extra data that I do not need?
what would you want exactly here? filter out 80 and 443? you can modify the command to suit your needs (pipe it to grep like you did) or simply do nothing inside the 'for' loop when port = 80 or 443 (if statement)


> for socket in $sockets

as you can see in the script 'sockets' variable stores the output of the command in $()
later 'for' loop puts its hands on that variable, takes each 'word' (delimited by whitespace) which happens to be in the IP:****port format and assigns it to socket variable. Between 'do' and 'done' you get to play with the current value of $socket. In other words it iterates the set of sockets and $socket stores current socket so you can access it.

> ip=${socket%:*}
port=${socket#*:}

this extracts a substring from the socket (ip:****port)
ip=${socket%:*} means get the part of $socket that is BEFORE ':*', meaning ': followed by any sequence of chars' and store it in $ip
port=${socket#*:} means get the part of $socket that is AFTER '*:', meaning 'any sequence of chars followed by :' and store it in $port

if you want to write scripts, find some bash manual on the net and dive in - you won't regret it

---

### Post by dodo3773 on 2011-01-15
> what would you want exactly here? filter out 80 and 443? you can modify the command to suit your needs (pipe it to grep like you did) or simply do nothing inside the 'for' loop when port = 80 or 443 (if statement)I guess what I am really trying to do after reading through this is to define a number range as one variable or grep two variables at once. What I did was

```
grep -e ':80' -e ':443'
```which was simple enough. But the problem I ran into is that if I wish to use a range like
49152 through 65535
(private ports usually used on my machine for bittorrent traffic)

I cannot really grep -e that. Well I could but I figure that there has got to be another way. I guess another way I could do this is to set a variable of anything above 49152. But then later when I am plugging in unassigned port ranges I
would have to know how to do this anyways.

> if you want to write scripts, find
some bash manual on the net and dive in -
you won't regret itI have looked at a few manuals and right now I am watching a video series on unix shell scripting. But to be honest I have learned and accomplished more on these forums than I have ever been able to with self study. It is like when I read some of these books and the author explains something I still don't get it. I am starting to understand man pages. But, I still feel that they could be a little less cryptic. Also, people here give me real examples that I can actually use and that mean something to me which has significantly helped me in learning newthings. Do you have any books or videos that you would highly recommend?

---

### Post by Vaphell on 2011-01-16
to be honest i learnt most of stuff by having a goal and googling for complete/partial answers - you know: 'linux cut substring', 'linux replace string' or something like that :) you will get like dozens of possibilities using different tools. At first you use 3 tools for everything but with time you get to know more and more tools and ways of doing stuff.

back to the port ranges:
- i noticed it just now - your ":80" and ":443" will fail for ":8011" or ":4433", you need to test if next char is whitespace \s or end-of-line $ (depending on situation)

fancy regex in grep to cover port ranges could work but it would be an absolute pain in the a$s to write and giving grep thousands of expressions (to cover each port of the range in naive way) to search is not cool.
Problem with patterns is that they don't get into logic behind the characters. For most tools integers is just a bunch of 0-9 characters not a number and is up to the user to add actual logic.
Maybe there is some magic one-liner or a combination of netstat parameters that can do your stuff but when you don't know it, there is nothing wrong with writing more verbose script without obscure hacks.

upgraded script
```
#!/bin/bash

if [ "$#" == "0" ]
then
  #default values
  ports=(  80     443       8000-9000   3000-5000 )
  labels=( "HTTP" "HTTPS"   "SOMETHING"   "TORRENT" )
else
  #script arguments
  i=0
  while (( "$#" ))
  do
    ports[i]=$1
    shift
    labels[i]=$1
    shift
    i=$((i+1))
  done
fi

sockets=$( netstat --tcp --numeric | awk 'NR>2 {print $5}' )
size=${#ports[@]}

#calculate arrays of $lower and $upper from $ports array
for (( i=0; i<${size}; i++ ))
do
  lower[i]=${ports[i]%-*}
  upper[i]=${ports[i]#*-}
done

for socket in $sockets
do
  ip=${socket%:*}
  port=${socket#*:}
  #iterate arrays of $lower and $upper to see if $port matches
  for (( i=0; i<${size}; i++ ))
  do
    if (( ${lower[i]} <= $port && $port <= ${upper[i]} )) 
    then
      echo $socket ${labels[i]}
      break
    fi
  done
done

```

Ports is an array of port ranges - single number means single port, x-y means from x to y, labels is an array of related labels assigned to ports (labels[i] describes ports[i]). You can modify these 2 at will - the only condition is that numbers of elements match, so use "" if you don't want a label. $size keeps the size of arrays so i can use it later to iterate easily over them.
from $ports array $lower and $upper arrays are calculated (stuff before - and stuff after - in $ports element, single port has no '-' so the whole string is returned, thus $lower=$upper)

next step is actual analysis. As you can see, netstat command is not grepped so the script tests each line of the netstat output. Each socket is tested against the range of $lower and $upper and if the port matches, $socket is printed out with the associated label.
As a bonus, thanks to labels you can run this script and easily pipe it to grep to display only a subset of sockets.
Also it's possible to rework this script to accept parameters, eg
```
my_script <port1> <label1> <port2> <label2> ...
``` and populate the arrays from parameters so it's even more flexible.

EDIT: added support for script arguments - not entirely foolproof, assumes even number of params, use "" for no label

---

### Post by dodo3773 on 2011-01-16
> **Vaphell said:**
> 
> to be honest i learnt most of stuff by having a goal and googling for complete/partial answers I could not agree more. This is the only real method I have ever known before joining these forums.
[QUOTE]
- i noticed it just now - your ":80" and ":443" will fail for ":8011" or ":4433", you need to test if next char is whitespace \s or end-of-line $ (depending on situation)Thank you for the tip. So, instead of ```
grep -e ":80" 
``` I would have to use ```
grep -e ":80 " 
```I am going to change my script right now accordingly. 

> fancy regex in grep to cover port ranges could work but it would be an absolute pain in the a$s to write and giving grep thousands of expressions (to cover each port of the range in naive way) to search is not cool.This is my problem. Right on the money.


> upgraded script
```
#!/bin/bash

if [ "$#" == "0" ]
then
  #default values
  ports=(  80     443       8000-9000   3000-5000 )
  labels=( "HTTP" "HTTPS"   "SOMETHING"   "TORRENT" )
else
  #script arguments
  i=0
  while (( "$#" ))
  do
    ports[i]=$1
    shift
    labels[i]=$1
    shift
    i=$((i+1))
  done
fi
sockets=$( netstat --tcp --numeric | awk 'NR>2 {print $5}' )

size=${#ports[@]}
echo ${ports[@]}
echo ${labels[@]}


#calculate arrays of $lower and $upper from $ports array
for (( i=0; i<${size}; i++ ))
do
  lower[i]=${ports[i]%-*}
  upper[i]=${ports[i]#*-}
done

for socket in $sockets
do
  ip=${socket%:*}
  port=${socket#*:}
  #iterate arrays of $lower and $upper to see if $port matches
  for (( i=0; i<${size}; i++ ))
  do
    if (( ${lower[i]} <= $port && $port <= ${upper[i]} )) 
    then
      echo $socket ${labels[i]}
      break
    fi
  done
done

```Ports is an array of port ranges - single number means single port, x-y means from x to y, labels is an array of related labels assigned to ports (labels[i] describes ports[i]). You can modify these 2 at will - the only condition is that numbers of elements match, so use "" if you don't want a label. $size keeps the size of arrays so i can use it later to iterate easily over them.
from $ports array $lower and $upper arrays are calculated (stuff before - and stuff after - in $ports element, single port has no '-' so the whole string is returned, thus $lower=$upper)

next step is actual analysis. As you can see, netstat command is not grepped so the script tests each line of the netstat output. Each socket is tested against the range of $lower and $upper and if the port matches, $socket is printed out with the associated label.
As a bonus, thanks to labels you can run this script and easily pipe it to grep to display only a subset of sockets.
Also it's possible to rework this script to accept parameters, eg
```
my_script <port1> <label1> <port2> <label2> ...
``` and populate the arrays from parameters so it's even more flexible.

EDIT: added support for script arguments - not entirely foolproof, assumes even number of params, use "" for no labelI am having a real hard time wrapping my head around this. I need to sit down and study this for a while. One thing I did notice is that you ended the script with "done" instead of "exit" Does that do the same thing? Is there an advantage to using one over the other?

---

### Post by Vaphell on 2011-01-16
i can explain some minute details if you wish, no problem - just ask

> One thing I did notice is that you ended the script with "done" instead of "exit"

there is no ending at all, script will end either way so why bother. done ends 'for' loops
in the last part there are 2 loops, one embedded in another - so there are 2 done's at the end

```

for ... #outer loop
  for ... #inner loop

  done #inner loop
done #outer loop

```

---

### Post by dodo3773 on 2011-01-16
> i can explain some minute details if you wish, no problem - just askI still need to figure out how a loop works. Give me a little while to do some googling and some tests so that I can understand a little better what is going on here.


> there is no ending at all, script will end either way so why bother. done ends 'for' loops
in the last part there are 2 loops, one embedded in another - so there are 2 done's at the endSo is putting exit at the end of a script just a waste of time? I do have an additional question for you (a little off topic). I created a script that starts some applications when my computer starts.

```
#! /bin/bash

sleep 10 && evolution & firefox-4.0 & sleep 20 && devilspie -a &  sleep 25 && pkill -f "devilspie -a"



exit
```But when I looked into my system monitor I noticed that "startupopen.sh" (the name of the script above) is still running after it executes. So, I created another script ```
#! /bin/bash


sleep 55 && pkill startupopen.sh


exit
```which kills the first one. Is there a better way to do this from the original script instead of needing to call on an additional one? This does not seem possible because how could a running script kill itself? Just curious if you ever came across this. Also, I noticed in your script and some others I have seen that the code is indented on certain lines. Is that something that you do yourself or are you using a certain editor that does that for you? Anyways, give me a little time to study and when I understand a little more I will get back to you.

---

### Post by Vaphell on 2011-01-16
examples of for loops
```
aaa="1 2 3"
echo LOOP 1
for a in $aaa; do echo a=$a; done;

echo LOOP 2
for a in {1..3}; do echo a=$a; done;

echo LOOP 3
for a in X{a..b}{1..2}; do echo a=$a; done;

echo LOOP 4
for (( a=0; a<4; a++ )); do echo a=$a; done;

echo LOOP 5
aaa=( 1 2 3 )
for a in ${aaa[@]}; do echo a=$a; done;

echo LOOP 6
aaa=( 1 2 3 )
for (( i=0; i<${#aaa[@]}; i++ )); do echo aaa[$i]=${aaa[i]}; done;

echo LOOP 7
for a in {1..3}; do
  for b in {1..3}; do
    echo a=$a b=$b
  done
done
```

you can end your script with exit anywhere and define the return code - 0 is treated as success, everything else is an error so you can use && and || to do stuff or use conditions to perform error-specific procedures.

lets say you have
prog1 && prog2
this requires that prog1 ends with 0 so prog2 can be executed
prog1 || prog2
here prog2 will run only when prog1 ends with an error
if you are not going to chain your script with anything or there is no need to end the script in the middle then you don't need exit

offtopic problem - no help here. I know what &, && or sleep do but i lack deeper knowledge, i find it strange though. Does **ps ux** confirm that the process is still running?

---

### Post by dodo3773 on 2011-01-16
> examples of for loopsThanks for this. It will take me a while to figure out though.

> you can end your script with exit anywhere and define the return code - 0 is treated as success, everything else is an error so you can use && and || to do stuff or use conditions to perform error-specific procedures.

lets say you have
prog1 && prog2
this requires that prog1 ends with 0 so prog2 can be executed
prog1 || prog2
here prog2 will run only when prog1 ends with an errorThis is one of the things I do get. "&&" and "&" are actually what got me started with this whole thing. I thought wow doing two things at once or one after the other is awesome. The "||" I have yet to use but I am sure that I will eventually. If I understand correctly the "||" is like an "if then else" without the "if" and the "then". 

> if you are not going to chain your script with anything or there is no need to end the script in the middle then you don't need exitCould you please elaborate on this a little?

> offtopic problem - no help here. I know what &, && or sleep do but i lack deeper knowledge, i find it strange though. Does **ps ux** confirm that the process is still running?Well I didn't use "ps ux" but the process was definitely still running. It is alright though the second script really takes care of that. The weird thing is that the second script does not keep running like the first. I can't explain it but it works.

---

### Post by Vaphell on 2011-01-16
> [quote]if you are not going to chain your script with anything or there is no need to end the script in the middle then you don't need exit


Could you please elaborate on this a little?[/quote]

[php]
if <something bad>; then
  exit 1 #error
fi
if <something else bad>; then
  exit 2 #error
fi
if <something good>; then
  exit 0 #success
fi

some
bunch
of
code
#if you got here with no problems, the script will exit with the code of the last command by itself (usually 0, yes?)
[/php]

if you have exits nicely defined you can use your script in a && b || c chains or make use of the exit code in scripts using $?. eg 
```
if [ "$?" == "666" ]
```
$? is a special variable that keeps the code

&&'s are braindead easy but to understand what exactly happens with && and || you need to know this - they are simply boolean logic operators (&&=AND, ||=OR) and the logic value of the whole chain is evaluated. code 0 = TRUE and code not-0 = FALSE
**a && b**
* if a is FALSE then the whole thing is FALSE => there is no need to check b (b command is skipped)
* if a is TRUE then we need to check b because the value of the whole expression = value of b (b command is executed)
in the sequence of ANDs first FALSE sets whole expression to FALSE

**a || b**
* if a is TRUE then the whole thing is TRUE no matter what (b is skipped)
* if a is FALSE then the value = value of b (b is executed)
in the sequence of ORs first TRUE sets whole expression to TRUE

of course ANDs and ORs can be mixed for fancy hacks

---

### Post by dodo3773 on 2011-01-16
So,  what your saying is that exit is for separating two or more different blocks of code in the same script. Is that basically it?

---

### Post by Vaphell on 2011-01-16
no, exit ends the execution of the script, no questions asked. In my pseudocode example the script can end in 4 different places
script enters condition #1 or #2 => ends with error with the exit code assigned, any code below that if is not executed
script enters condition #3 => ends with success, any code below that if is not executed
script executes everything => ends naturally with the exit code of the last command

[php]#!/bin/bash

echo "some code"

if (( $1 == 666 )); then
  echo SUCCESS
  exit 0
fi

echo "some more code"

if (( $1 > 0 )); then
  echo ERROR $1
  exit $1
fi

echo "even more code"[/php]

run the script above with different integer parameters (666, non-zero, 0)
```
./script 0
echo $?
./script 1
echo $?
./script 666
echo $?
```

666 triggers exit in the first if (success), any non-zero triggers exit in the second if (error), 0 skips ifs

---

### Post by dodo3773 on 2011-01-16
> **Vaphell said:**
> 

Because it is "then exit". Got it. I don't see how I missed that one.

---

### Post by Vaphell on 2011-01-16
yes, everything between then and fi belongs to the condition and is executed only if condition is met. Proper indentation is good and helps to keep track visually of what happens.

---

### Post by dodo3773 on 2011-01-17
> **Vaphell said:**
> yes, everything between then and fi belongs to the condition and is executed only if condition is met. Proper indentation is good and helps to keep track visually of what happens. Do you do the indentation by hand or is it an option that you set in your editor?

---

### Post by Vaphell on 2011-01-17
gedit, manual indentation though gedit can help you with that (it can start the new line with the indentation of the last line so it's easy to write blocks of code with unified intentation). Using tab and del from time to time never killed anybody and keeping the code tidy greatly reduces the time needed to write/debug.

---

### Post by dodo3773 on 2011-01-18
> **Vaphell said:**
> Using tab and del from time to time never killed anybody and keeping the code tidy greatly reduces the time needed to write/debug.Ha ha. Yeah thats true. I am still used to Writing small scipts. I am sure that when they start getting bigger this will be very useful. Based on all the things we have gone over the only conclusion I can come to is that this cannot be done ( using grep on a range of numbers I mean). I guess my only real option would be writing a really long script with all of the numbers in it. Do you think that an extremely long script would seriously affect the performance of running said script? I know that there is a way to output numbers in the terminal that you can predefine start and finish. I just do not remember what it is I will find it again though. So, I guess my next question is do you know how to add text to the beginning of multiple lines? For example if I had 

```

21
22
23
24
```and wanted to change it to

```

 -e :21
 -e :22
 -e :23
 -e :24

```How is this done? Do you know?

---

### Post by dodo3773 on 2011-01-18
O.K. So if I run ```
#! /bin/bash

seq 1 10 | sed "s/^/ -e ':/" | sed "s/$/'/" ;bash



exit
```It will give me

```
 -e ':1'
 -e ':2'
 -e ':3'
 -e ':4'
 -e ':5'
 -e ':6'
 -e ':7'
 -e ':8'
 -e ':9'
 -e ':10'
```So now the problem I have is that each one is a new line. So what I need to do is instead of a new line I need them just separated by spaces. Let me know what you think.

---

### Post by Vaphell on 2011-01-18
```

echo {a..z} {1..10}
echo -e\ {1..10}
echo -e\ :{8000..9000}[^0-9]*

netstat --tcp --numeric | awk 'NR>2 {print $5}' | grep $( echo -e\ :{8000..9000}[^0-9]* )
```

that command takes approx 1sec/1k of ports on my box - i thought it would be worse. Still i don't like it :-) 3/4 of the time is probably spent on the optimization of the expression alone as the results start to flow near the end.
approach of my script may be a bit slower than pure grepping for smaller sets of ports (who cares about 0.2s vs 1s anyway), it wins hands down in flexibility and in cases with huge port ranges where the execution time of naive grep reaches 30+ secs

btw, you can flatten multiline text simply by echoing it or storing in a variable
```

seq 1 10
echo $(seq 1 10)
var=$(seq 1 10)
echo $var

```
you can change this behavior by playing with the IFS variable that defines the separator of 'words'. By default any whitespace is considered a separator and is changed into space when you run it through variables and commands. You can change it so let's say only newlines are separators (=> formatting doesn't degrade). Very useful when you got to do something with let's say files with spaces in names, changing IFS to newline only prevents filename fragmentation that leads to frequent errors.

---

### Post by dodo3773 on 2011-01-18
Alright heres what I got. This

```
seq 1 10 | sed "s/^/ -e ':/" | sed "s/$/ '/" | tr "\\n" " "
```Will give me the range all on one line.

I tried the code you just posted

```
echo {a..z} {1..10}
echo -e\ {1..10}
echo -e\ :{8000..9000}[^0-9]*

netstat --tcp --numeric | awk 'NR>2 {print $5}' | grep $( echo -e\ :{8000..9000}[^0-9]* )


```and it gave me

```
-e :8000[^0-9]* -e :8001[^0-9]* -e :8002[^0-9]* -e :8003[^0-9]* -e :8004[^0-9]* -e :8005[^0-9]* -e :8006[^0-9]* -e :8007[^0-9]* -e :8008[^0-9]*  etc etc..
```So now I come to the other part. The if then. My script goes like this

```

if [ "$(netstat --tcp --numeric |  cut -c 45-65 | sort -u | sed '/Foreign/d' | sed '/^$/d' | grep -e ':80' -e ':443')" ]; then
echo 'http / https' && netstat --tcp --numeric |  cut -c 45-65 | sort -u | sed '/Foreign/d' | sed '/^$/d' | grep  -e ':80' -e ':443'
fi

```So, the if has to contain the whole statement so that the http / https will only echo if there is output from the original statement. Is there a better way?

---

### Post by Vaphell on 2011-01-19
> I tried the code you just posted

my example code showed how to produce a range of parameters. I merely printed out that huge range of **-e '...'** with the intermediate steps like using {..} to easily construct a range. Last line *should* do what you want as it actually uses that bunch of generated parameters in grep.

> So now I come to the other part. The if then. My script goes like this

1. why do you still use that cut | sort | sed | sed combo?
awk 'NR>2 { print $5 }' will print out the 5th element of each row when the row number > 2 (skips Foreign and empty line automatically), so you don't have to cut from-to and then remove non-ip lines with sed manually - unless i am missing something

2. you should sort **after** grepping - picking 10 elements out of 100 and sorting them later is more efficient than sorting 100 elements and picking 10 later. Doesn't matter much in a case with not so many lines but if you ever wanted to do that on a huge set of data, it would be like a night and day.

3. you execute the chain twice for no good reason
store the result in a variable, check the variable, print the variable out if the condition is met

[php]#!/bin/bash

fixed="-e .*:80 -e .*:443"
range=$( echo '-e .*:'{8000..8090} )
ports=$( echo "$fixed" "$range" )

grepped=$( netstat --tcp --numeric | awk 'NR>2 {print $5}' | grep -w $ports | sort -u )

if [ "$grepped" ]; then
  echo == HTTP/HTTPS ==
  echo "$grepped"
fi
[/php]

---

### Post by dodo3773 on 2011-01-19
> **Vaphell said:**
> 



why do you still use that cut | sort | sed | sed combo?
awk 'NR>2 { print $5 }' will print out the 5th element of each row when the row number > 2 (skips Foreign and empty line automatically), so you don't have to cut from-to and then remove non-ip lines with sed manually - unless i am missing something

No, it was me who was missing something. I just don't completely understand the command. What you said was that {print $5} prints the fifth element. That makes sense to me. But what does NR>2 mean? I know you explained it but I still do not completely get it. I just tried it and it works great though. 



> you execute the chain twice for no good reason
store the result in a variable, check the variable, print the variable out if the condition is metI did not know that a variable could be a command. That makes things alot easier. So, is it always 

variable=$( yourcommandhere )

I tried it before but did not use a $ and it did not work. I still have much to learn.


```
fixed="-e .*:80 -e .*:443"
range=$( echo "-e"\ '.*:'{8000..8090} )
ports=$( echo "$fixed" "$range" )

grepped=$( netstat --tcp --numeric | awk 'NR>2 {print $5}' | grep -w $ports | sort -u )

if [ "$grepped" ]; then
  echo == HTTP/HTTPS ==
  echo "$grepped"
fi
```After playing with this for a minute I think you have got it! This is it. The answer to the whole problem. I feel like you have been trying to show this to me for a while and I just did not get it. Also, with some very minor tweaking, I can use either one of the variables to get the desired effect. Dependant upon whether I want a range or a fixed number of ports. I can't believe I did not see this before. This is going to save me a lot of work and space. I have learned much from you. This is why I like ubuntu forums. Thank you.

---

### Post by Vaphell on 2011-01-20
let's take few lines of the netstat output
```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 10.111.255.23:42631     10.111.12.74:22        ESTABLISHED
```

as you can see first 2 lines are junk, we don't need them
```
awk '**NR>2** { print $5 }'
``` bolded part is a condition: do the stuff in {} only when the row number (NR) is greater than 2

we need only foreign ip:****port and it's is in the 5th column
```
awk 'NR>2 { **print $5** }'
``` bolded part: print 5th column of the data row

combined it means 'skip first 2 rows and then print the 5th thing from each row'

---

### Post by dodo3773 on 2011-01-20
> **Vaphell said:**
> 
```
awk '**NR>2** { print $5 }'
``` bolded part is a condition: do the stuff in {} only when the row number (NR) is greater than 2

we need only foreign ip:port and it's is in the 5th column
```
awk 'NR>2 { **print $5** }'
``` bolded part: print 5th column of the data row

combined it means 'skip first 2 rows and then print the 5th thing from each row'

Thank you for the explanation. One last question before I mark this thread as solved.  NR>2 chops off the first two lines. I got that. But when I reverse it like NR<2 it only shows me the first line. How would I go about chopping off just the last 2 lines?

---

### Post by Vaphell on 2011-01-20
well, it's rather obvious
the opposite of 'greater than' is not 'less than' but 'less than or equal'

#1: (1>2) -> false **(1<2) -> true**
#2: (2>2) -> false (2<2) -> false
#3: **(3>2) -> true** ( 3<2) -> false

you need to use <= or >= operators to include the boundary

---

### Post by dodo3773 on 2011-01-20
Thanks again. Marking this thread as solved.

---

