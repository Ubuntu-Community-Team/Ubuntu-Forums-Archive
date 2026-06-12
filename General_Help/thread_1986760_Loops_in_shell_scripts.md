---
title: "Loops in shell scripts"
date: 2012-05-25
forum: General Help
---

### Post by DrPL on 2012-05-25
Hi everyone,
Just a quick query, hopefully someone can provide a quick answer ;)

I have a lot of files that I need to process using a syntax like
./conv2.sh file_0.txt  file_conv_0.txt

The file numbering goes from 0 to about 50, and while I know the basic
syntax of shell scripts, I am confused as to how to run the preceding command "n" times, where "n" is part of the file name.

Many thanks

Paul

---

### Post by Jose Catre-Vandis on 2012-05-25
See if this helps

[http://www.thegeekstuff.com/2011/07/bash-for-loop-examples/](http://www.thegeekstuff.com/2011/07/bash-for-loop-examples/)

For multiple files I usually don't feed the scripts with parameters, i just lump them all into one directory together - e.g. (convert mp4 video to mp3 audio)

```
#!/bin/bash

#convert mp4 to mp3

FILES="*.mp4"

for F in $FILES

do
newname=`basename "$F" .mp4`
echo $newname
ffmpeg -i "$F" -vn -acodec libmp3lame -ac 2 -ab 192k -ar 44100 "$newname.mp3"

done
``` This takes myvideo.mp4 and creates myvideo.mp3. There are so many different ways to appraoch your requirement though....;)

---

### Post by matt_symes on 2012-05-25
Hi

Something along the lines of...

```
for i in {0..50}; do ./conv2.sh file_${i}.txt file_conv_${i}.txt; done
```

echoing the filename to test.

```
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 % for i in {1..10}; do echo ./conv2.sh file_${i}.txt file_conv_${i}.txt; done
./conv2.sh file_1.txt file_conv_1.txt
./conv2.sh file_2.txt file_conv_2.txt
./conv2.sh file_3.txt file_conv_3.txt
./conv2.sh file_4.txt file_conv_4.txt
./conv2.sh file_5.txt file_conv_5.txt
./conv2.sh file_6.txt file_conv_6.txt
./conv2.sh file_7.txt file_conv_7.txt
./conv2.sh file_8.txt file_conv_8.txt
./conv2.sh file_9.txt file_conv_9.txt
./conv2.sh file_10.txt file_conv_10.txt
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 %
```

Kind regards

---

### Post by DrPL on 2012-05-26
Thank you!

---

