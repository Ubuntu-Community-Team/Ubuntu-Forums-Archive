---
title: "Application Launcher shortcut to open termianl and execute a command"
date: 2010-01-15
forum: General Help
---

### Post by alibahaloo on 2010-01-15
Hello People...

I'm having Ubuntu Kramic Koala and i want to create a custom application launcher on the panel so when it is clicked it should open a terminal window and run the following command and then show the output for 5 secs and then closes the terminal... how can i do this?

```
cat /proc/sys/vm/laptop_mode && sleep 5
```

the above command is what i want to be executed at time of running the custom application launcher. if i paste the command in a terminal, it will show the output for 5 secs and then terminates... that's almost what i want. what i exactly want is that, i want it to work like when i click on the shortcut launcher, it should open a terminal and then exectues that command, show the output for 5 sec, pause, and then exits the teriminal.

:) i appreciate all the helps.
thanks in advance.

---

### Post by Cabs21 on 2010-01-15
> **alibahaloo said:**
> Hello People...

I'm having Ubuntu Kramic Koala and i want to create a custom application launcher on the panel so when it is clicked it should open a terminal window and run the following command and then show the output for 5 secs and then closes the terminal... how can i do this?

```
cat /proc/sys/vm/laptop_mode && sleep 5
```the above command is what i want to be executed at time of running the custom application launcher. if i paste the command in a terminal, it will show the output for 5 secs and then terminates... that's almost what i want. what i exactly want is that, i want it to work like when i click on the shortcut launcher, it should open a terminal and then exectues that command, show the output for 5 sec, pause, and then exits the teriminal.

:) i appreciate all the helps.
thanks in advance.

Write as simple Bash script and create a link to that and tell it to run in terminal.  It will open terminal and run your script.  Just add a quit line to the end and it will close the terminal when its done.

```
!bin/bash
cat /proc/sys/vm/laptop_mode && sleep 5
quit
```

Try this, see if it works.

also make sure you make the script executable,
```
chmod +x Path/to/your/script
```

---

### Post by alibahaloo on 2010-01-15
Works like a charm... thanks :)
i created a .sh script and the content is :
```
cat /proc/sys/vm/laptop_mode && sleep 5
quit

```
then i made a custom application launcher and choose the .sh script as command... :) now it works as i wanted...nice
now i want to modify the output if possible, help me with this if you can...

when i run the script, the output is always a number, i want to do it like, if the number is zero then "OFF" should be printed to the terminal, if its any number other than 0 then it should print "ON"... i'll play around with it to see if i can achieve it myself, but if you have ideas, I'd be happy to know them :)

thanks

---

### Post by Cabs21 on 2010-01-15
> **alibahaloo said:**
> Works like a charm... thanks :)
i created a .sh script and the content is :
```
cat /proc/sys/vm/laptop_mode && sleep 5
quit

```then i made a custom application launcher and choose the .sh script as command... :) now it works as i wanted...nice
now i want to modify the output if possible, help me with this if you can...

when i run the script, the output is always a number, i want to do it like, if the number is zero then "OFF" should be printed to the terminal, if its any number other than 0 then it should print "ON"... i'll play around with it to see if i can achieve it myself, but if you have ideas, I'd be happy to know them :)

thanks

I am not great at writing code but I would try to do something like this (again this is not exact code at all just a guess and how I would try it at first)

```
cat /proc/sys/vm/laptop_mode && sleep 5
if output==0
echo "OFF"
else if output==1
echo "ON"
end
quit
```

---

### Post by alibahaloo on 2010-01-15
> **Cabs21 said:**
> I am not great at writing code but I would try to do something like this (again this is not exact code at all just a guess and how I would try it at first)

```
cat /proc/sys/vm/laptop_mode && sleep 5
if output==0
echo "OFF"
else if output==1
echo "ON"
end
quit
```
Yes, i also had this in mind, to use if and else statements, but i get some syntax error, that's probably because I'm not very familiar with script writing...

---

### Post by Cabs21 on 2010-01-15
if and elseif might not be a usable input or command.  You will have to do some research on how to get these results.  Sorry I can't help you any further.  

This link might help.

[http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)

---

### Post by alibahaloo on 2010-01-15
> **Cabs21 said:**
> if and elseif might not be a usable input or command.  You will have to do some research on how to get these results.  Sorry I can't help you any further.  

This link might help.

[http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)
i see... thanks anyways... 
i think i know what the problem is, i need to read the output and then compare that output with what i  want...
cat prints the output on the terminal, and that output should compared...
hmm, i wonder how i can read this ouput, maybe save it as another string or integer variable then compare it and print the output i want depending on it...

---

### Post by alibahaloo on 2010-01-15
```
#!/bin/bash

status=$(cat /proc/sys/vm/laptop_mode)
if [ $status -eq 0 ] ; then
    echo "Laptop Mode OFF"
else
    echo "Laptop Mode ON"
fi
    echo "Terminating in 5 seconds..."
sleep 5
exit
```

this script works with the above requirements... 

cheers

---

### Post by Cabs21 on 2010-01-15
cool.  Glad I could help

---

