---
title: "There was an error creating the child process for this terminal"
date: 2012-01-09
forum: General Help
---

### Post by DOS286 on 2012-01-09
I'm hoping for some bash help here. I keep getting: "There was an error creating the child process for this terminal."

Here's the background. I have a stack of DV tapes full of home video I am transferring. I want to convert them to mpeg for permanent storage on the hard drive. I wrote the following script:

```
#! /bin/bash

mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:480,harddup,yadif -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:vstrict=0:acodec=ac3:abitrate=192:aspect=4/3 -ofps 30000/1001 -o "${1%.*}.mpeg" "$1"

```I put this in /user/local/bin and can run it on a .dv file from a right click. However, I cannot see the progress or output and can only run it on one file at a time. So I wrote another script that calls the first:

```
#! /bin/bash

for var in "$@"
do
    gnome-terminal -e "dvd2dvdmpeg.sh '$var'"
done

```I thought this would allow me to see the process (by running it in a terminal window) and allow me to right click multiple .dv files and convert them all. However, it just gives me "There was an error creating the child process for this terminal"

Does anyone know how to fix this? Or perhaps a better way to get this done?

---

### Post by papibe on 2012-01-09
gnome-terminal goes into the background by default. My guess is that there are so much processes called in parallel that they eat all your RAM.

Try running them one at a time (just call directly your script inside the for stament).

Just a thought.
Regards.

---

### Post by DOS286 on 2012-01-09
Thanks for the response. Do you mean without calling gnome-terminal? Something like this?

```
#! /bin/bash

for var in "$@"
do
    dvd2dvdmpeg.sh '$var'
done
```

I can try that after work tonight, but I suspect that I will not be able to see the output of mencoder and cannot check the progress. Any idea how to get this to show the output?

Also, I have not tried it on multiple files yet, I have only tested it on one file so far and cannot get that to work.

Thanks.

---

