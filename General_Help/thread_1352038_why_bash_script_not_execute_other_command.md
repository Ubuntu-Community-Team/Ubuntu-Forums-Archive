---
title: "why bash script not execute other command?"
date: 2009-12-11
forum: General Help
---

### Post by kkdhf on 2009-12-11
i setup a virtual server with ubuntu-9.04-server-i386.iso in vmware 6.5 , and i write a short bash script like this:
#! bin/bash
echo 'echo me'


and when i execute this script , i get the message: 
**echo me**
i try my best to solve this, but failed. 

i hope to someone can tell me why this happened, and how so solve this?

can u help me?

whatever,thx your reading.

---

### Post by Physical Hook on 2009-12-11
It's /bin/bash ( slash in front of the path ) not bin/bash ;)

---

### Post by soulsource on 2009-12-11
I don't get your point. You made a script that should output 'echo me' and complain that it does?

Maybe what you want is the $(command) structure. This executes the command in brackets and replaces itself by the commands output.

---

### Post by NFblaze on 2009-12-11
What the hell? It's doing exactly what you have wrote it to do?

---

### Post by kkdhf on 2009-12-11
...
in fact ,this will reply 
**me**

because i use backquote ' 
so ,
it will excute like this:
**echo 'echo me'**
**echoe me**
**me**

,and , i check the bash script, 
linux bash script support this type script.
ubuntu ,too.

hope your reply.

---

### Post by Physical Hook on 2009-12-11
I don't get it .. what is the problem ?

---

### Post by kkdhf on 2009-12-11
> **Physical Hook said:**
> It's /bin/bash ( slash in front of the path ) not bin/bash ;)


oh, thx . but my real script is /bin/bash ,,
and , i think this comment can removed.
some articles there is not this comment,and after 
chmod x ,
it can runs too.
in fact , i have one no head comment  runs too.

---

### Post by lisati on 2009-12-11
Two possibilities come to mind: either there's a langauge barrier (the OP's first language isn't English) or our legs are being pulled.

---

### Post by kkdhf on 2009-12-11
> **Physical Hook said:**
> I don't get it .. what is the problem ?


[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

i'm installing postfix,
and make bash to add user and make password,
the add user script like this:
echo "$1" > /tmp/user
**user=`cat /tmp/user | cut -f1 -d "@"`**
**domain=`cat /tmp/user | cut -f2 -d "@"`**
echo "$user@$domain::5000:5000::/home/vmail/$domain/:/bin/false::" >> /etc/dovecot/users

# Create the needed Maildir directories
/usr/bin/maildirmake.dovecot /home/vmail/$domain/$user 5000:5000

# To add user to Postfix virtual map file and relode Postfix
echo $1  $domain/$user/ >> /etc/postfix/vmaps
postmap /etc/postfix/vmaps
postfix reload

in fact, it runs no excute 'cat ....'

---

### Post by Physical Hook on 2009-12-11
Is this what you want ?

```
#!/bin/bash
MSG=`echo me`
echo $MSG
```

---

### Post by kkdhf on 2009-12-11
> **Physical Hook said:**
> Is this what you want ?

```
#!/bin/bash
MSG=`echo me`
echo $MSG
```

My first language is not english ..
sorry to this.

yes .
i think it will get string 'me' to screen ?
right?
but i get string 'echo me' to screen?
i wanna dis. string 'me' to screen.
how?
thx your reply.

---

### Post by Physical Hook on 2009-12-11
```
HUMAN="me"
echo $HUMAN

```

---

### Post by kkdhf on 2009-12-11
> **Physical Hook said:**
> ```
HUMAN="me"
echo $HUMAN

```


if use "", it's real string ,
i wanna to execute some other command like 'echo' .
i descript my detail:
i wanna make md5 to var.
and i type this at console :
**mkpasswd --hash=md5 123**

123 will be encrypt to md5 string.

and now , i put it to bash script like this:
[B]echo 'mkpasswd --hash=md5 123' >> msg
echo $msg[/B]
i want to get encrypted string to $msg.

---

### Post by sarin_cv on 2009-12-11
have a similar query.... I have written a simple script to stop amarok..

#!/bin/sh
echo "stopping amarok" > amarok_out.log
amarok -s


I have tried  to execute this using at command and gnome scheduled tasks.. both does not work.. 
at command shows,
at -f amarok_stop.sh 8:42 AM
warning: commands will be executed using /bin/sh
job 31 at Sat Dec 12 08:42:00 2009

but it will never get executed..

---

### Post by Physical Hook on 2009-12-11
```
PASSWORD="123"
MD5PASSWORD=`mkpasswd --hash=md5 $PASSWORD`
echo "md5: " $MD5PASSWORD

```

---

### Post by kkdhf on 2009-12-11
i get string too..
[B]md5: mkpasswd --hash=md5 123

no execute mkpasswd ,too. 
what occurs this case?
[/B]

---

### Post by Physical Hook on 2009-12-11
Ok, just to verify - create an empty file called sample.sh and paste in the code I just gave you. Open Terminal and execute the following commands ( be sure you are in the right directory ).

```
chmod +x sample.sh
./sample.sh
```Still the same output ?

---

### Post by kkdhf on 2009-12-11
do what u said,
i get string :
**md5: mkpasswd --hash=md5  $PASSWORD**

---

### Post by Physical Hook on 2009-12-11
Please show us the output ( copy and paste **everything** you see - no exceptions ) of:

```
ls -l | grep sample.sh
cat sample.sh
./sample.sh
```

** Replace sample.sh with the actual file name you have there.

---

### Post by kkdhf on 2009-12-11
BTW, Still the same output.

---

### Post by kkdhf on 2009-12-11
can i send email to u?
i use vmware to runs linux.
i cut screen to picture ...

---

### Post by Physical Hook on 2009-12-11
I don't know - you can try .. or attach them here :p

---

### Post by kkdhf on 2009-12-11
**why bash script not execute other command?** 			
 			 			 		   		 		 		i setup a virtual server with ubuntu-9.04-server-i386.iso in vmware 6.5 

i make a picture to show what happen,in this picture ,
i want to make md5 string to variable.
but no execute mkpasswd command.

[IMG]http://220.165.8.72:8002/screen.bmp[/IMG]

and original thread is :
[http://ubuntuforums.org/showthread.php?p=8478979#post8478979](http://ubuntuforums.org/showthread.php?p=8478979#post8478979)

hope u can fix me.

---

### Post by kkdhf on 2009-12-11
thx a lot whatever.
i have post new thread.
[http://ubuntuforums.org/showthread.php?p=8483480#post8483480](http://ubuntuforums.org/showthread.php?p=8483480#post8483480)

---

### Post by bodhi.zazen on 2009-12-11
> **kkdhf said:**
> thx a lot whatever.
i have post new thread.
[http://ubuntuforums.org/showthread.php?p=8483480#post8483480](http://ubuntuforums.org/showthread.php?p=8483480#post8483480)

Threads merged. Please do not start multiple threads on the same topic, it causes duplication of effort and confusion.

---

### Post by bodhi.zazen on 2009-12-11
The problem has to do with the difference between :

single quotes '
double quotes" 
and back tics `

```
#!/bin/bash

MESSAGE="message here"

echo "# no quotes"
echo $MESSAGE

echo "# no double quotes"
echo "$MESSAGE"

echo "# single quotes"
echo '$MESSAGE'

echo "# back tics, error is because the shell is trying to execute a command"
`echo "$MESSAGE"`
```

yields>  ./script                                                                                                                                                    12/11/09  9:36 PM
# no quotes
message here
# no double quotes
message here
# single quotes
$MESSAGE
# back tics, error is because the shell is trying to execute a command
./script: line 15: message: command not found

so look at bash and understand the difference between single quotes , ' , double quotes , " , and back tics , `

[http://www.wiredrevolution.com/bash-programming/single-versus-double-quotes-in-bash](http://www.wiredrevolution.com/bash-programming/single-versus-double-quotes-in-bash)

---

### Post by akashiraffee on 2009-12-11
Ditto.

' = single quote
` = BACK TICK

---

### Post by kkdhf on 2009-12-12
> **akashiraffee said:**
> Ditto.

' = single quote
` = BACK TICK


i make a mistake... 
thx your help , 
and sample is good to me..

my script runs now.

---

