---
title: "file redirection help, please"
date: 2011-09-26
forum: General Help
---

### Post by Diametric on 2011-09-26
Hello,

I am writing a script where I set a variable:

```
var="10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11"
```

How do I then take that variable and write it to a file in my script?  I am currently using:

```
else cat $var > /etc/resolv.conf
```

But it is vailing out saying 
"cat: 10.1.5.3: No such file or directory
cat: 10.2.5.3: No such file or directory
cat: 10.100.1.10: No such file or directory
cat: 10.100.1.11: No such file or directory"

What I want it for my variable to be come (overwrite) the contents of the file.  What am I missing?

Thanks!

---

### Post by matt_symes on 2011-09-26
Hi

Try
[FONT=monospace]
[/FONT]```
else echo $var > /etc/resolv.conf
```

Make sure the script is executable and run as root.

Kind regards

---

### Post by Diametric on 2011-09-26
Thnaks for your reply.  I tried echo, but I got the same error.  Here is the whole script:

```
resolvconfA="10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11"
resolvconfB="10.2.5.3 10.1.5.3 10.101.1.10 10.100.1.10"
defaultconf="10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11"
ip="$(ifconfig | egrep -A1 -i eth | grep "inet addr" | tr -s " " | cut -d " " -f 3 | cut -d : -f 2 | cut -d . -f 1,2)"

if [ $ip = 10.1 ] || [ 10.100 ];
        then cat $resolvconfA > /etc/resolv.conf

elif [ $ip = 10.2 ] || [10.101 ];
        then cat $resolvconfB > /etc/resolv.conf

else echo $defaultconf > /etc/resolv.conf

fi
```

---

### Post by matt_symes on 2011-09-26
Hi

```
**#!/bin/bash**
resolvconfA="10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11"
resolvconfB="10.2.5.3 10.1.5.3 10.101.1.10 10.100.1.10"
defaultconf="10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11"
ip="$(ifconfig | egrep -A1 -i eth | grep "inet addr" | tr -s " " | cut -d " " -f 3 | cut -d : -f 2 | cut -d . -f 1,2)"

if [ $ip = 10.1 ] || [ 10.100 ];
        then **echo** $resolvconfA > /etc/resolv.conf

elif [ $ip = 10.2 ] || [10.101 ];
        then **echo** $resolvconfB > /etc/resolv.conf

else **echo** $defaultconf > /etc/resolv.conf

fi

```

Kind regards

---

### Post by Diametric on 2011-09-26
That fixed it, thank you!  Can you explain why the cat command caused the script to fail where the echo command allowed it to run?

---

### Post by WorMzy on 2011-09-26
cat, used in the way you're using it, reads the contents of one or more _files_, not variables. There is another way to use cat, but in that case it reads standard input, and not variables, so it would have a similar problem.

echo, on the other hand, *can* read variables.

---

### Post by sisco311 on 2011-09-26
cat concatenates files. It expects a file name as an argument. echo displays a line of text.

Also [ 10.100 ] is always true, you probably want something like:
```
if [[ "$ip" == 10.1 ]] || [[ "$ip" == 10.100 ]] ...
```

See BashFAQ #31 (link in my sig) and [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

---

### Post by matt_symes on 2011-09-26
Hi

The cat command concatenates files so it is looking for a list of files to concatenate and it cannot find the files.

From 

```
man cat
```

> CAT(1)                                                                                    User Commands                                                                                   CAT(1)

NAME
       cat - concatenate files and print on the standard output

Kind regards

---

### Post by Diametric on 2011-09-26
Awesome.  I appreciate everyone's help.

---

### Post by Diametric on 2011-09-26
> **sisco311 said:**
> cat concatenates files. It expects a file name as an argument. echo displays a line of text.

Also [ 10.100 ] is always true, you probably want something like:
```
if [[ "$ip" == 10.1 ]] || [[ "$ip" == 10.100 ]] ...
```

See BashFAQ #31 (link in my sig) and [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

I actually changed it to:

```
if [ $ip = 10.1 -o $ip = 10.100 ];
```

Which seems to work.  Thanks for the catch...it would have rendered half of my script moot.

---

### Post by sisco311 on 2011-09-26
> **Diametric said:**
> I actually changed it to:

```
if [ $ip = 10.1 -o $ip = 10.100 ];
```

Which seems to work.  Thanks for the catch...it would have rendered half of my script moot.

In bash, we prefer [[ (the new test command) over [ for comparing strings, but that should work too. Anyway, you should always quote your expansions:
```
if [ "$ip" = 10.1 -o "$ip" = 10.100 ]
```

---

### Post by Diametric on 2011-09-26
For what it's worth, I ended up going with a case statement instead of a bunch of if, then's and elifs.  Here it is:

```
resolvconfA="nameserver 10.1.5.3 search blank.com blank.com 10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11"
resolvconfB="nameserver 10.1.5.3 search blank.com blank.com 10.2.5.3 10.1.5.3 10.101.1.10 10.100.1.10"
defaultconf="nameserver 10.1.5.3 search blank.com blank.com 10.1.5.3 10.2.5.3 10.100.1.10 10.100.1.11"
ip="$(ifconfig | egrep -A1 -i eth | grep "inet addr" | tr -s " " | cut -d " " -f 3 | cut -d : -f 2)"

case $ip in 
        10\.1\.* ) echo $resolvconfA > /etc/resolv.conf ;;

        10\.2\.* ) echo $resolvconfB > /etc/resolv.conf ;;

        172\.16\.1\.* ) echo $resolvconfA > /etc/resolv.conf ;;

        172\.16\.2\.* ) echo $resolvconfB > /etc/resolv.conf ;;

        * ) echo $defaultconf > /etc/resolv.conf ;;

esac
```

---

