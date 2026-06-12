---
title: "Need help in shell programming"
date: 2009-12-03
forum: General Help
---

### Post by Tapas Bose, India on 2009-12-03
Hallo everybody.
I wrote a shell script       which displays the result of division of one real number by another and informs if the user tries to divide by zero. Which is 
> 
#!/bin/sh
## Shell script of dividing two number
while [ 1 ]
do
    clear
    
    echo -n "Enter the Numerator : "
    read num
    echo -n "Enter the Denominator : "
    read den

    if  [ $den == 0 ]; then
        echo -e "\nDenominator can not be zero."
        sleep 2
    
    else
        res=`echo "scale=10; $num / $den" | bc`
        echo "The answer is : $res"
        exit
    fi

done
Everything is fine. But whenever I try to divide by 0.0 or 0.0000 etc it gives output
> 
Enter the Numerator : 1.1
Enter the Denominator : 0.0000
Runtime error (func=(main), adr=17): Divide by zero
The answer is : 
I can not solve the problem.
And whenever the result is is less than 1 it gives the output in the following format
> 
Enter the Numerator : 1.3
Enter the Denominator : 3.4
The answer is : .3823529411
Is there any way to get the output like 0.3823529411?
Please help.

---

### Post by derrick81787 on 2009-12-03
> **Tapas Bose, India said:**
> Hallo everybody.
I wrote a shell script       which displays the result of division of one real number by another and informs if the user tries to divide by zero. Which is 
Everything is fine. But whenever I try to divide by 0.0 or 0.0000 etc it gives output
I can not solve the problem.
And whenever the result is is less than 1 it gives the output in the following format
Is there any way to get the output like 0.3823529411?
Please help.

Your first problem is because you are using == to test numerical equality.  The == is for testing string equality, so if it is exactly 0, it will work, but anything else, like 0.0 it will not.  To test numerical equality, use -eq like

```
if [ $den -eq 0 ]; then
```

As far as the second problem, I don't know.

- Derrick

---

### Post by doas777 on 2009-12-03
you will probably have to check to see if the value is less than 1, but greater than -1, and prepend a 0 in that case.

---

### Post by Tapas Bose, India on 2009-12-03
Thank you Derrick. I change it into > if  [ $den -eq 0 ]; then. But now I got the following output
> 
Enter the Numerator : 3.4
Enter the Denominator : 5.6
./division.sh: line 12: [: 5.6: integer expression expected
The answer is : .6071428571

What about > ./division.sh: line 12: [: 5.6: integer expression expected
It does not appear when I use > if  [ $den == 0 ]; then

---

### Post by Tapas Bose, India on 2009-12-03
> **doas777 said:**
> you will probably have to check to see if the value is less than 1, but greater than -1, and prepend a 0 in that case.
I change it like
> 
if  [ $den -eq 0 ]; then
        echo -e "\nDenominator can not be zero."
        sleep 2
    
    else
        res=`echo "scale=10; $num / $den" | bc`
        if [ $res -lt 1 ];then
            echo "The answer is : 0$res"
        
        else
            echo "The answer is : $res"
        fi
        exit
    fi

But I got the output
> Enter the Numerator : 1
Enter the Denominator : 2
./division.sh: line 18: [: .5000000000: integer expression expected
The answer is : .5000000000


---

### Post by bit mad on 2009-12-03
$vars can only be whole numbers (integers)
[http://www.askdavetaylor.com/compare_float_real_numbers_in_a_shell_script.html](http://www.askdavetaylor.com/compare_float_real_numbers_in_a_shell_script.html)


see 17.4 here [http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial)

---

### Post by StuartN on 2009-12-03
> **Tapas Bose, India said:**
> whenever I try to divide by 0.0 or 0.0000 etc it gives output

It is easier to handle the numbers and errors within the bc script:

```
echo "scale=10; if ($den == 0) \"Error\" else $num / $den" | bc
```

This will output num/den, or Error if den is zero.

> **Tapas Bose, India said:**
> whenever the result is is less than 1 it gives the output in the following format

You can use c-style print formatting, for example **printf %8.6f .32** outputs 0.320000 (a float of width 8 and 6 digits following the decimal point).

---

### Post by Tapas Bose, India on 2009-12-03
> **StuartN said:**
> 

```
echo "scale=10; if ($den == 0) \"Error\" else $num / $den" | bc
```
Now I do this
```

#!/bin/sh
clear
    
    echo -n "Enter the Numerator : "
    read num
    echo -n "Enter the Denominator : "
    read den
echo "scale=10; if ($den == 0) \"Error\" && else $num / $den" | bc

```
And get this error
> Enter the Numerator : 1
Enter the Denominator : 2
(standard_in) 1: syntax error


---

### Post by StuartN on 2009-12-03
> **Tapas Bose, India said:**
> ```
echo "scale=10; if ($den == 0) \"Error\" && else $num / $den" | bc
```
And get this error

Delete the &&.

---

### Post by bit mad on 2009-12-03
```

[COLOR=Blue]#!/bin/sh[/COLOR]

echo "enter two numbers"
read aa
read bb
echo

if [ "$bb" = "0.0" ]; then
[COLOR=Blue]# echo "0.0 detected";[/COLOR]
  bb=0
fi
 
if [ "$bb" = 0 ]; then
  cc="division error (infinity)"
else
[COLOR=Blue]# cc=$(echo "scale=10; $aa/$bb" | bc)  # alternative:[/COLOR]
  cc=`echo "scale=10; $aa / $bb" | bc`
fi

[COLOR=Blue]# dd will be all chars before any . in cc[/COLOR]
dd=${cc%.*}
[COLOR=Blue]# if no chars before .  (string starts with .)  add 0 to start of cc[/COLOR]
if [ "$dd" = "" ]; then
[COLOR=Blue]# or without dd, all in 1 go :  if [ "${cc%.*}" = "" ]; then [/COLOR]
cc="0$cc"
fi

echo "$aa/$bb = $cc"

echo
echo "press return"
read a

```[COLOR=Red]
[/COLOR]

---

### Post by Tapas Bose, India on 2009-12-04
Thank you bit mad...

---

### Post by Tapas Bose, India on 2009-12-04
At last it is solved and gives desired output. It can handle 0, 0.0, 0.00, 000, 000.0000 any kind of denominator. 
```

#!/bin/sh
## Shell script of dividing two number
while [ 1 ]
do
    clear
    
    echo -n "Enter the Numerator : "
    read num
    echo -n "Enter the Denominator : "
    read den
    
    n=$(echo "scale=1; $den * 1 " | bc)

    if [ $n -eq 0 ]; then
        echo -e "\nDenominator can not be zero.\c"
        sleep 2
    else
        res=`echo "scale=10; $num / $den" | bc`

        printf "The result is : %.10g/%.10g=%.10g\n" $num $den $res
        echo -e "\nPress return to continue ...\c"
        read char
        exit
    fi
done

```
I am not marking this thread as solved because any one can enhance it.
Thank you friends.

---

### Post by bit mad on 2009-12-04
Well done :)

There is an easier way to test for a leading dot in my code :
**${cc:0:1}**  would be the first character, but some some reason I had trouble last night with that expression in Portable Ubuntu (on Windows) - it worked as part of a terminal command but not in a script file. And **echo -e** didn't work either. Weird!
Today in a VirtualBox (Ub. 9.04) it works both ways.

**if [ "${cc:0:1}" = "." ]; then cc="0$cc"; fi**

But your printf solution is more elegant :P
Thanks for the exercise, I was learning as I went too. There's something about Linux's openness that makes finding things out quite enjoyable.

---

### Post by Tapas Bose, India on 2009-12-04
Can you please explain me this syntax **${cc:0:1}** bit mad[B]...
[/B]

---

### Post by bit mad on 2009-12-04
substring of cc, from 1st place (the count starts at 0!), for 1 chars

if $cc  was "Test" then **${cc:1:2}** would be "es"

---

### Post by Tapas Bose, India on 2009-12-04
> @ bit madOkay clear. Thanks friend. Now I am trying to write a script which find prime numbers within a given range using the theory : given a number *n*, divide *n* by all numbers *m* less than or equal to the square root of n.

---

