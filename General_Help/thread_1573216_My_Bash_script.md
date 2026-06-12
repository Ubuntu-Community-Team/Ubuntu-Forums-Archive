---
title: "My Bash script"
date: 2010-09-12
forum: General Help
---

### Post by coolness on 2010-09-12
Hello all.

I am trying to make a script that will install certain programs. 
Here's the code:
> #!/bin/bash
echo "This script will add programs you like to the computer. Press enter to get started."
read
clear
#repeats this until the user asks for exit, otherwise he would have to run it over and over again.
until [ $question == "2" ]
do
	echo "Which programs would you like to install? Opera (1) Close (2)"
	#asks to install, reads users choice
	read question
	if [ $question == "1" ]
		then 
	#installs opera if user says 1
		apt-get install opera
	elif [ $question == "2" ]
	#exits if he says 2
		then
		exit
	#If the user types something else, it lets him try again
	else
		echo "I dont understand, use 1 or 2"
	fi
done


So, what am i doing wrong? Thanks.

---

### Post by Lukas666 on 2010-09-12
And what do you get? 

BTW, apt-get requires "sudo".

---

### Post by sharathcshekhar on 2010-09-12
I think you need to initialize variable question before calling until[]
question=0
Looks fine to me otherwise. Secondly, you will have to make sure the script is run as with sudo since you are running apt-get install

---

### Post by WorMzy on 2010-09-12
Opera isn't in the main repos, so unless you've added a custom repo that has Opera, you're going to get an error when the script tries to install it.

---

### Post by coolness on 2010-09-12
> **Lukas666 said:**
> And what do you get? 

BTW, apt-get requires "sudo".

I get [: 23: ==: unexpected operator

Thanks for your replys everyone,

> Opera isn't in the main repos, so unless you've added a custom repo that has Opera, you're going to get an error when the script tries to install it.

Does the error above fit the error i would get if opera couldnt be installed that way?
How could i install Opera, if not tru apt-get?

Btw i just checked, if i type "sudo apt-get install opera" on the command line, it informs me it is in its newest version. Maybe it can be done that way?

> I think you need to initialize variable question before calling until[]
question=0

Umm... What?
Im still a newbie here so :D

> Secondly, you will have to make sure the script is run as with sudo since you are running apt-get install

Same error, even when running the script with sudo

---

### Post by AlphaLexman on 2010-09-12
The third line in your script should be:
```
read question
```

---

### Post by WorMzy on 2010-09-12
[QUOTE="AlphaLexman"]The third line in your script should be:
```
read question
```[/QUOTE]

No it shouldn't.

```
#!/bin/bash
echo "This script will add programs you like to the computer. Press enter to get started."
read
clear
#repeats this until the user asks for exit, otherwise he would have to run it over and over again.
until [ "$question" == "2" ]; do
  echo "Which programs would you like to install? Opera (1) Close (2)"
#asks to install, reads users choice
  read question
  if [ "$question" == "1" ]; then
  #installs opera if user says 1
    sudo apt-get install opera
  elif [ "$question" == "2" ]; then
    #exits if he says 2x
    exit
#If the user types something else, it lets him try again
  else
    echo "I don't understand, use 1 or 2"
  fi
done
```

This works for me.

---

### Post by AlphaLexman on 2010-09-12
my bad, I didn't see the 'read question' later in the script cuz the op quoted instead of coded, sorry.

---

### Post by sharathcshekhar on 2010-09-13
> Umm... What?
Im still a newbie here so

I mean to say, initialize the variable "question" before comparing in until [ $question == 2 ]

```

#!/bin/bash
echo "This script will add programs you like to the computer. Press enter to get started."
read
clear
#repeats this until the user asks for exit, otherwise he would have to run it over and over again.

[COLOR="Red"]question=1 [/COLOR]
until [ $question == "2" ]
```

Or WorMzy suggested, using 
until [ "$question" == "2" ] 
also works

---

### Post by coolness on 2010-09-13
> **AlphaLexman said:**
> my bad, I didn't see the 'read question' later in the script cuz the op quoted instead of coded, sorry.

Yeah i didnt know i could do that :)

> **sharathcshekhar said:**
> I mean to say, initialize the variable "question" before comparing in until [ $question == 2 ]

```

#!/bin/bash
echo "This script will add programs you like to the computer. Press enter to get started."
read
clear
#repeats this until the user asks for exit, otherwise he would have to run it over and over again.

[COLOR="Red"]question=1 [/COLOR]
until [ $question == "2" ]
```

Or WorMzy suggested, using 
until [ "$question" == "2" ] 
also works

Isnt that what i did here? Or am i missing something? Why do i need to 
> 
question=1

---

### Post by WorMzy on 2010-09-13
Because in this statement:
```
until [ $question == "2" ]
```
$question will be expanded to whatever it contains, which, if you haven't given it a value is nothing, so bash will just see

```
until [ == "2" ]
```

And will complain because it's trying to compare nothing with "2". Declaring the variable beforehand will make bash see this:

```
until [ 1 == "2" ]
```

or in my example, it will see this:

```
until [ "" == "2" ]
```

The value will be updated everytime the loop runs, so my solution prevents the error resurfacing if the user just hits enter when prompted for a value.

---

### Post by coolness on 2010-09-13
> **WorMzy said:**
> Because in this statement:
```
until [ $question == "2" ]
```
$question will be expanded to whatever it contains, which, if you haven't given it a value is nothing, so bash will just see

```
until [ == "2" ]
```

And will complain because it's trying to compare nothing with "2". Declaring the variable beforehand will make bash see this:

```
until [ 1 == "2" ]
```

or in my example, it will see this:

```
until [ "" == "2" ]
```

The value will be updated everytime the loop runs, so my solution prevents the error resurfacing if the user just hits enter when prompted for a value.

Hmm....

Im beginning to understand...
But anyway, even with the $question=1 before until it doesnt work, same error :(

---

### Post by WorMzy on 2010-09-13
At which point?

Like I said before, if you just press enter when prompted for a number then you will get the error again, because $question will have no value again. Putting quotation marks around the variable, like I did, is the only way to prevent it.

---

### Post by coolness on 2010-09-14
```

until [ "$question" == "2" ]
do
	echo "Which programs would you like to install? Opera (1) Close (2)"
	#asks to install, reads users choice
	read question 

```

That gives:
```

[: 25: 1: unexpected operator
Which programs would you like to install? Opera (1) Close (2)

```

And then after i press 1 or 2 there, it gives:
```

[: 25: 1: unexpected operator
[: 25: 1: unexpected operator
I dont understand, use 1 or 2
[: 25: 1: unexpected operator
Which programs would you like to install? Opera (1) Close (2)



```

---

### Post by WorMzy on 2010-09-14
I can't reproduce that error. Have you changed more of the script?

---

### Post by coolness on 2010-09-14
> **WorMzy said:**
> I can't reproduce that error. Have you changed more of the script?

Wow, thats weird. I havent changed it as far as i know.
Here it is:
```

#!/bin/bash
echo "This script will add programs you like to the computer. Press enter to get started."
read
clear
#repeats this until the user asks for exit, otherwise he would have to run it over and over again.
question=1
until [ "$question" == "2" ]
do
	echo "Which programs would you like to install? Opera (1) Close (2)"
	#asks to install, reads users choice
	read question
	if [ $question == "1" ]
		then 
	#installs opera if user says 1
		apt-get install opera
	
	elif [ $question == "2" ]
	#exits if he says 2
		then
		exit
	#If the user types something else, it lets him try again
	else
		echo "I dont understand, use 1 or 2"
	fi
done


```

---

### Post by WorMzy on 2010-09-14
Well this is weird, I *can* reproduce the error, but only in dash. It works fine in bash for me.

This leads me to believe that your /bin/bash is a symbolic link to /bin/dash, or you're overriding the shebang by explicitly running the script with dash.

Check your /bin/bash with
```
ls -l /bin/bash
```

If that looks like this:
```
-rwxr-xr-x 1 root root 605848 May 17 01:38 /bin/bash
```
then that's fine, and you must be running the script incorrectly. You should run the script like this:
```
./<scriptname>.sh
```
or
```
bash <scriptname>.sh
```

---

### Post by Alexis Phoenix on 2010-09-14
That was interesting.  I didn't set the script to executable, just ran ```
sh testscript
```I completely forgot that sh isn't bash.  It didn't work.  Duh.  ```
bash testscript
```Small lesson for all Linux users there I think....
OP, if you don't mind me asking, was this just an exercise in scripting, or are you trying to create a front-end to apt?

---

### Post by coolness on 2010-09-15
Yeah wow I didnt realize that when I typed sudo sh script.sh it produced the error. 
Well, it works with ./ so I'm fine. Thanks for all your help guys! 
And yeah, I'm just learning bash, that's why I wrote the script.

---

