---
title: "Extract Flash video from a webpage, HELP."
date: 2011-03-30
forum: General Help
---

### Post by stchman on 2011-03-30
For the life of me I cannot get this video off this page.

[http://www.boeing.com/Features/2011/03/bds_mercury_rising_03_28_11.html](http://www.boeing.com/Features/2011/03/bds_mercury_rising_03_28_11.html)

I have tried numerous Firefox plugins and even tried clive with no success.

Thanks.

---

### Post by collisionystm on 2011-03-30
heres the more direct link to your video. This might help you in your venture....

[http://boeing.pb.feedroom.com/pb-comp/boeing/custom1/player.swf?SiteID=boeing&SiteName=Boeing&SkinName=custom1&ChannelID=f172ba8e1bc611ca29d00c7cc5932d7b490b9c4b&StoryID=2820618ef0a14345393875077b8c61c5cb2ff0f4](http://boeing.pb.feedroom.com/pb-comp/boeing/custom1/player.swf?SiteID=boeing&SiteName=Boeing&SkinName=custom1&ChannelID=f172ba8e1bc611ca29d00c7cc5932d7b490b9c4b&StoryID=2820618ef0a14345393875077b8c61c5cb2ff0f4)

---

### Post by collisionystm on 2011-03-30
try this....

open that link for your video. empty all your temp files and cookies from firefox

let your video download and buffer completely. 

open new tab and type about:cache

sift through there for your video... might be there

---

### Post by stchman on 2011-03-30
That appeared to do nothing.  Thanks for trying.

---

### Post by Script Warlock on 2011-03-30
try my favorite tool... get-flash-videos it might do the trick [http://code.google.com/p/get-flash-videos/](http://code.google.com/p/get-flash-videos/)

---

### Post by lovinglinux on 2011-03-30
That video seems to be using a real time protocol that do not store temp files in your cache. That is why all the extensions you tried failed to download the video.

---

### Post by stchman on 2011-03-30
Is there a solution?

---

### Post by lovinglinux on 2011-03-30
> **stchman said:**
> Is there a solution?

Well, there are some applications that can capture the stream, but I never tried one of those. What works, but is a pain is to capture the screen using recordmydesktop. Is real time capture, so you need to watch the entire video while capturing the screen.

Anyways, the server is setup this way so you can't download the video. So you probably shouldn't try to circumvent it.

---

### Post by ron999 on 2011-03-30
> **stchman said:**
> Is there a solution?
Yes
Install RTMPDump.
```
sudo apt-get install rtmpdump
```

Then paste this command:-
```
rtmpdump -r "rtmp://cp81026.edgefcs.net/vod/81026/boeing/20110329/" -a "vod/81026/boeing/20110329/" -f "LNX 10,1,102,64" -W "http://boeing.pb.feedroom.com/pb-comp/boeing/custom1/player.swf?SiteID=boeing&SiteName=Boeing&SkinName=custom1&ChannelID=f172ba8e1bc611ca29d00c7cc5932d7b490b9c4b&StoryID=2820618ef0a14345393875077b8c61c5cb2ff0f4" -p "http://www.boeing.com/Features/2011/03/bds_mercury_rising_03_28_11.html" -y "mp4:4b8ce7c01f273687594b52210a8368c99dc5014b.f4v" -o mp4_4b8ce7c01f273687594b52210a8368c99dc5014b.flv
```

---

### Post by lovinglinux on 2011-03-30
> **ron999 said:**
> Yes
Install RTMPDump.
```
sudo apt-get install rtmpdump
```

Then paste this command:-
```
rtmpdump -r "rtmp://cp81026.edgefcs.net/vod/81026/boeing/20110329/" -a "vod/81026/boeing/20110329/" -f "LNX 10,1,102,64" -W "http://boeing.pb.feedroom.com/pb-comp/boeing/custom1/player.swf?SiteID=boeing&SiteName=Boeing&SkinName=custom1&ChannelID=f172ba8e1bc611ca29d00c7cc5932d7b490b9c4b&StoryID=2820618ef0a14345393875077b8c61c5cb2ff0f4" -p "http://www.boeing.com/Features/2011/03/bds_mercury_rising_03_28_11.html" -y "mp4:4b8ce7c01f273687594b52210a8368c99dc5014b.f4v" -o mp4_4b8ce7c01f273687594b52210a8368c99dc5014b.flv
```

Yeah, that's the program I was referring to.

BTW, how did you get the command? It seems to be specific for that video.

---

### Post by ron999 on 2011-03-30
> **lovinglinux said:**
> 

BTW, how did you get the command? 

Look at post #9 in this thread:- [http://ubuntuforums.org/showthread.php?t=1701440]("http://ubuntuforums.org/showthread.php?t=1701440")

:)

---

### Post by lovinglinux on 2011-03-30
> **ron999 said:**
> Look at post #9 in this thread:- [http://ubuntuforums.org/showthread.php?t=1701440]("http://ubuntuforums.org/showthread.php?t=1701440")

:)

Thanks.

---

### Post by stchman on 2011-03-30
> **ron999 said:**
> Yes
Install RTMPDump.
```
sudo apt-get install rtmpdump
```Then paste this command:-
```
rtmpdump -r "rtmp://cp81026.edgefcs.net/vod/81026/boeing/20110329/" -a "vod/81026/boeing/20110329/" -f "LNX 10,1,102,64" -W "http://boeing.pb.feedroom.com/pb-comp/boeing/custom1/player.swf?SiteID=boeing&SiteName=Boeing&SkinName=custom1&ChannelID=f172ba8e1bc611ca29d00c7cc5932d7b490b9c4b&StoryID=2820618ef0a14345393875077b8c61c5cb2ff0f4" -p "http://www.boeing.com/Features/2011/03/bds_mercury_rising_03_28_11.html" -y "mp4:4b8ce7c01f273687594b52210a8368c99dc5014b.f4v" -o mp4_4b8ce7c01f273687594b52210a8368c99dc5014b.flv
```

The package rtmpdump is not available for Lucid.

---

### Post by idoitprone on 2011-03-30
Did you ever try wget?

```
wget <url>
```

```
wget http://boeing.pb.feedroom.com/pb-comp/boeing/custom1/player.swf?SiteID=boeing&SiteName=Boeing&SkinName=custom1&ChannelID=f172ba8e1bc611ca29d00c7cc5932d7b490b9c4b&StoryID=2820618ef0a14345393875077b8c61c5cb2ff0f4
```

if you want to name the file before hand

```
wget -O filename <url>
```

---

### Post by stchman on 2011-03-30
I was able to install rtmpdump from the ppa repositories.  It worked and I was able to download the full .flv file.

Thanks.

---

### Post by desdecode on 2011-04-04
Here's a little bash script I wrote that reads your firefox cache, finds flash files over a certain size, saves them in directory and opens the directory with nautilus to browse the extracted videos/flash files:

```
#!/bin/bash
# flvcache script

CACHE=~/.mozilla/firefox/xxxxxxxx.default/Cache
OUTPUTDIR=~/Videos/flvs
MINFILESIZE=2M

for f in `find $CACHE -size +$MINFILESIZE` 
do
    a=$(file $f | cut -f2 -d ' ')
    o=$(basename $f)
    if [ "$a" = "Macromedia" ]
        then
            cp "$f" "$OUTPUTDIR/$o"
    fi
done

nautilus  "$OUTPUTDIR"&
```It also shows you how you can do a few different things in bash, I originally posted it on my blog where you can find more instructions: [http://desdecode.blogspot.com/2011/04/saving-watched-online-videos-linux.html](http://desdecode.blogspot.com/2011/04/saving-watched-online-videos-linux.html)

I hope somebody finds it useful

---

