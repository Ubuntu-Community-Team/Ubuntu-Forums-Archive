---
title: "Shell script to generate Fibonacci series using recursion"
date: 2009-12-08
forum: General Help
---

### Post by Tapas Bose, India on 2009-12-08
I am facing problem with Shell script to generate Fibonacci series using recursion i.e. recursive function.
Here is my script:
```
#!/bin/sh

fibo()
{
    no=$1
    if [ $no -eq 1 ]; then
        return 0
    elif [ $no -eq 2 ]; then
        return 1
    else
        a1=`expr $no - 1`
        fibo $a1
        a=$(echo $?)

        b1=`expr $no + 1`
        fibo $b1
        b=$(echo $?)

        c=`expr $a + $b`
        return $c
    fi
}

####### Main

clear

echo -e "Enter number of terms : \c"
read n

if [ $n -gt 0 ]; then
    for (( i=1; i<=$n; i++ ))
    do
        fibo $i
        echo $?    
    done
else
    echo -e "Invalid input."
fi
```
But it does not give output.
Please help... 		   		  		  		  		  		  		 			 			 				[IMG]http://solaris.unix.com/images/misc/progress.gif[/IMG]

---

### Post by Tapas Bose, India on 2009-12-08
Please help.

---

### Post by Tapas Bose, India on 2009-12-08
bump

---

### Post by frodon on 2009-12-08
Fast bumping tactic and probably homework, thread closed till you can provide valid arguments to re-open it.

As a reminder posting homework as support request is not allowed by our Code of Conduct.

Thread closed.

EDIT: thread re-opened after PM exchange.

---

### Post by Tapas Bose, India on 2009-12-08
It is solved.
Here is the code : 
```

#!/bin/sh

# Shell scrpt to generate Fibonacci series using recursion

export MINIDX=2                     

Fibonacci ()
{
    idx=$1                
    if [ "$idx" -lt "$MINIDX" ]; then
        echo "$idx"              
    else
        (( --idx ))              
        term1=$( Fibonacci $idx )       

        (( --idx ))              
        term2=$( Fibonacci $idx )       

        echo $(( term1 + term2 ))
    fi
}

echo -n "Enter the number of term : "
read MAXTERM

for (( i=0; i<=$MAXTERM; i++ ))
do                      
    FIBO=$(Fibonacci $i)
    echo -n "$FIBO "
done

echo

exit 0

```

---

