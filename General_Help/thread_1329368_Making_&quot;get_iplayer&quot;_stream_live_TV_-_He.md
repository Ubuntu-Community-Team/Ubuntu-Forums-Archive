---
title: "Making &quot;get_iplayer&quot; stream live TV - Help Needed"
date: 2009-11-17
forum: General Help
---

### Post by MrGrumpyArse on 2009-11-17
Hi, Ive only been using Ubuntu for about a month(ubuntu karmic 64 bit) , but so far with the help of google and these forums things are going well.

My problem now is im unable to get the "get_iplayer" program to stream live tv successfully, i can however download and play the resulting downloads in mplayer / vlc etc.

[http://linuxcentre.net/getiplayer](http://linuxcentre.net/getiplayer)

I believe i have everything installed correctly (including flvstreamer) and have been trying the following command from the get_player site / documentation.

```
get_iplayer --stream --modes=flashnormal --type=livetv 'BBC Two'
  --player='mplayer -cache 512 -'
 
```So far i have discovered, by playing in terminal that to launch mplayer (as downloaded through synaptic) from terminal, i have to use the command "gmplayer".  So after several attempts with the original command from the website i have replaced "mplayer" with "gmplayer".

The result of entering the original command with either "mplayer" or "gmplayer" into terminal is that the requested "live tv channel", in this example BBC2, appears to be streaming, but the output is merely a stream of symbols within terminal which continues until i force it to quit, my net monitor screenlet also seems to indicate that a file is being streamed.  Mplayer isnt launched at all.

I am probably missing something obvious, and have searched both here and on the get_iplayer site to no avail.

So if anyone could point me in the right direction it would be much appreciated.

Regards

Mark

---

### Post by soni1770 on 2009-11-17
umm, you could just start to download the file then afer a few min click on the .mov file and play with vlc etc, think that's working for me?

---

### Post by khelben1979 on 2009-11-17
Perhaps you should give other software a try as well? [Check this out]("http://linux.wareseeker.com/free-streaming-tv/").

---

### Post by MrGrumpyArse on 2009-11-17
Thanks for your replies,

Soni1770 - have just tried the method you suggested, interesting result - VLC played the partial.avi.flv that was produced fine. Mplayer however played only the sound and showed a still image from the file. Which to me suggests a codec issue with mplayer?

Also tried adding the full path to the mplayer executive (if thats the right word) in the get_iplayer options file which now has the line - mplayer /user/bin/gmplayer.

This now launches mplayer if i stream a "non live" program which appear to be mp4.  This didnt work before i added the path.

So some progress made i suppose, but id still like to get the live stream to work "properly" if possible.

Khelben1979 - Thanks for the link, that might prove useful, if all else fails ;)

But for now i will keep plugging away with the get_iplayer / mplayer / vlc route

Thanks again

Mark

---

### Post by soni1770 on 2009-11-17
good luck, wish i knew a bit more about mplayer so i could help:)

---

