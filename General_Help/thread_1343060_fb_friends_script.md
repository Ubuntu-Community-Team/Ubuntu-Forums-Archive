---
title: "fb friends script"
date: 2009-12-01
forum: General Help
---

### Post by bluethundr on 2009-12-01
Hi There..

I'm trying to write a fun little proglet that lets you know about changes in your friends list on facebook. That is anytime someone either friends you or unfriends you you will know about it from this app. The latter is especially informative since facebook doesn't let you know the identity of people who unfriend you.

```

#!/bin/bash

DATE=`date +%e-%m-%y`
WDIR=~/Desktop/friendlists/
FRIENDS=$(fbcmd FRIENDS | awk '{ print $2 " " $3 }')

echo "Seeing who today's friends are"
echo "Today is $DATE"

if [ ! -d $WDIR ]; then
mkdir $WDIR
awk '{print $FRIENDS}' $WDIR/ref.txt
fi

if [ -e $WDIR/ref.txt ]; then
awk '{print $FRIENDS}' $WDIR/friends-$DATE.txt
LIST=$(diff $WDIR/friends-$DATE.txt $WDIR/ref.txt)

echo "Friends Lost"
echo "------------"
grep "<" $LIST | awk '{ print $2 " " $3 }'
echo " "
echo "Friends Gained"
echo "--------------"
grep ">" $LIST | awk '{ print $2 " " $3 }'
fi 

```

This is the error I get:

```

mazdayasna:friendlists bluethundr$ ./friends.sh
Seeing who today's friends are
Today is  1-12-09
awk: can't open file /home/bluethundr/Desktop/friendlists//friends-
 source line number 1
diff: extra operand `/home/bluethundr/Desktop/friendlists//ref.txt'
diff: Try `diff --help' for more information.
Friends Lost
------------

```

Once we get this working I'm sure plenty of people will find this interesting to use, especially if you have a lot of fb friends like I do.

Cheers

---

