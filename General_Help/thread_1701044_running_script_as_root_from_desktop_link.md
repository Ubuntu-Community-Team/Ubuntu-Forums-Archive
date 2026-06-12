---
title: "running script as root from desktop link"
date: 2011-03-05
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-03-05
so i have my file sh script 
```
#!/bin/sh
echo "Minutes to shutdown after:"
read input_variable
typeset -i input_variable
echo "Will power off after $input_variable minutes..."
echo "Press [Ctrl]+[C] to cancel shut down."
sleep $(($input_variable*60))
halt
exit 0
```
i wanted it to open a terminal with root access but i cant see mto get it to open and prompt for a password
gksu gnome-terminal -x sh /path/to/script.sh

---

### Post by dcstar on 2011-03-06
> **pqwoerituytrueiwoq said:**
> so i have my file sh script 
```
#!/bin/sh
echo "Minutes to shutdown after:"
read input_variable
typeset -i input_variable
echo "Will power off after $input_variable minutes..."
echo "Press [Ctrl]+[C] to cancel shut down."
sleep $(($input_variable*60))
halt
exit 0
```
i wanted it to open a terminal with root access but i cant see mto get it to open and prompt for a password
gksu gnome-terminal -x sh /path/to/script.sh

Create a Launcher "Application in Terminal" that does:

```
gksudo scriptname
```

---

### Post by pqwoerituytrueiwoq on 2011-03-06
if i do that the second echo is not displayed in the terminal
oh well i just rewrote the script
```
#!/bin/sh
input_variable=$(zenity --entry --title "How long should I wait?" --text "Minutes to shutdown after:" --width 300)
if [ "$input_variable" ]; then
    if [ "$input_variable" -eq "$input_variable" 2> /dev/null ]; then
        if [ "$input_variable" -gt "-1" ]; then
            if [ $(zenity --question --title="Are you sure?" --text "This computer will power off after $input_variable minutes"; echo $?) = "0" ]; then
                sleep $(($input_variable*60))
                halt
            else
                echo "Shutdown aborted"
            fi
        else
            zenity --error --title "Invalid input" --text "The lowest number I will accept is 0 and $input_variable is less than 0"
        fi
    else
        zenity --error --title "Invalid input" --text "\"$input_variable\" is not a number\nDecimals are not accepted" --width 200
    fi
else
    echo "See you later"
fi
exit 0
```dependencies are zenity sleep and halt if anyone is interested
you can change the echo commands to espeak commands and it will read the text but you will need to have espeak installed

---

