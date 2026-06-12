---
title: "Help needed with bash script controlling directory size"
date: 2009-10-29
forum: General Help
---

### Post by dscheste on 2009-10-29
Dear Team,

I need some help with a bash script I have been working on recently. This script is going to represent the final step in converting recordings by a Mythtv backend for blackberry and moving them into a directory that is going to be synchronized with my BB.

Because the memory card on my bb is not that huge, I want to be able to enforce the size of the directory where the converted recordings have been placed.

Below is what I have hacked together, but the code runs and deletes all files in the directory, I suspect there is a problem with dynamically updating the DIRSZE (variable responsible for the current size of the directory).

Could you please have a look at the code below and suggest a fix? Alternative approaches to enforce the size of a directory are also welcome. As you can see, I am deleting the oldest files in order to bring the size of the directory to the desired value.

Thank you,
dscheste


```
#!/bin/sh
MYDIRECTORY="/bb/cutlist/"
NUMBEROFFILES=$(ls -t $MYDIRECTORY)
MYSIZE=2048
TODELETE=$(ls $MYDIRECTORY -t | tail -1)
DIRSIZE=$(du -sm $MYDIRECTORY | cut -f 1)
for file in $NUMBEROFFILES
do
if [ "$DIRSIZE" -ge "$MYSIZE" ] ; then
        rm -v "$MYDIRECTORY$TODELETE"
        unset $TODELETE
        TODELETE=$(ls $MYDIRECTORY -t | tail -1)
fi
        unset $DIRSIZE
        $DIRSIZE=$(du -sm $MYDIRECTORY | cut -f 1)
done;
echo "Brought down to just  $DIRSIZE"
exit 0

```

---

### Post by dscheste on 2009-10-30
I think I figured it out.

A couple of things went wrong. Updating variable value within a loop isn't that straightforward, apparently.

Here is what I have come up with and it works. The limit size for the directory one need to setup in bytes though, but I am fine with it. Here is the code to enforce 1Gb size.

```
#!/bin/sh
MYDIRECTORY="/bb/cutlist/"
MYSIZE=1073741824
while [ $(ls -lR $MYDIRECTORY | awk '{total +=$5};END {print total }') -gt $MYSIZE ]; do
rm -v "$MYDIRECTORY$(ls $MYDIRECTORY -t | tail -1)"
#echo $(ls -lR $MYDIRECTORY | awk '{total +=$5};END {print total }')
#echo Brought down to $(ls -lR $MYDIRECTORY | awk '{total +=$5};END {print total/1024/1024 "Mb" }')
done
#echo $(ls -lR $MYDIRECTORY | awk '{total +=$5};END {print "Directory size is: " total/1024/1024 "Mb" }')
exit 0

```

---

