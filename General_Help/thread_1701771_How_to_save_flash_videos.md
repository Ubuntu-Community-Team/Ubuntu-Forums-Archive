---
title: "How to save flash videos?"
date: 2011-03-06
forum: General Help
---

### Post by higashi on 2011-03-06
I used to save flash videos by going to /tmp so that i can watch them later, without having to stream (and i'm not talking about youtube or anywhere else where it's against the ToU to save videos).

As many of you already know, videos are no longer saved in /tmp with flashplayer 10.2 (or they're delted immediately). I'm using Google Chrome and I've tried looking in the Cache and I've tried all kinds of things and i can't figure out how to save videos.

I would really appreciate any help you guys can give me. I wouldnt mind downgrading my version of flash (actually i'd love to do that if i knew how) but chrome seems to have flash built-in or something (?) so i have no idea how to do that.

I found a script that allows me to open whatever flash video i have open in browser with vlc, but vlc won't allow me to save as or anything. The site said that i can change the parts of the script to say mplayer to open with mplayer but i tried that and the script just stopped working. This is the script:
```
 #!/bin/bash

FLASH_TMP=`ls /tmp | grep Flash*`

if [[ $FLASH_TMP ]]; then 
     vlc /tmp/Flash*
else
     if [[ `ps x | awk '/libgcflashplayer.so\ /{print $1}'` ]]; then
          flashvids() { lsof -p `ps x | awk '/libgcflashplayer.so\ /{print $1}'` -n 2>/dev/null | perl -lne '@F = split(/ +/, $_, 9); print "/proc/$F[1]/fd/${\($F[3] =~ /(^\d+)/)[0]}" if $F[4] eq "REG" && $F[8] =~ /\(deleted\)$/'; }
     else
          flashvids() { lsof -p `ps x | awk '/libflashplayer.so\ /{print $1}'` -n 2>/dev/null | perl -lne '@F = split(/ +/, $_, 9); print "/proc/$F[1]/fd/${\($F[3] =~ /(^\d+)/)[0]}" if $F[4] eq "REG" && $F[8] =~ /\(deleted\)$/'; }
     fi

     vlc $(flashvids)
fi 
```
I figure i can save as if i open with movie player, so that would also be a great fix.

If anyone can tell me any way to save flash videos, it would be GREATLY (and i can't put enough emphasis on "greatly") appreciated!

---

### Post by Habeouscorpus on 2011-03-06
Get Download Helper for Firefox. It saves in .flv, which is played by the default movie player.

---

### Post by Shmantiv_Radio on 2011-03-06
Try Clipgrab.

---

### Post by higashi on 2011-03-06
Ah, thank you very much! :)
Any suggestions for chrome?

---

### Post by Hoopz on 2011-03-06
/home/username/.cache/google-chrome/Default/Cache

---

### Post by Rakeshvijayan on 2011-03-06
Netvideohunter is the best tool in my experiance search in google with key word 

Netvideohunter

---

### Post by zenwalker on 2011-03-06
use savevid.com keepvid.com sites to download flash videos off youtube or such sites.

---

### Post by higashi on 2011-03-06
> /home/username/.cache/google-chrome/Default/Cache
I've tried this but there is WAY too much clutter for me to have any chance of finding what I'm looking for.

> Netvideohunter is the best tool in my experiance search in google with key word 

Netvideohunter
Thanks but i already installed download helper for firefox and it works fine. I have no problem using firefox everytime i need to download something, but it would be more convenient if i can also do so with chrome.

---

### Post by Shmantiv_Radio on 2011-03-07
> **higashi said:**
> I've tried this but there is WAY too much clutter for me to have any chance of finding what I'm looking for.


Thanks but i already installed download helper for firefox and it works fine. I have no problem using firefox everytime i need to download something, but it would be more convenient if i can also do so with chrome.

You really should give ClipGrab a chance.

[http://www.omgubuntu.co.uk/2010/09/download-youtube-videos-ubuntu-clipgrab/](http://www.omgubuntu.co.uk/2010/09/download-youtube-videos-ubuntu-clipgrab/)

---

### Post by higashi on 2011-03-07
Will do, thanks. :)

---

### Post by desdecode on 2011-04-06
Here's a little bash script I wrote that reads your firefox cache, finds  flash files over a certain size, saves them in directory and opens the  directory with nautilus to browse the extracted videos/flash files:

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
```It also shows you how you can do a few different things in bash, I  originally posted it on my blog where you can find info and instructions: [http://desdecode.blogspot.com/2011/04/saving-watched-online-videos-linux.html](http://desdecode.blogspot.com/2011/04/saving-watched-online-videos-linux.html)

I hope somebody finds it useful.

---

### Post by rms-mit on 2012-04-27
There is a more manual way.

You used to just find the flv (flash video) file in /tmp/

Although it wasn't called someThingObvious.flv it was usually obvious because you could see the file time stamp matched the current time (if still being downloaded) or the time the browser finished downloading it.

Now flash deletes the file immediately after STARTing the download. BUT Linux does not actually delete the file till it is no longer opened by anything (this is why flash can still use the file in your browser)

So the file will not be seen in the /tmp directory because it is marked deleted but it is not actually delted till Flash closes it. So do the following:-

1) Use the command 'ps -ef|grep flash' to find the process ID number of the Flash process (the first number on the line, the second number is the PID of the process that launched flash ie your browser)

2) goto the /proce/<PID>/fd where PID is the PID you got from step 1. This directory lists all the files the flash process has open.

3) use 'ls -l' to list all the file flash has open. Most of these are links to network sockets and pipes etc. . . you are looking for the link to the original flash file in /tmp/ this is the file flash deleted as soon as it created.

eg. 37 -> /tmp/FlashXX0DbRQK

4) Copy the file somewhere. Be sure to use the link name (37) not the original file that link pointed to (not /tmp/FlashXX0DdRQK) as that original file has been deleted remember.

5) rename your copy with the extension .flv to make it more obvious what sort of file it is. This file is a video embedded in a flash file which many video players will play directly (eg vlc)

---

### Post by oldos2er on 2012-04-27
Thread closed. We do not support violating Youtube's (or other similar sites) TOS here.

[http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

---

