---
title: "Creating a math script"
date: 2010-07-16
forum: General Help
---

### Post by heatblazer on 2010-07-16
Hello. Recently I was trying to make a quick script for calculating payment between workers. I got stuck however... Here is what I am in for...

#!/bin/bash
#Setting the calculator
calc=` bc << EOF
scale=4
a=$2*($3/100)
b=$4
a/b
EOF
`
Good trough here... I`ve saved the $1 for further script... but... I need help from now on...

#Creating the script

while [ -n $1 ]
        do 
        case $1 in
        workerA) read -p "Enter the total sum: " total
                  total=$2;
                  read -p "Enter the percentage:" percent
                  percent=$3;
                  read -p "Enter number of workers:" workers
                  workers=$4 ;;
         *) echo "Error usage!"
          break
          esac
done


So... My script ends here... It just does not work.. what I am missing? Did I sat the vars in the wrong way?

---

### Post by gzarkadas on 2010-07-16
The `read -p "prompt" var' statement assigns the answer to `var' immediately upon execution; so the assignment afterwards is wrong. 

In addition $1 is not needed, unless you have other workerA-type sections in your case statement and a `shift' command inside your while loop.

Your script, for a one time calculation could be simply coded as:
```

#!/bin/bash
 
read -p "Enter the total sum: " total
read -p "Enter the percentage:" percent
read -p "Enter number of workers:" workers

bc << EOF
scale=4
a=$total*($percent/100)
b=$workers
a/b
EOF

```

---

### Post by heatblazer on 2010-07-17
> **gzarkadas said:**
> The `read -p "prompt" var' statement assigns the answer to `var' immediately upon execution; so the assignment afterwards is wrong. 

In addition $1 is not needed, unless you have other workerA-type sections in your case statement and a `shift' command inside your while loop.

Your script, for a one time calculation could be simply coded as:
```

#!/bin/bash
 
read -p "Enter the total sum: " total
read -p "Enter the percentage:" percent
read -p "Enter number of workers:" workers

bc << EOF
scale=4
a=$total*($percent/100)
b=$workers
a/b
EOF

```

Thanks. I know that. But... I was planing to enter more options to case command like workerA, workerB, workerC etc... The problem comes from there... but with a single option it does not work too :)

---

### Post by heatblazer on 2010-07-17
Figured it out...

ilian@RAI-X:~$ ./math -a
 Enter total sum: 9000
 Enter percentage:34
 Enter number of personel:5
(standard_in) 5: illegal character: O
(standard_in) 5: syntax error
The payment per selected worker is 612.0000 
ilian@RAI-X:~$ 

Now it correctly outputs what I wanted but still gets this annoying msg... Here is the code


!/bin/bash
#setting variables for math
#creating the script itself...F***it!

while [ -n $1 ]
        do
                case $1 in
                        -a) read -p " Enter total sum: " total
                            read -p " Enter percentage:" percent
                            read -p " Enter number of personel:" numb
                                math=` bc << EOF
                                        scale=4
                                        a=$[$total]*($[$percent]/100)
                                        b=$[$numb]
                                        a/b
                                        EOF
                                        `
                                break ;;
                        -b) echo "Usage: set the total sum to any non 0 character. Set percent and number of workers to any number. Then use the command 'math -a' or -b and enter the prompt"
                                break ;;
                        *) echo " Error in com line "
                                break ;;
                        --)
                                shift
                                break
                esac
        done
#Showing the freakin mess
echo "The payment per selected worker is $math "

---

### Post by gzarkadas on 2010-07-17
You don't actually need options here, when calling the script; they are just to provide help to the user.  Also the brackets you put (I suppose they are arrays) is something that is not needed here; single variables suffice. 

The whole complexity stems from the use of inappropriate tools to handle the script's main loop. The standard way to handle command line options in scripts is with `getopt'; using it gives you the full power that you, as a user, experience when interacting with a CLI utility. 

You can use `man getopt' to see more details for this highly useful command. It will benefit you in the long run. To solve the problem now, I attach a working skeleton script that uses getopt and has all those standard little pieces in place:

```

#!/bin/bash

function show_help ()
{
    cat << EOF
usage: math [options]
Calculate payment of workers from a total and a percentage
      --help                 display this help screen and exit
      --version              output version information and exit

Report math bugs to <your-email-address>
EOF
}

function show_version ()
{
    cat << EOF
math ver. 0.0.1 - calculate payment of workers 
Copyright (C) YEAR Your-Name <your-email-address>.
<licence-information>
EOF
}

function do_calc ()
{
    echo -e "scale=4\na=$1*($2/100)\nb=$3\na/b" | bc
}

function get_data ()
{
    local total percent workers

    read -p "Enter the total sum: " total
    read -p "Enter the percentage:" percent
    read -p "Enter number of workers:" workers

    echo $total $percent $workers
}

# MAIN

# add here switches to each new option; see man getopt for details
TEMP=$(getopt -o '' -l 'help,version' -n 'math' -- "$@")
if [ $? -ne 0 ] ; then 
    echo "Terminating..." >&2
    exit 1
fi
eval set -- "$TEMP"
# add here a section for each new option
while true ; do
    case $1 in
    --help)
        show_help
        exit 0
        ;;
    --version)
        show_version
        exit 0
        ;;
    --)
        # this gets you out of the option processing
        shift
        break
        ;;
    *) 
        echo "Internal error! Terminating..."
        exit 1
        ;;
    esac
done
# evaluate here remaining positional arguments if any
# and do the bulk of the job
echo "The payment per selected worker is: " $(do_calc $(get_data))

```Now, if you don't need to give the script to others to use, this is a lot of code for a simple task. For yourself it would be more easy to use this command:

```

read -p "Enter sum, percentage, workers: " total percent workers && echo -n "The payment per selected worker is: " && echo -e "scale=4\na=$total*($percent/100)\nb=$workers\na/b" | bc

```and save it as an alias in your .bachrc (or .bash_aliases if you use it), like this:

```

alias math='read -p "Enter sum, percentage, workers: " total percent workers && echo -n "The payment per selected worker is: " && echo -e "scale=4\na=$total*($percent/100)\nb=$workers\na/b" | bc'

```The .bashrc and .bash_aliases are hidden files inside your home folder. Use the `View|Show Hidden Files' nautilus menu to show them and then open them with gedit to actually edit them.

---

### Post by heatblazer on 2010-07-17
> **gzarkadas said:**
> You don't actually need options here, when calling the script; they are just to provide help to the user.  Also the brackets you put (I suppose they are arrays) is something that is not needed here; single variables suffice. 

The whole complexity stems from the use of inappropriate tools to handle the script's main loop. The standard way to handle command line options in scripts is with `getopt'; using it gives you the full power that you, as a user, experience when interacting with a CLI utility. 

You can use `man getopt' to see more details for this highly useful command. It will benefit you in the long run. To solve the problem now, I attach a working skeleton script that uses getopt and has all those standard little pieces in place:

```

#!/bin/bash

function show_help ()
{
    cat << EOF
usage: math [options]
Calculate payment of workers from a total and a percentage
      --help                 display this help screen and exit
      --version              output version information and exit

Report math bugs to <your-email-address>
EOF
}

function show_version ()
{
    cat << EOF
math ver. 0.0.1 - calculate payment of workers 
Copyright (C) YEAR Your-Name <your-email-address>.
<licence-information>
EOF
}

function do_calc ()
{
    echo -e "scale=4\na=$1*($2/100)\nb=$3\na/b" | bc
}

function get_data ()
{
    local total percent workers

    read -p "Enter the total sum: " total
    read -p "Enter the percentage:" percent
    read -p "Enter number of workers:" workers

    echo $total $percent $workers
}

# MAIN

# add here switches to each new option; see man getopt for details
TEMP=$(getopt -o '' -l 'help,version' -n 'math' -- "$@")
if [ $? -ne 0 ] ; then 
    echo "Terminating..." >&2
    exit 1
fi
eval set -- "$TEMP"
# add here a section for each new option
while true ; do
    case $1 in
    --help)
        show_help
        exit 0
        ;;
    --version)
        show_version
        exit 0
        ;;
    --)
        # this gets you out of the option processing
        shift
        break
        ;;
    *) 
        echo "Internal error! Terminating..."
        exit 1
        ;;
    esac
done
# evaluate here remaining positional arguments if any
# and do the bulk of the job
echo "The payment per selected worker is: " $(do_calc $(get_data))

```Now, if you don't need to give the script to others to use, this is a lot of code for a simple task. For yourself it would be more easy to use this command:

```

read -p "Enter sum, percentage, workers: " total percent workers && echo -n "The payment per selected worker is: " && echo -e "scale=4\na=$total*($percent/100)\nb=$workers\na/b" | bc

```and save it as an alias in your .bachrc (or .bash_aliases if you use it), like this:

```

alias math='read -p "Enter sum, percentage, workers: " total percent workers && echo -n "The payment per selected worker is: " && echo -e "scale=4\na=$total*($percent/100)\nb=$workers\na/b" | bc'

```The .bashrc and .bash_aliases are hidden files inside your home folder. Use the `View|Show Hidden Files' nautilus menu to show them and then open them with gedit to actually edit them.

Quite awesome coding... I`ll keep that in mind. Thanks for the info I am learning for 2 weeks and the code you posted is great and makes quite sense...! I`ll keep it as a source for future scripts.

---

