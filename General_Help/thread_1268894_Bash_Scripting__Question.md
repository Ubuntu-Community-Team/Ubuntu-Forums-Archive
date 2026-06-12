---
title: "Bash Scripting  Question"
date: 2009-09-17
forum: General Help
---

### Post by Kotsouba on 2009-09-17
hello to everyone ,just joined the ubuntu train and i have a question about bash scripting.
Basically i am using read -a to put the contents of a text file into an array and i want to compare each word (now possitioned into the array) with a certain key phrase and i want that to happen in an if statement.Sth like that(there may be a few or many syntax erros but thats not the point :P)
```
if(${Array[i]}=$Keyword) then
do
..
..
..
fi

```but i cant get that to work... is that even possible? 
any help greatly appreciated

---

### Post by DGortze380 on 2009-09-17
Yes, it's possible.

You'll need a while loop with the read statement, and manually manage the indexes of the array items.

Once you've build the array, just loop through like you stated above for your conditional.

If you post the actually script we can help debug and check for syntax errors...

---

### Post by Kotsouba on 2009-09-17
Here is the full script.I know that my aproach may not be the best but anywayz :P```

#!/bin/bash
read -a CITY<"timezones" #Read some Names and time zones from a File and put them in an array
I=0 
FOUND=0 #Flag

function PrintTime() #Function that i call to find the city
{
if [${CITY[$I]}=$CITYNAME ]; then #only comparing the i%2=0 values cause there are the names
echo &#919; &#974;&#961;&#945; &#963;&#964;&#951;&#957; ${CITY[$I]} &#949;&#943;&#957;&#945;&#953;; TZ=${CITY[$I+1]} date  +%r #Typoni sto Terminal
echo &#919; &#974;&#961;&#945; &#963;&#964;&#951;&#957; ${CITY[$I]} &#949;&#943;&#957;&#945;&#953;>>OUTPUT; TZ=${CITY[$I+1]} date  +%r>>OUTPUT #Typoni sto Arxeio
FOUND=1
fi
}
echo Give City Name
read CITYNAME   #the city that we are searching for in the array
while [ $I -lt 10 ]; do
PrintTime #cals the function 
let "I+=2"
done
if [ $FOUND = "0" ]; then 
echo The city you have typed cannot be found
fi


```
atm this is what i get when trying to execute
```

Give City Name
Athens
./FourthScript: line 8: [Lima=Athens: command not found
./FourthScript: line 8: [Apia=Athens: command not found
./FourthScript: line 8: [Moscow=Athens: command not found
./FourthScript: line 8: [Athens=Athens: command not found
./FourthScript: line 8: [Taipei=Athens: command not found
The city you have typed cannot be found


```

---

### Post by DaithiF on 2009-09-17
Hi, you need a space after the '[' character.  otherwise bash thinks you are trying to run the application '[Lima=Athens', which (not unsurprisingly) doesn't exist on your system!

---

### Post by Kotsouba on 2009-09-18
Thank you for that :P still have a problem though, i dont think the if works for some reason its always true no matter what city name i enter!
```
 if [ ${CITY[$I]}=$CITYNAME ];
```
 CITYNAME is a string, City[i] is an arrary containing name of citys in 0,2,4,6,8 and timezones in the form UTC+- in 1,3,5,7,9. What i want to do is compare the given city to the citys in the array each time.

---

### Post by DaithiF on 2009-09-18
try these lines in a terminal ... they may help you see the problem:

```
[[ apples ]] && echo "yes"
yes
[[ apples=oranges ]] && echo "yes"
yes
[[ apples = oranges ]] && echo "yes"


```
... do you see it?

hint: apples=oranges isn't a comparison, its a (single) sequence of characters.  when you ask to test a (single) sequence of characters, bash checks if the sequence is non-empty.  so apples=oranges results in true.

whereas [[ apples = oranges ]] is a comparison of two things.

so in short, again spacing is important -- separate the things you want to compare and the comparison operator by spaces ... [[<space>something<space>=<space>somethingelse<space>]]

---

### Post by Kotsouba on 2009-09-18
Thanx to everyone for the help :) i got it working !

---

