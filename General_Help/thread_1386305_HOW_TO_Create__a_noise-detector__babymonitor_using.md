---
title: "HOW TO: Create  a noise-detector / babymonitor using nothing but alsa-tools and grep"
date: 2010-01-20
forum: General Help
---

### Post by weblordpepe on 2010-01-20
Hi there.

Lately I discovered a very cheap and easy way to make a script which can detect if noise is heard on a microphone, and then do stuff.

I had the need to figure out when my (mentally disabled) cat was crying, so I was looking at the datastream of arecord whilst piped to the terminal. I found out that if noise is detected, the random garbage shows some alphanumeric characters, and if theres just silence, you just see garbage.

So using Grep, I figured I could capture if noise was heard. And it works. Here's the code below. This script is capable of detecting when noise begins and ends. The script automatically adjusts its buffer size for performance.

You can then rig it to do whatever you like. I give this away under the GPL 2 terms:

```

#!/bin/bash
#noise detector by weblordpepe. 
#determines when noise has started and when noise has stopped.

# set variables up for initial loop
noisethen="no"  # 'was noise heard on last loop?'
chunklen="1" # length of noise buffer to process

while (( 1 == 1 ))
do
 currenttime=$(date +%s)	 #unix time timestamp

 arecord -d $chunklen > /dev/shm/pwnd.wav  2> /dev/null # lol pwned. redirect sterror to null
 chunk=$(cat /dev/shm/pwnd.wav) #assigning a cat output to a variable converts to 1 line easily.

 heardchars=$(echo $chunk | grep 'z' | grep 't' | wc -l ) #hearing these chars means noise. strange but this actually works.


  # determine if current block is noise 
 noisethen=$noisenow #remember
 if (( $heardchars > 0 )) ; then
  noisenow="yes"

   #   RIG STUFF HERE FOR REALTIME NOISE ACTIONS
 else
  noisenow="no"
  #    RIG STUFF HERE FOR REALTIME SILENCE ACTIONS
 fi




 ###########   
 ### Detemine if noise has just started, still occuring, stopped, or still silence.
 # not only can you rig stuff here, but it also determines the length of the buffer chunks (performance tweak).

 if [ $noisenow == "yes" ] ; then
   if [ $noisethen == "yes" ] ; then
     mode="stillnoise"
     chunklen="2"

   else
     mode="newnoise"	# NEW NOISE STARTED
     starttime=$currenttime
     chunklen="3"
   
 #  RIG STUFF HERE TO PERFORM ACTIONS ON BEGINNING OF NOISE EVENT
   fi


 else
   if [ $noisethen == "yes" ] ; then

     mode="endnoise"   # END OF NOISE
     chunklen="2"
     endtime=$currenttime
     length=$(( $currenttime - $starttime ))

     logstring=$(echo 'Noise Detected:' $(date +%c -d @$starttime). 'Length:' $length 'Seconds.')
     echo $logstring

 #  RIG STUFF HERE TO PERFORM ACTIONS ON END OF NOISE EVENT
    
   else

     mode="stillsilence" # zz
     chunklen=3
   fi
 fi
 clear
 echo $mode


 sleep 0.0
done


```

This is part of the noise detector code I use for my website Pollywatch ([http://tinyurl.com/pollywatch](http://tinyurl.com/pollywatch)). I also use an open source tool called Motion to do motion-detection with webcam. Together they make a nifty baby monitor setup.

---

