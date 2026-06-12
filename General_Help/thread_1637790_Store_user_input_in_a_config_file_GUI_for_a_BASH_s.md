---
title: "Store user input in a config file GUI for a BASH script"
date: 2010-12-04
forum: General Help
---

### Post by vaniaspeedy on 2010-12-04
Hi, I'm trying to create a [backup script]("http://www.linuxquestions.org/questions/ubuntu-63/backup-script-848238/"). For my second version, I want to make a GUI that will ask the user three things:
1. which folders should be excluded
2. where to store the backup
3. the user's email

I need to store this input, and later input the values into variables in my script.
How do I go about doings this? I'm relatively new to bash scripting, and have no experience making a GUI.

---

### Post by asmoore82 on 2010-12-04
Bash scripts don't really do GUI's; that's partly what makes them "scripts".

The closest thing to a Bash script GUI is the "zenity" package,
it lets you present 1 widget at a time.
Here's a little something I did long ago:
```
[COLOR="Blue"]#!/bin/bash[/COLOR]

sum="0"

for x in 1st 2nd 3rd {4..10}th
do
	num=`zenity --scale --title "Enter A Number" --min-value 1 --max-value 99 \
		--text "Please, select your ${x} number." --value 50`
	(( sum += num ))
done

zenity --info --title "Grand Total" --text "The Sum is:\n  $sum"

[COLOR="Blue"]#End of File[/COLOR]
```

---

