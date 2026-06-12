---
title: "Replace special character with a script"
date: 2011-03-12
forum: General Help
---

### Post by sakishrist on 2011-03-12
Greetings,

I need a script that will replace '/' in a variable with '\'

I have tried the following:```
y=$(echo $1|sed 's/\//\\/g')
```
The thing is that this approach does not always work. Here is an example:```
user@pc:~$ sh script.sh /usr/**[COLOR=Red]v[/COLOR]**ar/sakis.txt
z:\usr
      ar\sakis.txt

user@pc:~$ sh script.sh /usr/**[COLOR=Red]t[/COLOR]**ar/sakis.txt
z:\usr    ar\sakis.txt

```Is there a way to treat those characters?

Thanks in advance!

---

### Post by kaibob on 2011-03-12
You are using the dash shell, which interprets \t and \v as horizontal and vertical tabs. Try using the bash shell, which does not do this unless specifically enabled. To run the bash shell put #!/bin/bash on the first line of the shell script and do not use sh when running the shell script. If this does not help, post the exact script you are using.

---

### Post by Diametric on 2011-03-12
> **kaibob said:**
> You are using the dash shell, which interprets \t and \v as horizontal and vertical tabs. Try using the bash shell, which does not do this unless specifically enabled. To run the bash shell put #!/bin/bash on the first line of the shell script and do not use sh when running the shell script. If this does not help, post the exact script you are using.

^^This is why I love these forums...

---

### Post by sakishrist on 2011-03-13
> **kaibob said:**
> You are using the dash shell, which interprets \t and \v as horizontal and vertical tabs. Try using the bash shell, which does not do this unless specifically enabled. To run the bash shell put #!/bin/bash on the first line of the shell script and do not use sh when running the shell script. If this does not help, post the exact script you are using.

Thanks a lot! Now it is working very well. :D

---

