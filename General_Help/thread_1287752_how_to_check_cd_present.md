---
title: "how to check cd present"
date: 2009-10-10
forum: General Help
---

### Post by sn0m on 2009-10-10
Hi guys
I want to condition my script to check if cdrw media is present, and if so to go ahead and blank it and then to record some file.wav that I have dumped using mplayer from a internet radio.
So is there a way for me to check in command line that disk is present?
Thanks in advance
Sokol

---

### Post by delcypher on 2009-10-10
Sorry this is the best I could come up with. It's kind of ugly I couldn't find a tool that did everything I wanted to cd/dvd drives so this will have to do. No doubt someone can come up with something better.

 It requires cdrao and dvd+rw-mediainfo be installed (they are on my system by default)

set DRIVE to the drive you want to use

```
#!/bin/bash

#SET your drive here
DRIVE=/dev/sr0
#check there is a disc present
if [ $( dvd+rw-mediainfo $DRIVE 2>&1 | grep -c "non-DVD media mounted") -eq 1 ]; then
echo "Disc present..."

#unmount disc drive (CD/CDRW/DVD will be automounted in ubuntu if it contains data)
echo "unmounting disc..."
umount $DRIVE

#check if disc is unmounted (cdrao command does not work if disc is mounted)
if [ $(mount | grep -c $DRIVE) -eq 0 ]; then

#okay we know there is a disc present, so let's see if we can write to it
CDRW=$( cdrdao disk-info --device $DRIVE 2> /dev/null | grep CD-RW | awk '{print $3}' | grep -c yes);
CDR=$( cdrdao disk-info --device $DRIVE 2> /dev/null | grep "CD-R empty" | awk '{print $4}' | grep -c yes);

if [ $CDRW -eq 1 ]; then
echo "CDRW loaded"
## add CDRW writting commands here
fi

if [ $CDR -eq 1 ]; then
echo "CDR empty loaded"
#add CDR writting commands here
fi

if [ $CDR -ne 1 -a $CDR -ne 1 ]; then
echo "No writtable medium inserted"
fi


else
echo "Error disc is mounted, cannot access!"
fi

else
echo "No disc in drive!"
fi

```

I've tested it with CDRs and that works but I don't have any CDRWs to test the script with. Any questions about how it works then ask me.

---

### Post by sn0m on 2009-10-12
thanks buddy, interesting script. I will study and try it. Hopefully will work ok.
Regards
Sokol

---

