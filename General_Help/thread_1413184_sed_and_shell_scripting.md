---
title: "sed and shell scripting"
date: 2010-02-22
forum: General Help
---

### Post by egghead0 on 2010-02-22
Hi Guys,

I have recently put together an install script to make my life a little easier.

The server is using lighttpd and I wish for the auth mod to be enabled.

For the line:

$HTTP["host"] =~ "127.0.0.1" {

I require the script to call the servers external IP and insert it in place of 127.0.0.1

Can someone please provide assistance with this?

Kind Regards,

egghead0

---

### Post by egghead0 on 2010-02-22
any one have any ideas about this please?

God this furom is busy! lol

---

### Post by mo.reina on 2010-02-22
```
#!/bin/bash

external=$(wget http://www.whatismyip.com/automation/n09230945.asp -O - 2> /dev/null)

echo $external

echo '$HTTP["host"] =~ "127.0.0.1" {' | sed "s/127.0.0.1/$external/"
```

you'll have to adopt it to your script.  the key lines are assigning the external i.p. to the variable *external* and replacing 127.0.0.1 with the variable using sed.
```
sed "s/127.0.0.1/$external/"
```

---

### Post by egghead0 on 2010-02-22
Thank you mo.reina!

I will test it when I get in but that looks about right - appreciate it!

:)

---

### Post by egghead0 on 2010-02-22
Tried:

root@ubuntu:~# external=$(wget [http://www.whatismyip.com/automation/n09230945.asp](http://www.whatismyip.com/automation/n09230945.asp) -O - 2> /dev/null)
root@ubuntu:~# echo $external
86.28.***.***
root@ubuntu:~# cat /etc/lighttpd/lighttpd.conf | sed -e "s/127.0.0.1/$external/" > /etc/lighttpd/lighttpd.conf

as a test in ssh - just wipes my lighttpd.conf to nothing - any ideas?

thanks

egghead0

---

### Post by egghead0 on 2010-02-22
nevermind - sorted it - thanks

---

