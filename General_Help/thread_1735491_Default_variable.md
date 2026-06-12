---
title: "Default variable"
date: 2011-04-21
forum: General Help
---

### Post by thomas515 on 2011-04-21
Is there a way to set a default variable in a script? Like if when prompted for a variable, entering nothing will default to a variable?

---

### Post by daweefolk on 2011-04-21
are you trying to write it in a bash shell script?
```
if [$variable==""] 
then export variable="defaultvalue" 
fi
```
I'm not that fluent in bash, but i believe that's right

---

### Post by thomas515 on 2011-04-21
ok what I'm trying to do is write a script to shutdown or reboot.

```
#!/bin/bash
clear
echo -n "Shutdown (-h) or Restart (-r)?:"
read WHAT
echo -n "When?:"
read WHEN
if [ "$WHAT" = "-h" ]; then
function pause() {
read -p "$*"
}
clear
sudo -u god sudo shutdown -h $WHEN

else
clear
sudo -u god sudo shutdown -r $WHEN
fi

```

What I want to do is set the $WHEN to a default of 'NOW' so it will shutdown immediately without me entering a time.  Any way to do this?

---

### Post by dino99 on 2011-04-21
an example

[http://www.ohbuntu.blogspot.com/2010/01/auto-shutdown-timer.html](http://www.ohbuntu.blogspot.com/2010/01/auto-shutdown-timer.html)

---

### Post by thomas515 on 2011-04-21
Well this is more for my own knowledge on multiple if-then statements not so much a shutdown script.

---

### Post by kaibob on 2011-04-21
> **thomas515 said:**
> Is there a way to set a default variable in a script? Like if when prompted for a variable, entering nothing will default to a variable?

You can use parameter expansion as explained in the Bash Reference Manual:

> ${parameter:=word}
If parameter is unset or null, the expansion of word is assigned to parameter. The value of parameter is then substituted. Positional parameters and special parameters may not be assigned to in this way. 

[http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion)

This same topic is discussed under the heading "Assign a default value" on the following site:

[http://wiki.bash-hackers.org/syntax/pe](http://wiki.bash-hackers.org/syntax/pe)

The default value is assigned to the variable when it is expanded: 

> $ var="hello" ; echo "${var:=bye}" ; echo $var
hello
hello

$ var="" ; echo "${var:=bye}" ; echo $var
bye
bye

If you want to assign a default value to an empty variable after prompting the user for input, I would probably just use  a simple bash test:

```
#!/bin/bash

read -p "Enter a word: " keypress

[[ -z "$keypress" ]] && keypress="no response"
```

---

