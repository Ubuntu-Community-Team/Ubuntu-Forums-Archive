---
title: "How to get mpg123 to play streamed playlist"
date: 2006-04-23
forum: General Help
---

### Post by hikitsu4 on 2006-04-23
Hello i was wondering how you get mpg123 to play shoutcast playlist or for example this playlist [http://server1.kawaii-radio.net:9000/listen.pls](http://server1.kawaii-radio.net:9000/listen.pls) 
If mpg123 doesnt work then i got mpg321 installed also.

---

### Post by TuxCrafter on 2006-07-21
I am searching also voor a cli (command line interface) tool that can play internet streams for for example [www.sky.fm](www.sky.fm).

CLI because i dont want it to use cpu load and useability

---

### Post by TuxCrafter on 2006-07-21
Some how it just came to me i had to test it and it works :-D


open a *.pls file it contains some stream adresses use them!

man mpg123 for info

```
mpg123 -C -v -b 1024 -k 64 http://64.236.34.196:80/stream/1002

```

---

### Post by TuxCrafter on 2006-07-21
I have made a script for playing *.pls files.

Please test it and post the feedback.

Make a file called play-internetradio.sh and paste the following text into it and make the script executable.

execute the file with the playlist file as argument.


```
#Company:	PowerCraft Technology
#Author: 	Copyright Jelle de Jong <jelledejong@powercraft.nl>
#Version:	0.0.1
#Date:		21-07-2006
#System:	Xubuntu 6.06
#Description:	Get the info out of a playlist file and try to play the stream
#Information:	man cut, man tail, man mpg123

# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by the
# Free Software Foundation; either version 2, or (at your option) any
# later version.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.

#!/bin/sh

echo $*
stream=`cat -A $* | head -n 3  | cut -f 2 -d '=' | tail -n 1 | cut -f 1 -d '^'`
echo $stream
echo "xterm -e mpg123 -C -v -b 2048 -k 256 "$stream""
xterm -e mpg123 -C -v -b 1024 -k 128 $stream
exit
```

---

### Post by Mandrake12 on 2008-02-21
Hi, your script seems to be just what I am looking for; however I have some problems getting it to work; I'm trying to load the following playlist:

```
[playlist]
NumberOfEntries=9
File1=http://icecast.commedia.org.uk:8000/resonance.mp3
File2=http://www.wfmu.org/wfmu.m3u                       
File3=http://www.wps1.org/players/wps1.pls
File4=http://media.hiof.no/streams/m3u/nrk-alltid-klassisk-128.m3u
File5=http://wwoz-sc.streamguys.com/listen.pls
File6=http://media.hiof.no/streams/m3u/nrk-alltid-nyheter-56.m3u
File7=http://anka.org:8080/fresh.ogg.m3u
File8=http://www.di.fm/mp3/minimal.pls
File9=http://www.di.fm/mp3/electro.pls
```

and I get the following error:

```
mandingo@mandingo:~/Desktop$ sh radio.sh radio.pls 
radio.sh: 7: stream: not found
radio.sh: 11: it: not found
radio.pls
radio.sh: 25: -d: not found
http://icecast.commedia.org.uk:8000/resonance.mp3$
xterm -e mpg123 -C -v -b 2048 -k 256 http://icecast.commedia.org.uk:8000/resonance.mp3$
```

any idea what is causing this error?

---

### Post by TuxCrafter on 2008-02-21
new version can be found in a later post

---

### Post by Mandrake12 on 2008-02-22
for some reason I still get an error trying to load the playlist posted above:

```
mandingo@mandingo:~/Desktop$ sh play-internetradio.sh radio.pls 
processing file(s):
-ne \E[34m
radio.pls 
-ne \E[32m
starting with:  
radio.pls
-ne \E[34m
command: aoss mpg123 -C -b 512 -k 128 http://www.di.fm/mp3/electro.pls 
-ne \E[32m
trying to start the stream, please standby... 
decoder: i586/pentium
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
        version 0.66; written and copyright by Michael Hipp and others
        free software (LGPL/GPL) without any warranty but with best wishes
Error: unknown mpeg MIME type audio/x-scpls - is it perhaps a playlist (use -@)?
Error: If you know the stream is mpeg1/2 audio, then please report this as mpg123 bug
-ne \E[32m
```

any idea what I'm doing wrong here?

---

### Post by TuxCrafter on 2008-02-22
fixed the script here it is see the attachment. i tested it with your file and it works.

chmod +x play-internetradio.sh

---

