---
title: "Youtube flash videos no longer in temp folder"
date: 2011-02-18
forum: General Help
---

### Post by cloyd on 2011-02-18
I used to be able to save you tube flash videos by copying them out of the tmp folder after the file had been completely buffered, and before closing the tab or that particular video. They no longer show up there.  Anyone know what has changed?  Download helper will do the same thing, but what happened?

---

### Post by sisco311 on 2011-02-18
The new Flash plugin stores the temp files in the web browser's cache directory.

---

### Post by cloyd on 2011-02-18
Thanks. Had to hunt a bit . . . the mozilla  folder was hidden (.mozilla), and I didn't know where. Found it

---

### Post by a2z on 2011-02-18
> **sisco311 said:**
> The new Flash plugin stores the temp files in the web browser's cache directory.

do you know how to put it back to tmp?
Thanks

---

### Post by kiridude on 2011-02-19
I'm curious too...and why?

---

### Post by luigi_mb on 2011-02-19
Possibly because the system may clean /tmp when shutting down.

/luigi

---

### Post by PaulReaver on 2011-02-19
#!/bin/bash

args=("$@")

args=`echo $args | sed 's/[/]$//'`

pids=`eval pgrep -f flashplayer`
for pid in $pids
do
lsoutput=$(lsof -p $pid | grep '/tmp/Flash[^ ]*')

IFS=$'\n'
for line in $lsoutput; do
lsout1=`echo $line | awk '{print "/proc/" $2 "/fd/" $4}' | sed 's/[rwu]$//'`
lsout2=`echo $line | awk '{print $9}' | awk -F '/' '{print $3}'`

if [ -n "$args" ];then
if [ -d $args ]; then
echo "Copying $lsout2 to $args/"
eval "cp $lsout1 $args/$lsout2.flv"
else
echo "The directory \"$args\" doesn't exist"
break
fi
else
echo "Copying $lsout2"
eval "cp $lsout1 $lsout2.flv"
fi

done
done





this little work of script genius will dump open cached flash videos to home directory on flash 10.2 :)

---

### Post by kiridude on 2011-02-20
> **PaulReaver said:**
> #!/bin/bash

args=("$@")

args=`echo $args | sed 's/[/]$//'`

pids=`eval pgrep -f flashplayer`
for pid in $pids
do
lsoutput=$(lsof -p $pid | grep '/tmp/Flash[^ ]*')

IFS=$'\n'
for line in $lsoutput; do
lsout1=`echo $line | awk '{print "/proc/" $2 "/fd/" $4}' | sed 's/[rwu]$//'`
lsout2=`echo $line | awk '{print $9}' | awk -F '/' '{print $3}'`

if [ -n "$args" ];then
if [ -d $args ]; then
echo "Copying $lsout2 to $args/"
eval "cp $lsout1 $args/$lsout2.flv"
else
echo "The directory \"$args\" doesn't exist"
break
fi
else
echo "Copying $lsout2"
eval "cp $lsout1 $lsout2.flv"
fi

done
done





this little work of script genius will dump open cached flash videos to home directory on flash 10.2 :)

Nice one!

---

### Post by noclue_27 on 2011-02-20
> **cloyd said:**
> Thanks. Had to hunt a bit . . . the mozilla  folder was hidden (.mozilla), and I didn't know where. Found it

Where'd you happen to find it? I've been looking for a while.. but not too good at this >.<

---

### Post by Vaphell on 2011-02-20
press ctrl+h to unhide bunch of .whatever in your home folder (names starting with dots, names ending with tildas = hidden). .mozilla keeps your local firefox config, browser's cache is inside your profile folder.

---

### Post by woofti on 2011-02-21
Thanks I enjoyed that and a friend was watching and as he said, powerful.

---

### Post by chetancrasta on 2011-02-25
Hello everyone.
None of the methods described by previous posters are as convenient as just copying the flash file from the tmp directory.

Therefore, what I did was downgrade my Flash to 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

### Post by bike756 on 2011-02-28
I can see the video file loading in the .mozilla cache directory until it grows to 25MB. then it stops growing and when the video finishes loading in the browser, that file disappears. Where did it go?? How can I download videos larger than 25 megabytes? and hopefully videos that are complete?

---

### Post by TeoBigusGeekus on 2011-02-28
See my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread.

---

### Post by vagrale13 on 2011-03-05
> **chetancrasta said:**
> Hello everyone.
None of the methods described by previous posters are as convenient as just copying the flash file from the tmp directory.

Therefore, what I did was downgrade my Flash to 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.
Works great!
The only change where i did, i put the file **libflashplayer.so** to the folder [B]/home/user/.mozilla/plugins 
[/B]

---

### Post by jamesbon on 2011-03-23
Well what I did was followed instructions here
[http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html#more](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html#more)

and downgraded to old version of flash.
Can any one tell if this problem does not exist in Flash 11 i.e. the cached video can be accessed from /tmp and it does not gets deleted.

---

### Post by mjuchli on 2011-04-05
I see this is marked as solved but here is my method anyway. I am using Flash 10.2r153 on Ubuntu 10.10 AMD64, and videos tend to disappear from the cache as soon as they are fully buffered.

In firefox, type "about:cache" into the address bar and it will tell you the location of your cache. Mine is ~/.mozilla/firefox/od8t71bi.Default/Cache/

Make a script like this:
```
#!bash
## -v=verbose -c=checksum -r=recursive
while true
do rsync -vcr --min-size=1M ~/.mozilla/firefox/od8t71bi.Default/Cache/ ~/cache_mirror
echo "Sleeping for 1"
sleep 1
done
```This script uses rsync to mirror my firefox cache into the folder "cache_mirror" repeatedly at 1 second intervals. It compares file checksums and only copies files larger than 1M. So far it has worked flawlessly with about 6 videos.

My procedure is:
1. Clear firefox cache (CTRL-SHIFT-DEL, de-select everything but "cache")
2. Start script in a terminal
3. Open page with video on it.
4. Wait until video is fully buffered.
5. Stop script with CTRL-C

I hope someone finds that useful :)

---

### Post by Robert Lutken on 2011-04-08
I was wondering this as well, thanks Guys & Girls :)

---

### Post by chetancrasta on 2011-04-10
Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

---

### Post by Grandma_DOG on 2011-04-15
How is the script used?  Obviously copy and paste it into a file, then make it executable. But does it have to be run every time I boot up, or put into a particular directory?

> **PaulReaver said:**
> #!/bin/bash

args=("$@")

args=`echo $args | sed 's/[/]$//'`

pids=`eval pgrep -f flashplayer`
for pid in $pids
do
lsoutput=$(lsof -p $pid | grep '/tmp/Flash[^ ]*')

IFS=$'\n'
for line in $lsoutput; do
lsout1=`echo $line | awk '{print "/proc/" $2 "/fd/" $4}' | sed 's/[rwu]$//'`
lsout2=`echo $line | awk '{print $9}' | awk -F '/' '{print $3}'`

if [ -n "$args" ];then
if [ -d $args ]; then
echo "Copying $lsout2 to $args/"
eval "cp $lsout1 $args/$lsout2.flv"
else
echo "The directory \"$args\" doesn't exist"
break
fi
else
echo "Copying $lsout2"
eval "cp $lsout1 $lsout2.flv"
fi

done
done





this little work of script genius will dump open cached flash videos to home directory on flash 10.2 :)

---

### Post by suniyo on 2011-07-31
It is not stored in my browser's cache folder in default profile which I am using. I'm using Firefox 6.0 on Ubuntu 10.04 LTS. Did Flash plugin changed the default location again??

---

### Post by suniyo on 2011-07-31
I am using flash 10.03 on ubuntu 10.04 and no videos are stored in either /tmp or .mozilla/firefox/profile/cache. 

To conform it I checked the about:cache in firefox to find the location of the cached video but on the page for the video url:
**Cache entry information**

it says

file on disk:     none

So may be it is not storing the cached copy locally at all, or am I missing something here?

It seems like it is not storing the copy because .mozilla/firefox/profile/cache folder is also empty. I use more than one profile on firefox and all cache folders in various profiles are empty.

---

### Post by suniyo on 2011-07-31
other information from the cache entry:

**Cache entry information**

         key:     [http://v2.cache5.c.youtube.com/videoplayback?sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Calgorithm%2Cburst%2Cfactor%2Coc%3AU0hQR1FRTl9FSkNOMF9JS1JF&fexp=901318%2C904532%2C907301&algorithm=throttle-factor&itag=34&ip=0.0.0.0&burst=40&sver=3&signature=B7254DADE3761B0357AE77FD7FCEBADC56FD1749.7006EB48DF9C985CFC79AF04386B7ADD6ED60270&expire=1312160400&key=yt1&ipbits=0&factor=1.25&id=4d9ac605ac95ee74&redirect_counter=1](http://v2.cache5.c.youtube.com/videoplayback?sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Calgorithm%2Cburst%2Cfactor%2Coc%3AU0hQR1FRTl9FSkNOMF9JS1JF&fexp=901318%2C904532%2C907301&algorithm=throttle-factor&itag=34&ip=0.0.0.0&burst=40&sver=3&signature=B7254DADE3761B0357AE77FD7FCEBADC56FD1749.7006EB48DF9C985CFC79AF04386B7ADD6ED60270&expire=1312160400&key=yt1&ipbits=0&factor=1.25&id=4d9ac605ac95ee74&redirect_counter=1)           fetch count:     2           last fetched:     2011-07-31 23:51:54           last modified:     2011-07-31 23:40:34           expires:     2011-08-01 23:36:17           Data size:     3955524           file on disk:     none           Security:     This document does not have any security info associated with it.              Client:     HTTP           request-method:     GET           response-head:     HTTP/1.1 200 OK Last-Modified: Mon, 01 Feb 2010 14:00:13 GMT Content-Type: video/x-flv Date: Sun, 31 Jul 2011 18:08:26 GMT Expires: Sun, 31 Jul 2011 18:08:26 GMT Cache-Control: max-age=86400 Accept-Ranges: bytes Content-Length: 3955524 X-Content-Type-Options: nosniff Server: gvs 1.0

---

### Post by tyxle on 2011-08-01
Beautiful.

---

### Post by faical117 on 2012-03-16
#!/bin/bash

args=("$@")

args=`echo $args | sed 's/[/]$//'`

pids=`eval pgrep -f flashplayer`
for pid in $pids
do
lsoutput=$(lsof -p $pid | grep '/tmp/Flash[^ ]*')

IFS=$'\n'
for line in $lsoutput; do
lsout1=`echo $line | awk '{print "/proc/" $2 "/fd/" $4}' | sed 's/[rwu]$//'`
lsout2=`echo $line | awk '{print $9}' | awk -F '/' '{print $3}'`

if [ -n "$args" ];then
if [ -d $args ]; then
echo "Copying $lsout2 to $args/"
eval "cp $lsout1 $args/$lsout2.flv"
else
echo "The directory \"$args\" doesn't exist"
break
fi
else
echo "Copying $lsout2"
eval "cp $lsout1 $lsout2.flv"
fi

done
done

---

### Post by amirmku on 2012-06-07
> **faical117 said:**
> #!/bin/bash

args=("$@")

args=`echo $args | sed 's/[/]$//'`

pids=`eval pgrep -f flashplayer`
for pid in $pids
do
lsoutput=$(lsof -p $pid | grep '/tmp/Flash[^ ]*')

IFS=$'\n'
for line in $lsoutput; do
lsout1=`echo $line | awk '{print "/proc/" $2 "/fd/" $4}' | sed 's/[rwu]$//'`
lsout2=`echo $line | awk '{print $9}' | awk -F '/' '{print $3}'`

if [ -n "$args" ];then
if [ -d $args ]; then
echo "Copying $lsout2 to $args/"
eval "cp $lsout1 $args/$lsout2.flv"
else
echo "The directory \"$args\" doesn't exist"
break
fi
else
echo "Copying $lsout2"
eval "cp $lsout1 $lsout2.flv"
fi

done
done

How to make this work? please help

---

### Post by VanillaMozilla on 2012-06-07
If you guys want an easy way to do this, you can just add the Video DownloadHelper extension to Firefox.  That will get you going with a few clicks.  I rarely recommend extensions, but this works.

---

### Post by vasa1 on 2012-06-07
There's an admin notice about saving YouTube videos. Maybe it's not prominent enough.

---

### Post by VanillaMozilla on 2012-06-07
> **vasa1 said:**
> There's an admin notice about saving YouTube videos. Maybe it's not prominent enough.
Maybe somewhere [in here.](http://ubuntuforums.org/showthread.php?t=766683)  There are only 176 pages of helpful hints, nicely collected into a single, easy-to-read thread.  :)

---

### Post by oldos2er on 2012-06-07
Closed. Please read [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

---

