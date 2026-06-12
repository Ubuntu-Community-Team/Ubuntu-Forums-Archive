---
title: "Rsync Deletes files it should not delete. (podcathing script)"
date: 2011-05-04
forum: General Help
---

### Post by Knightwise on 2011-05-04
Hello guyz.

I built a script that downloads my podcasts using Gpodder into the directory

/HOME/SHARED/PODCASTS/ (with a subdirectory for each podcast)

The script then selects the latest episode and copies it over to a target directory (it empies the target directory first and copies over everything) 

I want to use RSYNC to make sure the 'not so fresh' episodes get deleted and the "fresh" episodes get copied over. Then dropbox can sync the "new" files over to the cloud where i can access them via my ipad/iphone (whole other story).

The thing is : i've replaced the cp command with the RSYNC command and now the script is acting strangely.

It selects and sync's over the "newest" podcasts to the destination directory. Then it suddenly DELETES all the episodes in the destination directory and copies over the three last files. Its really strange.

I'll give you a turnout of the script AND the output.

THE SCRIPT

#!/bin/bash
gpo update
gpo download
IFS=$'\t\n'
PODCASTS=/home/SHARED/PODCASTS/*
DESTINATION=/home/SHARED/DROPBOX/
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

sent 38977 bytes received 31 bytes 78016.00 bytes/sec
total size is 38866 speedup is 1.00
Source path: Tritonal_-_Air_Up_There_037.mp3
sending incremental file list
Tritonal_-_Air_Up_There_037.mp3

sent 172885132 bytes received 31 bytes 18198438.21 bytes/sec
total size is 172863903 speedup is 1.00
Source path: episode170.m4a
sending incremental file list
episode170.m4a

sent 41355342 bytes received 31 bytes 27570248.67 bytes/sec
total size is 41350186 speedup is 1.00
Source path: agp_2011_04_11_044.mp3
sending incremental file list
agp_2011_04_11_044.mp3

sent 57604780 bytes received 31 bytes 12801069.11 bytes/sec
total size is 57597632 speedup is 1.00
Source path: folder.jpg
sending incremental file list
folder.jpg

sent 22534 bytes received 31 bytes 45130.00 bytes/sec
total size is 22427 speedup is 0.99
Source path: Club_Sunset_Episode_061.mp3
sending incremental file list
Club_Sunset_Episode_061.mp3

sent 286720469 bytes received 31 bytes 19773827.59 bytes/sec
total size is 286685352 speedup is 1.00
Source path: folder.jpg
sending incremental file list
folder.jpg

sent 147181 bytes received 31 bytes 98141.33 bytes/sec
total size is 147058 speedup is 1.00
Source path: 290_EP290_TomtheUniverse.mp3
sending incremental file list
290_EP290_TomtheUniverse.mp3

sent 49579446 bytes received 31 bytes 33052984.67 bytes/sec
total size is 49573272 speedup is 1.00
Source path: geekbeattv--0174--20110427--small.h264.mp4
sending incremental file list
geekbeattv--0174--20110427--small.h264.mp4

( and so forth) 
Then SUDDENLY 
sent 33378217 bytes received 31 bytes 13351299.20 bytes/sec
total size is 33374019 speedup is 1.00
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

sent 58 bytes received 15 bytes 146.00 bytes/sec
total size is 0 speedup is 0.00
Source path: folder.jpg
sending incremental file list
folder.jpg

sent 110502 bytes received 31 bytes 221066.00 bytes/sec
total size is 110383 speedup is 1.00
Source path: TheTechieGeek_082.mp3
sending incremental file list
TheTechieGeek_082.mp3

sent 16670764 bytes received 31 bytes 11113863.33 bytes/sec
total size is 16668613 speedup is 1.00
Source path: folder.jpg
sending incremental file list
folder.jpg

sent 201457 bytes received 31 bytes 402976.00 bytes/sec
total size is 201326 speedup is 1.00
Source path: folder.jpg
sending incremental file list
folder.jpg

sent 21386 bytes received 31 bytes 42834.00 bytes/sec
total size is 21279 speedup is 0.99
Source path: uupc_s04e05_high.mp3
sending incremental file list
uupc_s04e05_high.mp3

sent 58678125 bytes received 31 bytes 23471262.40 bytes/sec
total size is 58670847 speedup is 1.00


*** Now i'm left with a folder that ONLY contains those last 3 files. *** WHY ? ? ?

---

### Post by DaithiF on 2011-05-04
Hi,
I suspect one of your podcast directories is empty.

In that case your $SOURCE_PATH variable is empty and your rsync command ends up like:
```
rsync -avt --del "/path/to/empty/dir/" /path/to/destination

```
ie. you are syncing an empty directory to the destination, and since you specify the --del flag rsync will oblige by deleting all files from destination.

to fix this, check that source_path actually contains something before rsync'ing e.g. add a line like this to skip when source_path is empty:

```
# check if source_path is a file, otherwise skip this directory
[[ -n $source_path ]] || continue
```

---

### Post by Knightwise on 2011-05-04
Awesome !

You are indeed correct , one of the directories was empty, the other ones all contained at least a "folder.jpg" file with the album art ( + some podcasts) 

Could you tell me where in the script i would have to "slide in" this line ?

---

### Post by DaithiF on 2011-05-04
> **Knightwise said:**
> Could you tell me where in the script i would have to "slide in" this line ?
Immediately after the line where you set source path.

by the way, you mix upper and lower case names for variables, better to just use lower case consistently, to avoid the risk of overwriting environment variables.  thats why i was using source_path rather than your SOURCE_PATH ... but whichever you use, use the same in the line you add to test its value :)

---

### Post by Knightwise on 2011-05-04
Waaw :) 

i'll plunk the line into my script when I get home tonight and start testing it out. When the script is complete i'll post it back to the thread.

Once it is complete i'll use the SYNC feature in GOODREADER (an app on my ipad - ipod ) to sync the new files from the dropbox folder thus being able to have "fresh podcasts" without using a cable using Ubuntu, A script, Dropbox and an IOS app :)

What a ride ;)

---

### Post by Knightwise on 2011-05-04
YES ! It works :)

For those wanting to use my script here it is

#!/bin/bash
IFS=$'\t\n'
PODCASTS=/home/SHARED/PODCASTS/*
DESTINATION=/home/SHARED/DOWNLOADS/FRESHPODCASTS
for path in $PODCASTS
do
    SOURCE_PATH=`ls -rt $path | tail -1` 
    [[ -n $SOURCE_PATH ]] || continue
    echo "Source path: $SOURCE_PATH"
    rsync -avt --del "$path/$SOURCE_PATH" $DESTINATION
done


I'm now going to perfectionise the script by adding 2 kinds of destinations.

#the music directory on my android.
ANDROID = /media/DESIRE/Music 

making the script look like this

#!/bin/bash
IFS=$'\t\n'
PODCASTS=/home/SHARED/PODCASTS/*
IPAD=/home/SHARED/DOWNLOADS/FRESHPODCASTS
ANDROID=/media/DESIRE/Music
for path in $PODCASTS
do
    SOURCE_PATH=`ls -rt $path | tail -1` 
    [[ -n $SOURCE_PATH ]] || continue
    echo "Source path: $SOURCE_PATH"
    rsync -avt --del "$path/$SOURCE_PATH" $IPAD
    rsync -avt --del "$path/$SOURCE_PATH" $ANDROID
done

---

### Post by tsger on 2011-06-13
Hey, Knightwise, This is fantastic!  I was having the same delete problems, glad to find the solution here!  Thank you for posting your finds!

I have been following your podcasting setup tips from your recent shows and docucasts.

Couple of additional things I am trying...note, I am not a bash scripting guru, so there are probably simpler and cleaner ways to do what I have attempted. I do a lot of googling, forum searching, and copying/pasting!

1.  I need to convert the ogg formatted podcasts into mp3, because my ipod touch doesn't play ogg natively (requires the program [FONT="Courier New"]**soundconverter**[/FONT]).  
I wrote the following and called it [FONT="Courier New"]**oggconvert.sh**[/FONT]:

```
#!/bin/bash
LOCATION=~/Music/gpodder-downloads/
find $LOCATION -name '*.ogg' -exec soundconverter -b -m audio/mpeg -s .mp3 '{}' \; \
-exec rm '{}' \;
```

2.  I'd like the files to have friendly names, so I rename them with the following (requires the program [FONT="Courier New"]**eyeD3**[/FONT]):

```
for path in $PODCASTS
do
SOURCE_PATH=`ls -rt $path | tail -1`
[[ -n $SOURCE_PATH ]] || continue
echo "Source path: $SOURCE_PATH"
eyeD3 --rename=%a-%A-%n-%t "$path/$SOURCE_PATH"
done
```

I inserted that in the final script (see below), and it works pretty well, but there are some files which don't get renamed, I'm still researching that one.  Also, some of the file names end up being pretty long.

3.  Lastly, I want to get an email when the podcasts have been downloaded and synchronized, so I installed the program [FONT="Courier New"]**sendemail**[/FONT], and wrote the following script, calling it [FONT="Courier New"]**email.sh**[/FONT]:

```
#!/bin/bash
# -f = from address
# -t = to address
# -u = email subject
# -m = email body text
# -s = email sending server
# -o = this is needed for servers that require tls
# -xu = user name
# -xp = password
sendemail \
  -f [email]myname@someaddress.com[/email] \
  -t [email]recipientname@someaddress.com[/email]  \
  -u "Podcasts Were Updated" \
  -m "Do a sync now" \
  -s smtp.mymailhost.com \
  -o tls=yes \
  -xu myusername \
  -xp mypassword
```
  
All that does is notify me when it has finished.  I'd like to be able to figure out a way to have the email tell me which episodes were just downloaded...any ideas?

So here's my final script:

```
#!/bin/bash
gpo update
gpo download
IFS=$'\t\n'
CONVERSIONSCRIPT=~/scripts/oggconvert.sh
$CONVERSIONSCRIPT
PODCASTS=~/Music/gpodder-downloads/*
DESTINATION=~/Music/Podcasts/
for path in $PODCASTS
do
SOURCE_PATH=`ls -rt $path | tail -1`
[[ -n $SOURCE_PATH ]] || continue
echo "Source path: $SOURCE_PATH"
eyeD3 --rename=%a-%A-%n-%t "$path/$SOURCE_PATH"
done
for path in $PODCASTS
do
SOURCE_PATH=`ls -rt $path | tail -1`
[[ -n $SOURCE_PATH ]] || continue
echo "Source path: $SOURCE_PATH"
rsync -arv --delete "$path/$SOURCE_PATH" $DESTINATION
done
EMAILSCRIPT=~/scripts/email.sh
$EMAILSCRIPT
```

I'm open to any feedback!

---

### Post by tsger on 2011-06-13
Anyone know how to write a script that will list all the episodes that were downloaded during the last 'gpo download' command?

---

### Post by Knightwise on 2011-07-08
instead of using

gpo download

use

gpo download > downloaded.txt


this will give you a file of all the downloaded episodes.

---

