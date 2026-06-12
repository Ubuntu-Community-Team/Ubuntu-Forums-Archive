---
title: "bash script problem"
date: 2010-10-04
forum: General Help
---

### Post by U_buntu on 2010-10-04
The problem I'm having is on echo "2. Command list"
it just starts the script over again. Even if I put something else in there like gnome-terminal, it just starts the script over again. I can't figure out why. And in this particular part


2) while read LINE
do
echo "$LINE" 
done  < /home/ubuntu/Documents/ShellScripting/Commands;;

I'm not even sure if that will work correctly in this script. But here is the script below. any ideas?



#!/bin/bash
while :
do
clear
echo "Lets get started then."
sleep 2
clear
echo "What are we reviewing today?"
echo "1. New Terminal"
echo "2. Command List"
echo "3. exit"
read opt
case $opt in
1) gnome-terminal;;
2) while read LINE
do
echo "$LINE" 
done  < /home/ubuntu/Documents/ShellScripting/Commands;;
3) exit;;
*) echo "$opt in an invalid option. Please press enter to continue."
read enterkey;;
esac
done

---

### Post by lloyd_b on 2010-10-05
> **U_buntu said:**
> The problem I'm having is on echo "2. Command list"
it just starts the script over again. Even if I put something else in there like gnome-terminal, it just starts the script over again. I can't figure out why. And in this particular part


2) while read LINE
do
echo "$LINE" 
done  < /home/ubuntu/Documents/ShellScripting/Commands;;

I'm not even sure if that will work correctly in this script. But here is the script below. any ideas?



#!/bin/bash
while :
do
clear
echo "Lets get started then."
sleep 2
clear
echo "What are we reviewing today?"
echo "1. New Terminal"
echo "2. Command List"
echo "3. exit"
read opt
case $opt in
1) gnome-terminal;;
2) while read LINE
do
echo "$LINE" 
done  < /home/ubuntu/Documents/ShellScripting/Commands;;
3) exit;;
*) echo "$opt in an invalid option. Please press enter to continue."
read enterkey;;
esac
done

Try this instead:```
#!/bin/bash
while :
do
    clear
    echo "Lets get started then."
    sleep 2
    clear
    echo "What are we reviewing today?"
    echo "1. New Terminal"
    echo "2. Command List"
    echo "3. exit"
    read opt
    case $opt in
        1) gnome-terminal;;
        2) cat /home/ubuntu/Documents/ShellScripting/Commands |
           while read LINE
           do
             echo "$LINE" 
           done
           echo "Press any key to continue"
           read enterkey;;
        3) exit;;
        *) echo "$opt in an invalid option. Please press enter to continue."
           read enterkey;;
    esac
done
```The "cat ... |" executes the 'cat' command, and pipes the output from it to the 'while' loop, which is what you want in this case.

Lloyd B.

---

### Post by lloyd_b on 2010-10-05
Was doing something else, and realized that the whole 'while' loop is rather silly in this case - the 'less' command is more reasonable:```
#!/bin/bash
while :
do
    clear
    echo "Lets get started then."
    sleep 2
    clear
    echo "What are we reviewing today?"
    echo "1. New Terminal"
    echo "2. Command List"
    echo "3. exit"
    read opt
    case $opt in
        1) gnome-terminal;;
        [COLOR="Red"]2) less /home/ubuntu/Documents/ShellScripting/Commands;;[/COLOR]
        3) exit;;
        *) echo "$opt in an invalid option. Please press enter to continue."
           read enterkey;;
    esac
done
```(but my first example is a useful example of how to handle looping through the output from a command, in case you *do* actually need it in the future)

Lloyd B.

---

### Post by U_buntu on 2010-10-05
awesome they both work great. Thanks

---

