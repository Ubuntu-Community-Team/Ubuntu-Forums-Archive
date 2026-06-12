---
title: "Script help"
date: 2011-09-23
forum: General Help
---

### Post by Diametric on 2011-09-23
Hello,

How do I set a variable with multiple data sets?  Meaning, I want to set a variable to equal 4 different ip's.  

```
variable=10.1.5.3, 10.2.5.3, 10.100.1.10 and 10.100.1.11
```

I know the above isn't correct, but that's what I'm looking for, how to get all thos IP's set as one variable.

Thanks in advance for your help!

Forgot to mention that this is a bash script...

---

### Post by Azdour on 2011-09-23
Hi,

Are you looking basically for an array, e.g.:

```

#!/bin/bash
variable=(10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11)
echo ${variable[0]}
echo ${variable[1]}
echo ${variable[2]}
echo ${variable[3]}
echo ${variable[*]}
```

---

### Post by dave01945 on 2011-09-23
you could set it as an array

```
variable=(ip1 ip2 ip3 ip4)
```

then to echo them just as an example

```
echo "${variable[1]}"
ip1

echo "${variable[2]}"
ip2

echo "${variable[3]}"
ip3

echo "${variable[4]}"
ip4

echo "${variable[@]}"
ip1 ip2 ip3 ip4
```

hopefully this is what you was after

--EDIT--

i need to learn to type quicker :)

---

### Post by Diametric on 2011-09-23
Thanks for your reply.  I don't think so.  I tried your example and when I:

```
echo $variable
```

it returns only the first IP, I need it to return all 4 IP's.  Does that make sense?  Just trying to be as clear as possible...sometime I get confures...lol

Thanks!

---

### Post by Diametric on 2011-09-23
It looks like if I simply quote it, it returns what I need.

```
variable="10.1.5.3 10.2.5.3 10.1.100.10 10.1.100.11"
```

Does the trick!

Thanks for the help...

---

### Post by nothingspecial on 2011-09-23
Hi,

```
~$ variable=(10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11)
~$ echo "${variable[@]}"
10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11
```

---

