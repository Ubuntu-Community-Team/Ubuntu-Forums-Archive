---
title: "Shell script to find factorial"
date: 2009-12-08
forum: General Help
---

### Post by Tapas Bose, India on 2009-12-08
Hallo everybody. My question is : Is shell script support recursive function? I have wrote a shell script of finding factorial of a number. The code is given below:
```

#!/bin/bash

fact ()
{
    if [ $1 -gt 1 ]; then
        y=`expr $1 - 1`
        fact $y

        x=$(( $1 * $? ))
        return $x
    else
        return 1
    fi
}

echo -e "Enter a number : \c"
read num

fact $num

echo "Factorial of $num is $?."

exit 0

```
But it can not give output if I enter 6 or higher number. what is happening? 
Please help.

---

### Post by lackoblacko on 2009-12-08
change
```

echo "Factorial of $num is $?."

```
to
```

echo "Factorial of $num is $x."

```

---

### Post by Tapas Bose, India on 2009-12-08
Thank you lackoblacko. I have changed it as told. But the result is unexpected:
> 
tapas@My-Child:~/Shell$ bash ./factorial.sh
Enter a number : 1
Factorial of 1 is .
tapas@My-Child:~/Shell$ bash ./factorial.sh
Enter a number : 2
Factorial of 2 is 2.
tapas@My-Child:~/Shell$ bash ./factorial.sh
Enter a number : 3
Factorial of 3 is 6.
tapas@My-Child:~/Shell$ bash ./factorial.sh
Enter a number : 4
Factorial of 4 is 24.
tapas@My-Child:~/Shell$ bash ./factorial.sh
Enter a number : 5
Factorial of 5 is 120.
tapas@My-Child:~/Shell$ bash ./factorial.sh
Enter a number : 6
Factorial of 6 is 720.
tapas@My-Child:~/Shell$ bash ./factorial.sh
Enter a number : 7
Factorial of 7 is 1456.
tapas@My-Child:~/Shell$ bash ./factorial.sh
Enter a number : 8
Factorial of 8 is 1408.
tapas@My-Child:~/Shell$ bash ./factorial.sh
Enter a number : 9
Factorial of 9 is 1152.
tapas@My-Child:~/Shell$ bash ./factorial.sh
Enter a number : 10
Factorial of 10 is 1280.
 

See the output for 1, 7, 8, 9, 10. What is your opinion?

---

### Post by lackoblacko on 2009-12-08
the bourne shell cant store alot in $? (exit code).  limit is 255.  heres an alternative way
```

#!/bin/bash

echo "Enter a number"
read num
fact=1
n=$num
while [ $num -ge 1 ]
do

  fact=`echo $fact \* $num|bc`
  
  let num--

done
echo "factorial of $n is $fact"

```

---

### Post by Tapas Bose, India on 2009-12-08
I solved it. Here is the code:
```

#!/bin/bash

# Shell script to find factorial of a given number.

factorial()
{
    if [ $1 -gt 1 ]; then
        i=`expr $1 - 1`
        j=$(echo "$1 * $(factorial $i)" | bc )
            echo $j
    else
        echo 1
    fi
}

####### Main

while [ 1 ]
do
    clear
    echo -e "Enter a number : \c"
    read x
    
    if [ $x -gt 50 ]; then
        echo -e "\nNumber out of range.\c" && sleep 3
    else
        echo -e "\nFactorial of $x is : \c"
        factorial $x
        echo -e "\n" && exit 0
    fi
done

```

---

### Post by Meghnaad on 2010-05-25
[COLOR="DarkRed"]
AVOID RECURSION AS LONG AS POSSIBLE !!!!!![/COLOR]
I know I am too late but see this solution

fact.bash
> #/bin/bash

echo $(seq 1 $1) | tr " " "*" | bc

pass no. as first argument to script

if NUMERIC argument is not passed , it's not going to work
you can perform error checking for arguments

1. If an argument is passed

> if [ $# -ne 1 ]
then
       echo "Some Error..."
       exit 1
fi

2. If passed argument is numeric or not

> if echo "$1" | grep "^[0-9]+$" > /dev/null 2> /dev/null
then
       echo "It's a number"
       #Find Factorial HERE
else
       echo "It isn't a number"
       exit 2
fi


3. you need to check if passed number is 0 if yes Simply Display 1 as output
[COLOR="DarkRed"]
AVOID RECURSION AS LONG AS POSSIBLE !!!!!![/COLOR]

---

### Post by nikhilbhardwaj on 2010-05-25
recursion isn't too bad
sure it uses more memory on the stack and stuff
but the solutions look rather elegant.

---

### Post by Meghnaad on 2010-05-25
@nikhilbhardwaj
> Oh !
what can i say ?

you decide, 

you want memory efficient code !
OR
a good looking code !

and by the way my non recursive code also looks nice ! ;)

---

