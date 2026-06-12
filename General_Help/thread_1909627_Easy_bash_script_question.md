---
title: "Easy bash script question"
date: 2012-01-15
forum: General Help
---

### Post by warmnscsi on 2012-01-15
can someone explain why this scrpt would work in fedora 13 and not in newer versions. I'm currently using centOS6 which I think is based off of fedora 15 or 16

```
#!/bin/bash
if [ $1="start" ]
then
echo "The sample daemon has started"
sleep 2
elif [ $1="stop" ]
then
echo "The sample daemon has been stopped"
sleep 2
elif [ $1="restart" ]
then
echo "The sample daemon has been restarted"
sleep 2
fi
```

I keep getting > [root@localhost ~]# service sample start
/etc/init.d/sample: line 2: if[start = start]: command not found
/etc/init.d/sample: line 3: syntax error near unexpected token `then'
/etc/init.d/sample: line 3: `then'


---

### Post by TeoBigusGeekus on 2012-01-15
Try with this
```
#!/bin/bash
if [[ $1 == start ]]
then
echo "The sample daemon has started"
sleep 2
elif [[ $1 == stop ]]
then
echo "The sample daemon has been stopped"
sleep 2
elif [[ $1 == restart ]]
then
echo "The sample daemon has been restarted"
sleep 2
fi
```
Notice the spaces before and after ==.

---

### Post by papibe on 2012-01-15
I can only comment on my version, 4.1.5(1) on 10.04:

You need a space to separate the symbol '=' and the expressions. Change this
```
if [ $1="start" ]
```
For this:
```
if [ $1 = "start" ]
```
You may even want to quote your variables like this:
```
if [ "$1" = "start" ]
```
Hope it helps.
Regards.

---

### Post by warmnscsi on 2012-01-16
> **TeoBigusGeekus said:**
> Try with this
```
#!/bin/bash
if [[ $1 == start ]]
then
echo "The sample daemon has started"
sleep 2
elif [[ $1 == stop ]]
then
echo "The sample daemon has been stopped"
sleep 2
elif [[ $1 == restart ]]
then
echo "The sample daemon has been restarted"
sleep 2
fi
```Notice the spaces before and after ==.

That worked, thanks! Wish there was some way to give you rep. Papibe thanks for trying to help, it didn't work with CentOS6.

---

