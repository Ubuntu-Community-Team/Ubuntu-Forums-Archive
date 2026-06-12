---
title: "Passing commands to Functions in BASH"
date: 2012-02-26
forum: General Help
---

### Post by iMetaphysikz on 2012-02-26
```

#!/bin/bash

ask()
{
$1
}

ask "echo This is not working >> 2.txt"

```

Can anyone enlighten me on this one?
The echo command works but the re-direction to the text file 2.txt does not work
Can someone explain why this is the case.

---

### Post by TeoBigusGeekus on 2012-02-26
Try with this
```
#!/bin/bash

ask()
{
$1
}

ask "echo This is not working" >> 2.txt
```

---

### Post by Thorsen V on 2012-02-26
try:

ask()
{
$1
}

ask "echo This is not working" >> 2.txt

ETA: [TeoBigusGeekus,]("http://ubuntuforums.org/member.php?u=504094") you beat me by a minute :)

---

### Post by scheibenlosen on 2012-02-26
> **iMetaphysikz said:**
> ```

#!/bin/bash

ask()
{
$1
}

ask &quot;echo This is not working >> 2.txt&quot;

```Can anyone enlighten me on this one?
The echo command works but the re-direction to the text file 2.txt does not work
Can someone explain why this is the case.

 Try removing ask(), and then as a command, sh ask "echo This is not working" >> 2.txt  It works for me.

---

### Post by sudodus on 2012-02-26
What do you want to do? Maybe you can use the read command of bash to assign your input to a variable. Test making the file ***echoer*** of the following three lines
```

#! /bin/bash

echo "Input line of text and press Enter"
read txt
echo "Echoing $txt"

```
and run it with ```
bash ./echoer
```

---

### Post by iMetaphysikz on 2012-02-26
The Problem that i now have is that if i want a second command/line of text that I want to pass to the function for example "echo hello" redirects its output to the 2.txt file as-well

This is 

```

[]("http://ubuntuforums.org/member.php?u=504094")#!/bin/bash

ask()
{
$1
$2
}

ask "echo This is not working" > 2.txt "echo hello"

```

---

### Post by Thorsen V on 2012-02-26
that works how I'd expect it to.

Can you clarify what you're trying to so?

---

### Post by Thorsen V on 2012-02-26
#!/bin/bash

ask()
{
$2 > $1
$3
}

ask "2.txt" "echo This is not working"  "echo hello"

This prints "This is not working" to file and hello to the console ... is that what you're after?

---

### Post by Khayyam on 2012-02-26
iMetaphyisicz ...

I think you are 're-using' my function without understanding 'function' and its use.

```
#!/bin/bash

function ask()
{   
    echo -n "$@" '[y/n] ' ; read ans
    case "$ans" in
        y*|Y*) return 0 ;;
        *) return 1 ;;
    esac
}

ask "Do you understand functions?" &&
echo "YES" > yesweunderstandfunctions.txt
```In your example the "function" is whatever is passed as parameter "${1}" to the script.

```
% cat param.sh
#!/bin/bash

echo "Parameter \${1} is ${1}"
% param.sh yes
Parameter ${1} is yes
% param.sh gobbldygook
Parameter ${1} is gobbldygook
```Not the best way to provide a function ... it might help if you explain what your trying to do. The following perhaps?

```
#!/bin/bash

if [[ -z ${@} ]]; then
    echo "No question provided."
    echo "Usage: $(basename ${0}) question"
    exit
fi

function ask()
{   
    echo -n "$@" '[y/n] ' ; read ans
    case "$ans" in
        y*|Y*) return 0 ;;
        *) return 1 ;;
    esac
}

ask "${@}" && echo "${@}=YES" > answer.txt
```Just so you understand, functions can do other things other than 'ask' questions.

```

nd () {
  test -d "${1}" || mkdir -p "${1}" && cd "${1}"
}
```With this function 'nd newdir' will make a directory 'newdir' and 'cd newdir'.

Hope that helps clarify things ...  khay

---

### Post by iMetaphysikz on 2012-02-26
Thanks Khayyam.

Essentially I am trying to reuse the ask function to do different things depending on the situation, in some instances I want to append to a log file, in other instances I want to call another function depending on user response.

In the code below rdx would be another function that the script calls

```

ask()
{
        local  i=0

        for i in {1..10}
                do

                        echo -n "$1"
                        read ans
                        ans=$(echo $ans | tr '[A-Z]' '[a-z]')

                        case $ans in
                                y)
                                        $2
                                        return 0 ;;
                                n)
                                        $3
                                        return 0 ;;
                                *)
                                        echo  "Please enter y or n"
                                        local j=$((10-$i))
                                        echo  "If neither y/n is pressed after $j attempts it will be assumed that $3"
                        esac

        done
        echo $3
}

ask "Please Enter an RDX Cartridge if formatting is required, is the RDX cartridge inserted (y/n)?" "rdx" "RDX Cartridge formatting is not required"

ask "echo Has this script been useful" "echo Very Useful >> feedback.txt" "echo Try again Buddy >> feedback.txt"



```

Now using your code with the && will add text to the yesweunderstandfunctions.txt if the user says yes because the function was successfully completed, but if the user says no it will not, I would also have to capture this information to a text file.

That's why I have used the "echo Very Useful >> feedback.txt"


```

ask "Do you understand functions?" &&
echo "YES" > yesweunderstandfunctions.txt

```

Note, the code I have written above may not work as it was a rough example, as I ammended it from the script I'm currently writting. However I do not have that script on the computer I'm currently on.

---

### Post by iMetaphysikz on 2012-02-26
A Global variable and an if statement after calling the function will do what I'm looking for.
I Just wasn't thinking clearly.

Thanks for the help everyone

---

### Post by Khayyam on 2012-02-27
> **iMetaphysikz said:**
> Thanks Khayyam.

Your welcome, but please, no more 'pseudocode' ... "funcoid () { ${1} }" doesn't explain what your trying to do, **real** code examples provide those reading with some clue as to where you might be going wrong. If you post 'examples' like the above pseudocode, then the best we can do is guess. 

> **iMetaphysikz said:**
> Essentially I am trying to reuse the ask function to do different things depending on the situation, in some instances I want to append to a log file, in other instances I want to call another function depending on user response.

Thats **exactly** what a function does, your just not understanding it correctly. Each time 'ask' is called, there will be a 'retval', 0 for success, 1 for failure, you can use this to do whatever you want as part of the answer given to that question. When I used "&&" this was just **one** way of using retval.

You don't need to "call another function" just provide one, functions are like "commands", they are just a way simplify the code (for reuse). You can state all your functions at the top of the script and use them, or not, in whatever part of the script you choose.

> **iMetaphysikz said:**
> Now using your code with the && will add text to the yesweunderstandfunctions.txt if the user says yes because the function was successfully completed, but if the user says no it will not, I would also have to capture this information to a text file. That's why I have used the "echo Very Useful >> feedback.txt"

Easy, "If .. else". Your not really understanding how the function can be used. If it could only be used once, then it would be sort of pointless providing it as a function.

Also, watch your quotes ... echo "Very Useful" >> feedback.txt .. spaces are "special" characters and need to be quoted.

So, an example ..

```
#!/bin/bash

function ask()
{ 
    echo -n "$@" '[y/n] ' ; read ans
    case "$ans" in
        y*|Y*) return 0 ;;
        *) return 1 ;;
    esac
}

ask "Question 1?"
    if [[ "$?" = 0 ]] ; then
        echo "1=YES" >> answers.txt
    else 
        echo "1=NO" >> answers.txt
    fi
ask "Question 2?"
    if [[ "$?" = 0 ]] ; then
        echo "2=YES" >> answers.txt
    else
        echo "2=NO" >> answers.txt
    fi
ask "Question 3?"
    if [[ "$?" = 0 ]] ; then
        echo "3=YES" >> answers.txt
    else
        echo "3=NO" >> answers.txt
    fi
exit
```Thats it at its most simplified. You could do include further questions within the "if .. else", or further tests, commands, etc. 

best ... khay

---

