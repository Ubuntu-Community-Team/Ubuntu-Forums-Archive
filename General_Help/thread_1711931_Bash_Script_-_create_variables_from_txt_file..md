---
title: "Bash Script - create variables from txt file."
date: 2011-03-21
forum: General Help
---

### Post by Chrus on 2011-03-21
I'm working on a script that asks a lot of questions from the user when it is first run, and stores all the answers into variables that will be used later in the script. So I had the idea of storing the answers in a text file the first time they are answered, then read them back the next time the script is run and only ask the user for variables that are empty.

I've got the part about checking if the variable is empty, asking for a value and passing it to a text file sorted. Its the reading it back into that variable thats causing problems.

Using a case statement, I can check each variable and do them one at a time. But with the number of variables I plan on having, thats gonna be one massive case statement. Theres gotta be a better way.

Mytext file is laid out VAR_NAME=value on each line. I was looking for a way of having the script go through my text file line by line and create the variable called whatever is before the '=' and put the value in from whatever is after the '='.

Does sound logical?

I've included a piece of test code I was playing around with trying to get the concept sorted out.

Thanks

```

#!/bin/bash

touch info.txt

for line in $(cat info.txt)
do
   case "$line" in
      NAME=*)
         NAME=${line:5}
         ;;
      SOMEONEELSE=*)
         SOMEONEELSE=${line:12}
         ;;
   esac
done

##################################

if [ ! -n "$NAME" ]; then
   echo "Please enter your name:"
   read NAME
   echo "NAME=${NAME}" >> info.txt
fi

if [ ! -n "$SOMEONEELSE" ]; then
   echo "Please enter someone elses name:"
   read SOMEONEELSE
   echo "SOMEONEELSE=${SOMEONEELSE}" >> info.txt
fi

echo "Your name is ${NAME}"
echo "Somoeone else is ${SOMEONEELSE}"


```

---

### Post by DaithiF on 2011-03-22
The quickest way would be to simply **source** the file with the variable definitions.  That will populate the variables with their values for the rest of your script.

```
$ cat info.txt
NAME=john
AGE=23
$ source info.txt
$ echo $NAME; echo $AGE
john
23

```

however there is a security risk here because you are executing the contents of the info.txt file, so if someone with malicious intent modified the file by adding some other commands then you would unknowingly execute those commands.

A slightly safer alternative would be to read the file, split lines on the '=' character and only execute those lines that look like variable assignments.

```
while read line
do
  IFS="=" read name value <<< "$line"
  [[ -n "$name" && -n "$value" ]] && eval "$name=$value"
done < info.txt
echo "name is $NAME"
echo "age is $AGE"
```

but this is still basically flawed because you're still executing code that you can't be sure hasn't been changed.  

So while its possible to do what you want, probably better to explicitly check for the variables you expect to be populated, to avoid having to execute code other than your own.

---

### Post by Chrus on 2011-03-22
Thanks mate. That looks like it should do what im after.

---

