---
title: "sed -i problems"
date: 2012-04-19
forum: General Help
---

### Post by cj13579 on 2012-04-19
hi all,

I have a script that I am running and part of it inserts some lines into a config file using sed:

```
sed -i '19 i\  stuff to insert' ./config.yml
```

This works on one of my ubuntu boxes but not the other and I can't for the life of me work out why! The filesystem permissions look to be the same:

working:
```
$ ls -l | grep config.yml
-rwxr-xr-x 1 www-data www-data   3301 2012-04-19 19:00 config.yml

```
not working:
```
$ ls -l | grep config.yml
-rwxr-xr-x 1 www-data www-data    281 2012-04-19 14:02 config.yml

```

When I run the sed command from the command line I get no error message and the return codes seems to be fine. However, I don't see any stuff in the file:
```
$ sed -i '19 i\  stuff to insert' ./config.yml
$ echo $?
0
$

```
I have even checked to make sure that they are running the same version of sed:
working:
```
$ uname -a
Linux q2server 2.6.32-38-generic-pae #83-Ubuntu SMP Wed Jan 4 12:11:13 UTC 2012 i686 GNU/Linux
$ sed --version
GNU sed version 4.2.1

```
not working:
```
$ uname -a
Linux ubuntu 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux
$ sed --version
GNU sed version 4.2.1

```

Any help as always is greatly appreciated!

---

### Post by papibe on 2012-04-19
Hi cj13579.

My first guess is that one that doesn't work hasn't more that 19 lines.

Could you post the result of this commands on both machines?
```
wc -l config.yml
```
Regards.

---

### Post by cj13579 on 2012-04-19
Ah ha! Genius - that was exactly the problem. To get round it I just stuck a little condition in to add another line fist:

```
if [[ $x -ge $y ]] ; then
   sed -i '$ a\ ' $CONF
fi
```

I had another one similar later on in the script where I was trying to work with an empty file. I just changed the methodology if and when there are no lines in the file:

```
x=$(wc -l $APP_HOME/config.txt | cut --fields=1 --delimiter=' ')
if [[ $x -eq 0 ]] ; then
   echo "$sm:$loc/$star" >> $APP_HOME/config.txt
else
   sed -i "$ a\
   $sm:$loc/$star" $APP_HOME/config.txt
fi
```

Many thanks for your great help and swift response.

---

