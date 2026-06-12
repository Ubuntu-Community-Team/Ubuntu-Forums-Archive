---
title: "echo $ sign in script"
date: 2011-05-26
forum: General Help
---

### Post by jaes84 on 2011-05-26
How would i go about echoing stuff like $database, but as the word, not the variable?
for example:
$l = "$database = $db" where $database is supposed to be the word, while $db is the variable

---

### Post by m_duck on 2011-05-26
Either use a backslash, or single quotes, i.e.
```
echo "\$database"
```
```
echo '$database'
```
The former escapes the '$' character to print it literally, and the latter takes the entire string as a literal, due to the use of the single quotes rather than double quotes.

---

### Post by jaes84 on 2011-05-26
Thanks, but now i have another problem :( whenever i run the script, it says 
test.sh 3: l: not found
This is the script:
```

#!/bin/bash
l = "\$k"
echo $l

```

---

### Post by m_duck on 2011-05-26
You need to remove the spaces around the equals sign. BASH doesn't like that.

---

### Post by jaes84 on 2011-05-26
Sweet, thank you so much!

---

### Post by m_duck on 2011-05-26
You're welcome.

---

### Post by jaes84 on 2011-05-26
Sorry, but now i have another problem
Whenever i try to make a new string, it spits out this error
```

: bad variable name
$db_database = ;

```
Here is the script
```

#!/bin/bash
read -p "Enter database name: " dbname
newdb="\$db_database = "$dbname";"
echo $newdb

```

---

### Post by jaes84 on 2011-05-26
I have also tried this, but to no avail:
```

#!/bin/bash
read -p "Enter database name: " dbname
newdb="\$db_database = \"$dbname\";"
echo $newdb

```

---

### Post by tgm4883 on 2011-05-26
I just copied from your post and it works here

```
#!/bin/bash
read -p "Enter database name: " dbname
newdb="\$db_database = "$dbname";"
echo $newdb
```

---

### Post by m_duck on 2011-05-26
Reading the user input to the variable dbname is fine.

Assuming you want to echo the string **$db_database = user_input;** you need to have the following, since for $dbname you actually want BASH to expand the variable to insert its contents into the string.
```
#!/bin/bash
read -p "Enter database name: " dbname
newdb="\$db_database = $dbname;"
echo $newdb
```

---

### Post by jaes84 on 2011-05-26
> **m_duck said:**
> Reading the user input to the variable dbname is fine.

Assuming you want to echo the string **$db_database = user_input;** you need to have the following, since for $dbname you actually want BASH to expand the variable to insert its contents into the string.
```
#!/bin/bash
read -p "Enter database name: " dbname
newdb="\$db_database = $dbname;"
echo $newdb
```

Thanks, but i also need the quotes

---

### Post by m_duck on 2011-05-26
Ah ok, I see what you're going for... One mo.

EDIT: Here we go.

```
#!/bin/bash
read -p "Enter database name: " dbname
newdb="\$db_database = \"$dbname\";"
echo $newdb
```

EDIT 2: And thus on reflection, I'm not sure why your earlier script didn't work... It looks the same. Weird. The above works here anyway.

EDIT 3: They're *exactly* the same. Much oddness...

---

### Post by jaes84 on 2011-05-26
Thanks, but it still doesn't work :(
any ideas?

---

### Post by m_duck on 2011-05-26
Can you define *doesn't work*? How are you running the script? Any errors? Incorrect output?

If I run the above, and type in ***my_db*** at the prompt, the string I get returned is ***$db_database = "my_db";***. Is this not what was being aimed for?

---

### Post by matt_symes on 2011-05-26
Hi

Works here as well
```

matthew@matthew-laptop:~$ cat test.sh 
#!/bin/bash
read -p "Enter database name: " dbname
newdb="\$db_database = \"$dbname\";"
echo $newdb
matthew@matthew-laptop:~$ bash test.sh 
Enter database name: hello
$db_database = "hello";
matthew@matthew-laptop:~$ bash -x test.sh 
+ read -p 'Enter database name: ' dbname
Enter database name: hello
+ newdb='$db_database = "hello";'
+ echo '$db_database' = '"hello";'
$db_database = "hello";
matthew@matthew-laptop:~$  
```

Kind regards

---

### Post by jaes84 on 2011-05-26
I execute the script by doing sudo sh ./test2.sh or sh test2.sh
When i do ./test2.sh, then i get the following error:
```

bash: ./test2.sh /bin/bash^M: bad interpreter: No such file or directory

```Otherwise, i just get this error after entering the variable:
```

: bad variable name

```
EDIT: When i do bash test2.sh, i get this error, after entering the variable
```

': not a valid identifierdbname

```
and no, that is not a typo

---

### Post by m_duck on 2011-05-26
Unless there are other parts of the script that do stuff requiring root permissions, it is not necessary to it with sudo.

The first error implies that the first line isn't as it seems, and contains a rogue escape character. Can you type the script out into a new file? Or even completely delete the first line and re-add it.

If you add the line back ***./test2.sh*** should run it without a problem. You could run it without the declaration at the beginning as matt_symes did by running ***bash test2.sh***. The former reads the first file to check what interpreter to use and where it is, the second specifies the interpreter with which to run the script first.

EDIT: Ah, a quick bit of Googling as said something to me - did you first create the script on a Windows box? Certain delimiters in Windows editors like notepad (i.e. end of line characters) are not the same as in *nix, and I guess some residuals of that have remained if that is the case.

---

### Post by Vaphell on 2011-05-26
you defined default shell with the hashbang line - it's bash and you run the script with sh
just change executable bit to true with chmod +x and run the script with ./script.sh

also ^M indicates you wrote the script in windows which ends line with 2 bytes: newline and carriage return (\n and \r) while linux uses only \n. That matters

```
sed -r -i 's:\s*$::' script.sh
``` should fix that (expression removes whitespaces at the end of line)

---

### Post by jaes84 on 2011-05-26
Right, so i tried removing, then running bash test2.sh, and i still get the "': not a valid identifierdbname"
When i re-add it, it still prints out the /bin/bash/^M, command not found

---

### Post by jaes84 on 2011-05-26
Thanks So much!, i did write the script in windows, but i did not know it would have this effect. Can you reccomend any editors in windows, that do not do this?

---

### Post by matt_symes on 2011-05-26
Hi

Copy and paste this into a terminal and hit enter

```
cat <<"EOF" > test2.sh
#!/bin/bash
read -p "Enter database name: " dbname
newdb="\$db_database = \"$dbname\";"
echo $newdb
EOF
bash test2.sh
```EDIT: I see you just fixed it :D

Kind regards

---

### Post by m_duck on 2011-05-26
Vim and Emacs will both work in Windows but both have associated learning curves if you haven't used them before. I suspect Notepad++ (which seems to be the most popular choice for text editing in Windows) would have an option to use Linux special characters.

---

### Post by jaes84 on 2011-05-26
> **m_duck said:**
> Vim and Emacs will both work in Windows but both have associated learning curves if you haven't used them before. I suspect Notepad++ (which seems to be the most popular choice for text editing in Windows) would have an option to use Linux special characters.

I am quite experienced with Vim, and Ubuntu for that matter, i use it at work, but i use Windows for games, and common programming. I was using Notepad++. I will look around for this fix for notepad++, and if not, i will just use vim. Thank you everyone for your help!

---

### Post by Vaphell on 2011-05-26
read this to understand the problem and see how to fix it using standard tools :)
[http://en.wikipedia.org/wiki/Newline](http://en.wikipedia.org/wiki/Newline)

---

### Post by m_duck on 2011-05-26
> **jaes84 said:**
> I am quite experienced with Vim, and Ubuntu for that matter, i use it at work, but i use Windows for games, and common programming. I was using Notepad++. I will look around for this fix for notepad++, and if not, i will just use vim. Thank you everyone for your help!

Ah ok sorry, I'm never quite sure - since as you know then, recommending Vim to someone who has never used it before may result in a few raised eyebrows! I also apologise that I cannot be much help in terms of Notepad++ too. Good luck finding a solution :)

---

### Post by jaes84 on 2011-05-26
Epic, it seems all i had to do was to go to Edit->EOL Conversion, and click UNIX conversion
Just for future reference :D

---

### Post by jaes84 on 2011-05-26
> **m_duck said:**
> Ah ok sorry, I'm never quite sure - since as you know then, recommending Vim to someone who has never used it before may result in a few raised eyebrows! I also apologise that I cannot be much help in terms of Notepad++ too. Good luck finding a solution :)
So true :D

---

### Post by jaes84 on 2011-05-26
This is actually a bit off-topic, but would this work to replace a whole line with the variable?
```

sed '2s/.*/$newdb/g' config.php

```

When i do this with perl, this is what happens
in the file:
 = "test";

---

### Post by Vaphell on 2011-05-26
no, single quotes prevent variable expansion
you'd get literal $newdb

try
```
sed '2s/.*/'"$newdb"'/g'
```

---

### Post by jaes84 on 2011-05-26
> **Vaphell said:**
> no, single quotes prevent variable expansion
you'd get literal $newdb

try
```
sed '2s/.*/'"$newdb"'/g'
```
Epic, now for the last question, how do i stop sed from outputting the whole file whenever i run sed?

---

### Post by Vaphell on 2011-05-26
you want to modify file in place?
you need to add -i parameter because by default sed reads file and prints the result to console, -i actually changes the file

```
sed -i '2s/.*/'"$newdb"'/g' config.php
```

alternatively you can redirect output to another file
```
sed '2s/.*/'"$newdb"'/g' config.php > new_config.php
```

if you have any doubts about some command, try running it with **--help** switch. Most of the time you'll get condensed information about the options at hand

---

