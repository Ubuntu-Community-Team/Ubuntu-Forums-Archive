---
title: "string to be compared treated as command, why?"
date: 2012-03-18
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-03-18
when I run this script:

```

trythisvar=$(sudo ufw status verbose | tr -d -c [:alpha:])
echo $trythisvar
if "$trythisvar" = "some dumb string"
    then echo "The damn thing's alive!"
    else echo "No, it doesn't equal that."
fi

```in a terminal I get this output:

```

me@me-dt:~$ /home/me/0_my_stuff/scripts/ufw-testing-UNFINISHED/trythis.sh 
Statusinactive
/home/me/0_my_stuff/scripts/ufw-testing-UNFINISHED/trythis.sh: line 3: Statusinactive: command not found
No, it doesn't equal that.
me@me-dt:~$ 

```which seems to indicate that in line 3 the expansion of trythisvar is treated as a command despite being enclosed by double quotes and appearing in the context of a string comparison. Would someone mind giving me a hint why this is so? Thanks for your time to read this, even if you are as puzzled as I am, which isn't likely.

---

### Post by HiImTye on 2012-03-18
ignore this, Im an idiot mixing up differing things, one sec Ill fix your script

---

### Post by Vaphell on 2012-03-18
put condition inside square brackets

---

### Post by HiImTye on 2012-03-18
here you are:
```
#!/bin/bash
trythisvar=$(sudo ufw status verbose | tr -d -c [:alpha:])
if [ "$trythisvar" = "Statusinactive" ] ; then
  echo "UFW Inactive!"
else
  echo $trythisvar
fi
```sorry for fixing your indenting and style, it bothers me when my scripts all don't look pretty

edit: made it actually functional

---

### Post by Dreamer Fithp Apprentice on 2012-03-18
Aha!
Thank you, HiImTye & Vaphell!

HiImTye, my indentions are merely the chaotic result of random cosmic rays and thermal noise in my brain so it's no loss. ;-)

---

### Post by Dreamer Fithp Apprentice on 2012-03-18
For the benefit of those who might read this thread because they are looking for something similar:

Note that the conditional is wrapped not just in square brackets but also by spaces. So it is bracket space condition space bracket, as in HiImTye's example. Just reading the code it is easy to not notice the spaces.

---

### Post by matt_symes on 2012-03-19
Hi

In case $trythisvar is empty (trythisvar=$(sudo ufw status verbose | tr -d -c [:alpha:]) return an empty string for some reason)

```
if [ x"$trythisvar" = x"Statusinactive" ] ; then
```

Otherwise you get (when interpreted by the shell)

```
if [  = "Statusinactive" ] ; then
```

and this will error.

Kind regards

---

