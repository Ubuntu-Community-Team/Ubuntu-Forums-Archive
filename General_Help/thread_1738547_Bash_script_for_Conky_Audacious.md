---
title: "Bash script for Conky Audacious"
date: 2011-04-24
forum: General Help
---

### Post by Icche Ghuri on 2011-04-24
I've made a very simple bash script for both conky and audacious lovers like me. It will first check if audacious is running or not. If running then it'll show some informations on the basis of its playback status, ie stopped, paused or playing. Here is the code

```
#!/bin/bash

#variable declarations
check=`audtool --current-song`

playback_status=`audtool --playback-status`

aud="Audacious is now"
status=`audtool --playback-status`
title=`audtool --current-song`
artist=`audtool --current-song-tuple-data artist`
album=`audtool --current-song-tuple-data album`
year=`audtool --current-song-tuple-data year`
track_no=`audtool --current-song-tuple-data track-number`
track_length=`audtool --current-song-length`

#conditional statments starts
if [ "${check}" == "No song playing." ]; #Check if audacious is running
then
    echo "Audacious is not running"
    
elif [ "${playback_status}" == "paused" -o "${playback_status}" == "stopped" ]; #Check for 'paused' and 'stopped' state
then
    echo ${aud}  ${status}
    
    
else #..:Music informations:..#
    echo ${aud}  ${status} 
    echo  "Title:" ${title}
    echo  "Artist:" ${artist}
    echo  "Album:" ${album}
    echo  "Year:" ${year}
    echo  "Track No:" ${track_no}
    echo  "Track Length:" ${track_length}
fi
```


**_How to use:_**
[list][*]Create a text file, put this code into that and save it. (I saved it as conky_audacious into my home folder)
[*]Open a terminal and make it executable by the command
```
chmod a+x conky_audacious
```or, right click> Properties> Permissions> Execute and check "Allow executing file as program"

[*]Add this line to your .conkyrc file
```
${execi 2 ~/conky_audacious}
```
[*]Restart conky

It'll produce informations like this screenshot
[IMG]https://lh5.googleusercontent.com/_ALyUuIk8s88/TbTaGlpOmiI/AAAAAAAAAJ4/cz2_LhNF8P8/s800/conkyaudacious.png[/IMG]

You can add more informations associated with the "audtool" command. Type
```
audtool --help
```
in a terminal and findout more information fields. Then add/change variables and echos in the bash script.
[/LIST]

---

### Post by fdrake on 2011-04-24
that's cool i will try it! good job!

---

### Post by fdrake on 2011-04-24
that's cool i will try it! good job!

---

### Post by elliotn on 2011-07-20
anyone has a way to display album art with conky?

---

### Post by Jony35359595 on 2011-07-20
> **elliotn said:**
> anyone has a way to display album art with conky?
I'm using Rhythmbox and installed conkyRhythmbox form conky companions repo, all working grat with it!\
> ${execi 8 cp "`conkyRhythmbox --datatype=CA | sed -e 's/\\\//g'`" ~/.album.pic}${image ~/.album.pic -p 0,455 -s 86x86 -f 3}
[IMG]http://s2.share.te.ua/b333779/conkyrhythmbox.jpg[/IMG]
you can easily change size and position of album art...

---

### Post by elliotn on 2011-07-20
> **Jony35359595 said:**
> I'm using Rhythmbox and installed conkyRhythmbox form conky companions repo, all working grat with it!\

[IMG]http://s2.share.te.ua/b333779/conkyrhythmbox.jpg[/IMG]
you can easily change size and position of album art...

wow that's cool but I wonder if I can do the same in audacious.

---

### Post by VastOne on 2011-10-05
> **elliotn said:**
> wow that's cool but I wonder if I can do the same in audacious.

I explain how to do it with Audacious in a [_[COLOR="Green"]How To here on #![/COLOR]_]("http://crunchbanglinux.org/forums/topic/15356/how-to-conky-music-and-cover-art-2-methods-for-16-apps/")

---

### Post by midas546 on 2011-12-05
THANKS SOO MUCH :guitar:

---

