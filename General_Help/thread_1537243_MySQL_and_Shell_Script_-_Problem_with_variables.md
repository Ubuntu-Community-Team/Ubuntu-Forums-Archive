---
title: "MySQL and Shell Script - Problem with variables"
date: 2010-07-23
forum: General Help
---

### Post by t0rtura on 2010-07-23
Hello everybody,

I've tried to use mysql with shell scripts but I am with a little problem, I'm trying to get a data value from a table and insert this value in another table using the script below:

I'm using a remote database.

#!/bin/bash

var1=$(mysql -h 10.10.0.89 -N -u root -ppassword -e "SELECT NOME FROM TABLE1 WHERE IP = '10.10.0.2';" DATABASE1)

mysql -h 10.10.0.89 -u root -ppassword -e "INSERT INTO TABLE2 (NOME) VALUES ('$var1');" DATABASE1


When I run the script, tha data value has not been saved into TABLE2.NOME. But the curious thing is, when I open Terminal and paste those script commands manually, it works! What is the problem? Using a script, doesn't work, but manually, using Terminal prompt, everything works fine...

Someone could help me?
Thanks
T0rtura

---

### Post by bigboy_pdb on 2010-07-23
There are a couple of things that I can think of that might be affecting the script.

You might want to try putting "-D" before the databases name (without the quotes).

You might also want to put double quotes around the script that's being run inside the subshell and returned as a variable, meaning it would be:
var1="$(...)"

Also, have you tried printing the variable? If you use 'od -c <<< "$var1"' in the script it should show you if the variable has a newline in it and what it's exact contents are. My guess is that the value that is returned may have a newline in it and the script is not reading it properly.

Furthermore, you should be able to do this in a mysql script without relying on the bash shell. It would only use one connection that way.

---

### Post by clrg on 2010-07-23
The mysql command might not like being run from a script. Some programs check whether a TTY device is available and fail if not.

---

### Post by t0rtura on 2010-07-23
> **bigboy_pdb said:**
> Also, have you tried printing the variable? If you use 'od -c <<< "$var1"' in the script it should show you if the variable has a newline in it and what it's exact contents are. **My guess is that the value that is returned may have a newline in it and the script is not reading it properly.**

The problem was solved, and was something like that you tell... The value of $var1 wasnt correct and I've made a few changes to fix...

Thx a lot
T0rtura

---

### Post by clrg on 2010-07-23
Please mark the thread as solved.

---

