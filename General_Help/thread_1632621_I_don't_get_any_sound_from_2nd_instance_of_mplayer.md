---
title: "I don't get any sound from 2nd instance of mplayer"
date: 2010-11-28
forum: General Help
---

### Post by tobytoby on 2010-11-28
I start 2 instances of mplayer from a bash script. However, the 2nd instance of mplayer runs, but there is no sound? (What the scripts are supposed to do is to fade out the mp3:s being played by the first instance of mplayer. Then start a separate mp3-file and when that hasfinished to play, fade in the original mp3:s again.) Everything works and runs, but there is no sound from the separately started mp3 (2nd instance of mplayer). 

Here is the code:
```
#!/bin/bash
#this script starts instance #1 of mplayer

mkfifo mplayer.pipe #controlled from the other script through pipe

mplayer -slave -input file=/home/administrator/script/mplayer.pipe /home/administrator/music/*
```Here is the code for the second instance of mplayer:
```
#!/bin/bash

#the sound of the 1st instance of mplayer gets faded out
echo "set_property volume 100" > /home/administrator/script/mplayer.pipe

COUNT=100
while [ $COUNT -gt 0 ]; do
    sleep 0.03
    echo vardet $COUNT
    echo "set_property volume "$COUNT > /home/administrator/script/mplayer.pipe
    let COUNT=COUNT-1
done
 echo "pause" > /home/administrator/script/mplayer.pipe #pause instance #1
#end of fade out

#the 2nd instance of gets started (it starts but does not sound!)
mplayer /home/administrator/music2/file2.mp3


#when file2.mp3 has quit played, fade in instance #1 of mplayer
echo "set_property volume 0" > /home/administrator/script/mplayer.pipe

COUNT=0
while [ $COUNT -le 100 ]; do
    sleep 0.03
    echo vardet $COUNT
    echo "set_property volume "$COUNT > /home/administrator/script/mplayer.pipe
    let COUNT=COUNT+1
done 
```

---

### Post by tobytoby on 2010-11-28
softvol?

---

