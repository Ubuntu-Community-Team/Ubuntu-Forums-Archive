---
title: "Why don't I have the permissions to save this file?"
date: 2009-12-09
forum: General Help
---

### Post by redsoxsrule424 on 2009-12-09
I need to save the code below into my /usr/local/bin directory as 'odtvrecord' however when I try to save it using gedit it says I do not have the permissions to save it. Is there a command that I can use so that I can save it? Thanks!

The code:

#!/bin/bash

FILEPART=1
FILENAME="output"

# Construct filename to output to
if [ "$1" ]
then
  FILENAME="$1"
fi

# Iterate the part number
if [ "$2" ]
then
  FILEPART=$2
fi

# Use cURL to capture the stream
curl [http://bglive-a.bitgravity.com/twit/live/high](http://bglive-a.bitgravity.com/twit/live/high) --ignore-content-length -o $FILENAME.$FILEPART.flv

# Re-connect if the connection is lost
# If statement checks for return values of cURL which indicate that the stream
# could not be connected to and no data besides the http headers were received.
if [ $? -eq 1 -o $? -eq 2 -o $? -eq 5 -o $? -eq 6 -o $? -eq 52 ]
then
  sh $O $FILENAME $FILEPART
else
  sh $0 $FILENAME $(($FILEPART+1))
fi

exit

---

### Post by audiomick on 2009-12-09
try putting sudo before the gedit command
```
sudo gedit path_and_file_name
```
you will be asked for you password, it is the one you log on with.

---

### Post by redsoxsrule424 on 2009-12-09
Thanks!

---

### Post by Miljet on 2009-12-09
Please do not use sudo with gedit!!  Use gksudo instead
```
 gksudo gedit path_and_file_name
```

See this link for explanation:  [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

