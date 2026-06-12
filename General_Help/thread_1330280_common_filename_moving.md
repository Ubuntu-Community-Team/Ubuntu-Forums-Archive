---
title: "common filename moving"
date: 2009-11-18
forum: General Help
---

### Post by wasutton3 on 2009-11-18
i torrent some free podcasts, and when i download them to my headless server, i leave them to seed (using transmission) until i reach a 1:1 ratio. I would like to set up a script to automatically move these to a folder once they finish seeding. they are all formatted as title.yyyy.mm.dd.guest.mp3 where title is the name of the show, and guest is the guest. is this possible? and if so, how would i go about doing so and where would i start?

---

### Post by Giblet5 on 2009-11-18
Is there a way, from the command line, to query the stats on a given file to determine that you've hit the 1:1 seed ratio?

Post the command line used and the output and I'll post a script to automate it.

---

### Post by wasutton3 on 2009-11-18
transmission-remote localhost:8080 --auth=username:password -l | grep The.Podcast.Name

Is the command, and it outputs a long list of the torrents that start with the podcast name in a table format of the following
```
ID DONE HAVE ETA UP DOWN RATIO STATUS NAME
```

I dont know how exactly i can get this to work properly.

---

### Post by Giblet5 on 2009-11-18
That's not actual output, though it does tell me what fields are what...

Put the command in a code block using "bob" and "1234" for username and password. Then put actual output (no grep) in a code block.

I have to know exactly what to expect in the output if I'm going to automate it.

If the data is too sensitive, take a look at the man pages for sed and awk and you'll get some good ideas about how to do this yourself.

---

### Post by wasutton3 on 2009-11-18
Thats the output. 

```
ID     Done       Have  ETA           Up    Down  Ratio  Status       Name
   1   100%   854.3 MB  Done         0.0     0.0   1.00  Stopped      BackTrack 4 Beta
 

```

---

### Post by sisco311 on 2009-11-18
I don't know how to do this in transmission, but in deluge there are options to move finished torrents to a new location and stop seeding them when the share ratio reaches 1:1.

---

### Post by wasutton3 on 2009-11-18
i know there is (on deluge), but i need the web interface (its the only one that works well remotely as well as on a mobile browser), i found a script that would do it to transmission but i need to find out how to do that to specific torrents. there isnt a function like that in transmission that i am aware of

---

### Post by Giblet5 on 2009-11-18
Well, this will move the avi files. The ones with the unlikely names will be tougher.

```
#!/bin/bash

TARGET_DIR="/home/avi-purgatory"

transmission_commandline | sed -e '1d' | awk '{ if( $8 >= 1.00 ) print $10 }' | grep -e '.avi$' > /tmp/files-$$.dat

for i in `cat /tmp/files-$$.dat`
do
   mv $i $TARGET_DIR
done

rm -f /tmp/files-$$.dat

exit 0
```


Like I said, the other file names don't appear to be filenames.

Also, it is extremely dangerous to use [ and ] in a filename as those are special characters to the shell...

Also, it looks like you are sharing copyrighted material. DON'T DO THAT.

---

### Post by fluffman86 on 2009-11-18
Hahahaha, Christian Music, Ozzy, and Watchmen *director's cut*.  What an ecclectic mix. :D  :LOL:

---

### Post by wasutton3 on 2009-11-18
Yea i know its eclectic. I own all that material, i just dont like swapping disks and stuff around (scratched one too many expensive disks that way)

---

### Post by Giblet5 on 2009-11-18
Well, save that script, make it executable, and run it periodically. It'll move the AVI files. I'd fix those filenames though. That's going to cause trouble. Guaranteed.

---

