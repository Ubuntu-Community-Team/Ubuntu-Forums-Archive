---
title: "Bash scripting help"
date: 2012-05-18
forum: General Help
---

### Post by Tclarkie on 2012-05-18
Hi all
I am trying to write a simple script to make it easy download the Triple J feature album, incorporating rtmpdump and pacpl.
 ```
#!/bin/bash
echo "Directory: "
read directory
cd $directory 
echo "xml:"
read xml 
grep "rtmp" $xml | tr "[ ]" "[\n]" | grep "rtmp" | sed "s/url=//g" >> .rtmp

for line in `cat .rtmp`; do
echo $line | tr -d '"'
echo "name of track: "
read  "name"
rtmpdump -r "$line" -o "$name.flv"
pacpl ."$name".flv -t mp3
rm ."$name".flv
play -q /usr/share/chirp.wav 
done
rm .rtmp
```
RTMPDUMP always returns "RTMPDump v2.4
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
WARNING: Unknown protocol!" but when i substitute the variable $line with the string it contains, it works
what is the problem here?
Thanks

---

### Post by Vaphell on 2012-05-18
what are the values $line gets from that cat .rtmp? print them out with no modification. Are they with ", because i see you echo $line with stripped "?
if so, you should either modify sed
```
sed -r 's/url=["](.*)["]/\1/'
```
or
```
"${line//\"/}"
```

---

### Post by Tclarkie on 2012-05-18
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/01.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/02.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/03.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/04.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/05.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/06.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/07.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/08.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/09.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/10.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/11.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/12.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/01.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/02.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/03.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/04.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/05.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/06.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/07.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/08.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/09.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/10.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/11.mp3"
"rtmp://cp44823.edgefcs.net/ondemand/flash/triplej/streams/audio/albums/thetempertrap/12.mp3"

---

### Post by Vaphell on 2012-05-18
yup, quotes are in the value and "rtmp:// is not exactly a valid protocol name, look my previous post i edited it with more detail

---

### Post by Tclarkie on 2012-05-18
I did as you suggested, still returns WARNING: Unknown protocol!

---

### Post by Vaphell on 2012-05-18
how does your script look like now?
some snippet from the input data would be nice so it's easy to track the flow of the script

---

### Post by Tclarkie on 2012-05-18
```
#!/bin/bash
echo "Directory: "
read directory
cd $directory 
echo "xml:"
read xml 
grep "rtmp" $xml | tr "[ ]" "[\n]" | grep "rtmp" | sed -r 's/url=["](.*)["]/\1/' >> .rtmp
for line in `cat .rtmp`; do
url=$line
echo "name of track: "
read  "name"
rtmpdump -r "$url" -o "$name.flv"
pacpl ."$name".flv -t mp3
rm ."$name".flv
play -q /usr/share/chirp.wav 
done
rm .rtmp

```

all input
directory: t2 (a local folder)
xml: 1.xml (a saved verion of [http://www.abc.net.au/triplej/geo/thetempertrap/thetempertrap.xml](http://www.abc.net.au/triplej/geo/thetempertrap/thetempertrap.xml) ~/t2)
name of track: Song1

Output:
```
tully@tully-Satellite-A100:~$ sh triplej/usr/bin/triplej
Directory: 
t2
xml:
1.xml
name of track: 
Song1
RTMPDump v2.4
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
WARNING: Unknown protocol!

Connecting ...
WARNING: HandShake: client signature does not match!
INFO: Connected...
ERROR: Closing connection: NetStream.Play.Failed
Perl Audio Converter - 4.0.5

error: the following is not a file or directory: .Song1.flv

see 'pacpl --help' or 'pacpl --longhelp' for a list of options.
rm: cannot remove `.Song1.flv': No such file or directory

```

---

### Post by Vaphell on 2012-05-18
lol, due to copyright something something unavailable something something Australia only :-) could you paste a line or two from the xml file?

---

### Post by Tclarkie on 2012-05-18
Pfft.. Thats your fault for living in Poland :P i just attached the xml

---

### Post by Vaphell on 2012-05-18
you don't need to kick the man when he's down ;-)
no sun, no ocean from every side, no australian dollar... and on top of that sites refuse to serve content... that's just too much :P

---

### Post by Tclarkie on 2012-05-18
You're right, living 25 minutes from secluded, warm, beautiful beaches is pretty good :P

---

### Post by Vaphell on 2012-05-18
i don't think you really want my help... ;-)



```
#!/bin/bash

read -p "Directory: " directory
cd $directory 
select xml in *.{xml,txt}; do break; done

files=( $( grep "rtmp" "$xml" | tr "[ ]" "[\n]" | grep "rtmp" | sed -r 's/url="(.*)"/\1/' ) )

for file in "${files[@]}"
do
  echo $file
  read -p "name of track: " name
  rtmpdump -r "$file" -o ."$name.flv"
  pacpl ."$name".flv -t mp3
  rm ."$name".flv
  play -q /usr/share/chirp.wav 
done
```

removed temporary file, added array
replaced echo ... ;read ... with read -p ...
added automatic menu of matched files, tweak file pattern to suit your needs
should work but i can't be bothered to download these files :-)

---

