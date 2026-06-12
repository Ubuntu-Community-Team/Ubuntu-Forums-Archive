---
title: "Copy only most recent files from a directory"
date: 2011-03-04
forum: General Help
---

### Post by Knightwise on 2011-03-04
Hey Guyz

I am using Gpodder for the moment and would like to copy the 3 most recent podcast episodes of every podcast to a second directory (in fact the second directory resides on  my android phone, mounted via usb)

The setup is as follows

Gpodder downloads the episodes in 

/home/PODCASTS/podcast 1/
/home/PODCASTS/podcast 2/
/home/PODCASTS/podcast 3/
and so forth ...

My Android phone is mounted in 
/media/ANDROID/

What command should I use for copying over the 3 latest episodes of every podcast to my android phone ? 

I know that ls -rt lists them up chronologically
and when i do      ls-rt | tail -3   i get a list of the 3 recent podcasts of THAT specific directory
but what command do i use to "ls" into the directory (recursively) and get the 3 latest files of every directory AND copy those over to /media/ANDROID ?

thanx :)

---

### Post by Knightwise on 2011-03-04
Gpodder is a podcatcher , it downloads the episodes of every podcast from the web :

[http://gpodder.org/](http://gpodder.org/)

---

### Post by aeiah on 2011-03-04
just to be clear, are you wanting a script/command that:

[LIST]
[*]copies the 3 most recent, no matter what podcast folder they are from (a total of 3 get copied onto your android phone)
[/LIST]

or

[LIST]
[*]copies the 3 most recent from each podcast folder (so a total of 9 in your example)
[/LIST]

---

### Post by Knightwise on 2011-03-04
Hey :) 

The three most recent ones from every podcast
(so 9 in total)

---

### Post by aeiah on 2011-03-04
> **Knightwise said:**
> when i do      ls-rt | tail -3   i get a list of the 3 recent podcasts of THAT specific directory


well, one way you could do it is to use this command in a for loop. so roughly speaking: "for each of my podcast directories, move the files that result from ls -rt | tail -3 over to android"

```

PODCASTS = /home/PODCASTS/*

for path in $PODCASTS
do
    mv `ls $path -rt | tail -3` /media/ANDROID/
done

```

now, your podcast and android paths will probably want changing (are you sure your podcasts arent in /home/username/podcasts/ or something?)

i havent tested this so lemme know if ive wrote a pile of ****

---

### Post by Knightwise on 2011-03-04
Can i run a PHP script like a standard batch script (i'm very novice in scripting)
yep , i've put the podcasts file in /home/PODCASTS (not in my personal home dir) because i also share out that folder via samba for streaming everything.

---

### Post by aeiah on 2011-03-04
i usually write python scripts but im trying to get myself into the habit of writing bash scripts for very simple tasks as it feels a bit more native.

i think you may need to install php, or just php-cli but after that you should be able to treat them the same. if not, you might have to launch them as ```

php scriptname.php
```

---

### Post by Knightwise on 2011-03-04
Awesome :) 

I'm trying it now

First i installed php : 
sudo apt-get install php5-cli 

then added the following line to your header
#!/usr/bin/php
made the script exexutable 
It looks like this.


#!/usr/bin/php
PODCASTS = /home/cardinalzero/testfolder1/*

for path in $PODCASTS
do
    cp -av `ls $path -rt | tail -1` /home/cardinalzero/testfolder2
done

(as an example)


but it doesnt copy anything over ?

---

### Post by aeiah on 2011-03-04
well what i gave you was bash, not php. i dont know any php

at the top of a bash script you'd put ```
#!/bin/bash
```

ill test what i put and see if it works or not

---

### Post by Knightwise on 2011-03-04
Allmost there

I've adapted the script (thanx to some help from the guyz at ubuntu-uk)
It works ,

!/bin/bash
PODCASTS=/home/SHARED/PODCASTS/*
for path in $PODCASTS
do
cp -av $path/`ls $path -rt | tail -1` /media/Y/Music/Podcasts/
done


HOWEVER 

the subdirectories in the PODCASTS folder have SPACES in their names :( .. and that completely fracks it up :§

---

### Post by aeiah on 2011-03-04
i dont know why i suggested mv instead of cp, you obviously wanted to copy them. not that my script would have worked anyway.

incidentally, your revised script only copies the newest from each, not the newest 3.

---

### Post by Knightwise on 2011-03-04
I'm allmost there

the only error is the script now copies over EVERY episode instead of just the last one


#!/bin/bash
PODCASTS=/home/SHARED/PODCASTS/*
for path in $PODCASTS
do
cp -av "$path/`ls -rt $path | tail -1`" /media/Y/Music/Podcasts/
#cp -av $path/`ls $path -rt | tail -1` /media/Y/Music/Podcasts/
done

---

### Post by aeiah on 2011-03-04
adding ```

IFS=$'\t\n'

```
to the top of your script (well, under the #!/bin/bash declaration) will enable you to have spaces in the filenames without resorting to quotes in your command. normally the variable IFS is set to ' \t\n' (thats a space). meaning normally spaces act like separators (\t is tab, \n is newline)

this means you can do away with the quotes and get the same functionality you had before (ie, the newest file from each directory)
```

#!/bin/bash
IFS=$'\t\n'
PODCASTS=/home/SHARED/PODCASTS/*

for path in $PODCASTS
do
    cp -av $path/`ls $path -rt | tail -1` /media/Y/Music/Podcasts/
done
```

like i said, im crap with bash, so im learning a bit too :p i still dont know how to get the newest 3 though, since tail -3 doesnt work in this situation

---

### Post by Knightwise on 2011-03-04
BRILLIANT ! that did the trick. ! ! ! 

Now its copying over just the last file.

i've made some additions to the code (thanx to @marijnvds on #ubuntu-uk) and now it looks like this 

#!/bin/bash
IFS=$'\t\n'
PODCASTS=/home/SHARED/PODCASTS/*
DESTINATION=/media/Y/Music/Podcasts/

for path in $PODCASTS
do
    SOURCE_PATH=`ls -rt $path | tail -1`
    echo "Source path: $SOURCE_PATH"
    cp -av "$path/$SOURCE_PATH" $DESTINATION
done


SOLVED !!!! Thanx everyone :) !!!!!:KS:KS:KS:KS:KS:KS

---

### Post by aeiah on 2011-03-04
ive got it copying over the newest 3 if you want. i think that last revision just neatens it up, doesnt it? (ie it still just copies the newest one)


below should copy the newest 3 from each directory. i used another for loop inside the first one, so it does: "for each directory in the source, get a list of the 3 newest files. for each of the 3 newest files, copy over to the destination"
```

#!/bin/bash
IFS=$'\t\n'
PODCASTS=/home/SHARED/PODCASTS/*
DESTINATION=/media/Y/Music/Podcasts/
for path in $PODCASTS
do
        threeNewest=`ls $path -rt | tail -3`
        for file in $threeNewest
        do
                cp -av $path/$file $DESTINATION
        done
done

```

---

### Post by Knightwise on 2011-03-04
Yep , its the general idea (i can set the tail to -3 when i want to) but to save space i'll take the last episode :) 

Its a very tidy script , 
you could set cp -avm to prevent cp to copy episodes you already have

---

### Post by Knightwise on 2011-04-30
Hello guyz.

I'm still "working on the script" where in its "next incarnation" it is serving to select my latest podcast and copy them over to my dropbox directory using RSYNC. I want to use RSYNC to make sure the 'not so fresh' episodes get deleted and the "fresh" episodes get copied over. Then dropbox can sync the "new" files over to the cloud where i can access them via my ipad/iphone (whole other story).

The thing is : i've replaced the cp command with the RSYNC command and now the script is acting strangely.

It selects and sync's over the "newest" podcasts to the destination directory. Then it suddenly DELETES all the episodes in the destination directory and copies over the three last files. Its really strange.

I'll give you a turnout of the script AND the output.

THE SCRIPT

#!/bin/bash
#gpo update
#gpo download
IFS=$'\t\n'
PODCASTS=/home/SHARED/PODCASTS/*
DESTINATION=/home/SHARED/COMMON/FRESHPODCASTS
for path in $PODCASTS
do
    SOURCE_PATH=`ls -rt $path | tail -1`
    echo "Source path: $SOURCE_PATH"
    rsync -avt --del "$path/$SOURCE_PATH" $DESTINATION
done




The OUTPUT

Source path: folder.jpg
sending incremental file list
folder.jpg

sent 38977 bytes  received 31 bytes  78016.00 bytes/sec
total size is 38866  speedup is 1.00
Source path: Tritonal_-_Air_Up_There_037.mp3
sending incremental file list
Tritonal_-_Air_Up_There_037.mp3

sent 172885132 bytes  received 31 bytes  18198438.21 bytes/sec
total size is 172863903  speedup is 1.00
Source path: episode170.m4a
sending incremental file list
episode170.m4a

sent 41355342 bytes  received 31 bytes  27570248.67 bytes/sec
total size is 41350186  speedup is 1.00
Source path: agp_2011_04_11_044.mp3
sending incremental file list
agp_2011_04_11_044.mp3

sent 57604780 bytes  received 31 bytes  12801069.11 bytes/sec
total size is 57597632  speedup is 1.00
Source path: folder.jpg
sending incremental file list
folder.jpg

sent 22534 bytes  received 31 bytes  45130.00 bytes/sec
total size is 22427  speedup is 0.99
Source path: Club_Sunset_Episode_061.mp3
sending incremental file list
Club_Sunset_Episode_061.mp3

sent 286720469 bytes  received 31 bytes  19773827.59 bytes/sec
total size is 286685352  speedup is 1.00
Source path: folder.jpg
sending incremental file list
folder.jpg

sent 147181 bytes  received 31 bytes  98141.33 bytes/sec
total size is 147058  speedup is 1.00
Source path: 290_EP290_TomtheUniverse.mp3
sending incremental file list
290_EP290_TomtheUniverse.mp3

sent 49579446 bytes  received 31 bytes  33052984.67 bytes/sec
total size is 49573272  speedup is 1.00
Source path: geekbeattv--0174--20110427--small.h264.mp4
sending incremental file list
geekbeattv--0174--20110427--small.h264.mp4

( and so forth) 
Then SUDDENLY 
sent 33378217 bytes  received 31 bytes  13351299.20 bytes/sec
total size is 33374019  speedup is 1.00
Source path: 
sending incremental file list
./
deleting uupc_s04e05_high.mp3
deleting thechillcast-278695-04-28-2011.mp3
deleting tekzilla--0212--psndown--small.h264.mp4
deleting pe28-med.m4v
deleting lifehacker--0006--repurposed--large.h264.mp4
deleting kc0052.mp3
deleting hpr0715.mp3
deleting hak5--0910--twosteprickrolldoom--large.h264.mp4
deleting glp136.mp3
deleting geekbeattv--0174--20110427--small.h264.mp4
deleting garethemerypodcast_130.m4a
deleting friskyPodcast0154_-_Shamanah_live_at_getFrisky_Miami.mp3
deleting folder.jpg
deleting episode170.m4a
deleting agp_2011_04_11_044.mp3
deleting Tritonal_-_Air_Up_There_037.mp3
deleting TheTechieGeek_082.mp3
deleting Reverse_Speech_with_David_John_Oates.mp3
deleting PC154_SinnersSaints.mp3
deleting NC_2011_04_24.mp3
deleting MikeMatas_2011.mp3
deleting MPU048.mp3
deleting LinuxActionShowEP156-MP3.mp3
deleting Club_Sunset_Episode_061.mp3
deleting 290_EP290_TomtheUniverse.mp3

sent 58 bytes  received 15 bytes  146.00 bytes/sec
total size is 0  speedup is 0.00
Source path: folder.jpg
sending incremental file list
folder.jpg

sent 110502 bytes  received 31 bytes  221066.00 bytes/sec
total size is 110383  speedup is 1.00
Source path: TheTechieGeek_082.mp3
sending incremental file list
TheTechieGeek_082.mp3

sent 16670764 bytes  received 31 bytes  11113863.33 bytes/sec
total size is 16668613  speedup is 1.00
Source path: folder.jpg
sending incremental file list
folder.jpg

sent 201457 bytes  received 31 bytes  402976.00 bytes/sec
total size is 201326  speedup is 1.00
Source path: folder.jpg
sending incremental file list
folder.jpg

sent 21386 bytes  received 31 bytes  42834.00 bytes/sec
total size is 21279  speedup is 0.99
Source path: uupc_s04e05_high.mp3
sending incremental file list
uupc_s04e05_high.mp3

sent 58678125 bytes  received 31 bytes  23471262.40 bytes/sec
total size is 58670847  speedup is 1.00


*** Now i'm left with a folder that ONLY contains those last 3 files. *** WHY ? ? ?

---

