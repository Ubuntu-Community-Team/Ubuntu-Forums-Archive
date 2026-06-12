---
title: "help with my script"
date: 2010-02-07
forum: General Help
---

### Post by sn0m on 2010-02-07
dear experts
I'm trying to extract audio and then convert to mp4 format a bunch of flv files downloaded from internet. There are three files
I intend to use ffmpeg in the following options:
ffmpeg -i input.flv -acodec copy output.mp3
and
ffmpeg -i "input.flv" -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2 "output.mp4"
So I started writing a script like this:

#!/bin/bash -x
cd /home/koli/exp
for i in *.flv do ; /usr/bin/ffmpeg -i $i -acodec copy $i.mp3 ;done
before i added the mp4 convert option.
However when i tried to run it, it gives me: syntax error near unexpected token `/usr/bin/ffmpeg'

so i would appreciate if any of you gentle souls out there could help me out with it.
Thanks
Sokol

---

### Post by cjhabs on 2010-02-07
The "do" comes after the ;

---

### Post by chewearn on 2010-02-07
You have the first semi-colon at the wrong location.
To prevent error from filename with special characters (e.g. spaces), it is advisable to enclose with double quotes.

```

for i in *.flv ; do /usr/bin/ffmpeg -i "$i" -acodec copy "$i.mp3" ; done
```

---

### Post by kaibob on 2010-02-07
I don't know anything about ffmpeg, but the error message is because you have the semi-colon wrong:

```
for i in *.flv ; do /usr/bin/ffmpeg -i $i -acodec copy $i.mp3 ;done
```

---

### Post by sn0m on 2010-02-07
Thanks fellas, you are my heroes.
It works like a charm.
Greetings
Sokol

---

### Post by jamesisin on 2010-02-07
For what it's worth, you shouldn't need the /usr/bin/ either  That location ought to already be in your path:

```
echo $PATH
```

This should show a list of your path locations and /usr/bin/ should be among them.

---

