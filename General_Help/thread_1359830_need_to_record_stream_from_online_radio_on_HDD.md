---
title: "need to record stream from online radio on HDD"
date: 2009-12-20
forum: General Help
---

### Post by Nailox on 2009-12-20
solution:

a] system > synaptic package manager
b] search for vlc player and install it with all the related plugins you can find
c] start it from applications>sound & video
d] go to view >check "advanced controls" (if unchecked)
e] click the red dot to start recording and click it again when you decide you want to stop recording
f] the files are huge .mp3's in your home folder (places > home folder)
g] to change the record dir: in VLC > tools > preferences > input and codecs > look for "record directory and file name"
f] be careful with the copyrights and enjoy !

---

### Post by Puck7 on 2009-12-20
This blog post is for you:
[http://www.omgubuntu.co.uk/2009/12/record-multiple-radio-stream-at-same.html](http://www.omgubuntu.co.uk/2009/12/record-multiple-radio-stream-at-same.html)

---

### Post by cmcanulty on 2009-12-20
I installed the plugio but there is no record option on right click, how do I enable it?

---

### Post by mc4man on 2009-12-20
> how do I enable it? 
rhythmbox -> edit -> plugins

---

### Post by Nailox on 2009-12-20
i read the blog but i cant  install that plugin ;( when i right click on the radio there's just remove and properties

i miss my last.fm and i miss all my pals seeing what Im listening to on skype .. :(((( help me get those things back pls

this ridimbox wont even let me log in last fm and idk how to use the IM plugin to show the mp3 on skype

---

### Post by cmcanulty on 2009-12-20
I added the station I like but I get this error message when I try to play it.See screenshot attached. It looked for a plugin but found none. I can play with the movie player but I wanted to use rhythmbox so I can record. My Ubuntu auto goes to movie player for audio files though in preferred applications it is set to rhythmbox. How can I change it. I don't know where the program is on my computer. I looked for it with no luck

---

### Post by Nailox on 2009-12-21
cmcanulty, thanks for taking over my thread but can some1 actually be of some help here ?

---

### Post by RodGer GR on 2009-12-21
I think you can do it using real player. Here: [https://help.ubuntu.com/community/HowToRipRealaudioStreamsToMp3](https://help.ubuntu.com/community/HowToRipRealaudioStreamsToMp3) is really nice how to. Give it a try and tell us how it worked

---

### Post by realzippy on 2009-12-21
I use kstreamripper...(frontend for streamripper)
Works great.

---

### Post by sdowney717 on 2009-12-21
kstreamer worked only one time, now it endlessly buffers. however the stream is playing fine in exaile. verdict is buggy code.

---

### Post by sdowney717 on 2009-12-21
solution found
simply record stream using vlc player
to get red record button, select advanced controls

I tested with this celtic christmas url
simply open network stream and paste
[http://76.73.21.74:8050](http://76.73.21.74:8050)

[http://audacity.sourceforge.net/help/faq?s=recording&i=streaming](http://audacity.sourceforge.net/help/faq?s=recording&i=streaming)
apparently audacity can record what ever is playing on your speakers

---

### Post by cmcanulty on 2009-12-22
I still don't see how to make VLC play a radio station. I tried entering
[http://www.sky.fm/play/guitar](http://www.sky.fm/play/guitar)
in open network stream and nothing. I can play it from the web site but then can't record.OK I installed audacity nd still don't see how to play a station with it. I don't know why this is so hard.

---

### Post by Nailox on 2009-12-23
realplayer cant work for me - i cant find vsound- will try kstreamer-

---

### Post by Nailox on 2009-12-23
> **sdowney717 said:**
> solution found
simply record stream using vlc player
to get red record button, select advanced controls

I tested with this celtic christmas url
simply open network stream and paste
[http://76.73.21.74:8050](http://76.73.21.74:8050)

[http://audacity.sourceforge.net/help/faq?s=recording&i=streaming](http://audacity.sourceforge.net/help/faq?s=recording&i=streaming)
apparently audacity can record what ever is playing on your speakers

i think this depends on your hardware as well .. and where is "advanced controls" ??

> In the drop-down menu on Audacity's mixer toolbar, choose &#8220;Wave Out&#8221; or &#8220;Stereo Mix&#8221; as the input source. (The exact name may be different, depending on your computer's sound drivers.) When you press the **Record** button, Audacity will capture whatever sound is playing on your computer's speakersI cant find wave out or stereo mix - i have only d-mic0 and ext-mic0 - i switch them both but still no luck with audacity

just to add that audacious is bringing a very nice theme with it - go to change background - themes - customize- default aud

---

### Post by Nailox on 2009-12-23
bump yo :) tnx to sdowney for the hint -- check the 1st post

---

### Post by sdowney717 on 2009-12-23
> I still don't see how to make VLC play a radio station. I tried entering
[http://www.sky.fm/play/guitar](http://www.sky.fm/play/guitar)
in open network stream and nothing. I can play it from the web site but then can't record.OK I installed audacity nd still don't see how to play a station with it. I don't know why this is so hard.


that one is hard because there are html, java layers, something blocking you from finding the true stream url. 

there might be a tool to discover the stream url, i dont know.

If you load up exaile and click on a streamcast radio station, you can goto properties and find the url stream. or you can load it up in the browser, and if it is using mplayer, then right click and find the url link by selecting copy location, then paste into vlc

---

### Post by sdowney717 on 2009-12-23
I also played around with mplayer which you can play and record from the commandline. i was using these commandlines a few months ago. you also need to compile mplayer with mp3 support, if you want mp3 encoded files.
ubuntu version of mplayer-mencoder does not give you this mp3lame. you can do timed recordings and i am sure it also works with audio. just have to study the line to see what you want to do.

note, the "v qmax' should be 'vqmax', somehow the forum is messing up by putting in a space.

> mplayer "http://rss.cnn.com/~r/services/podcasting/cnnnewsroom/rss/~5/7y6nlSBXSn4/the.daily.11.16.cnn.m4v" :file=/home/scott/Videos/test.m4v -vc dummy;

mplayer -dumpstream //http://rss.cnn.com/~r/services/podcasting/cnnnewsroom/rss/~5/7y6nlSBXSn4/the.daily.11.16.cnn.m4v 
After recording you will get the file stream.dump. You should rename it to .rm, .ra, .asf, .wmv or other format you are using.


mplayer -dumpstream mms://url/path/to/video.wmv -dumpfile your_dumped_stream.wmv


this works, gets the stream and transcodes it
mencoder [http://rss.cnn.com/~r/services/podcasting/cnnnewsroom/rss/~5/7y6nlSBXSn4/the.daily.11.16.cnn.m4v](http://rss.cnn.com/~r/services/podcasting/cnnnewsroom/rss/~5/7y6nlSBXSn4/the.daily.11.16.cnn.m4v) -o /home/scott/Videos/test.m4v  -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame 

this works, gets the stream and transcodes it and records only 1 minute of video
mencoder [http://rss.cnn.com/~r/services/podcasting/cnnnewsroom/rss/~5/7y6nlSBXSn4/the.daily.11.16.cnn.m4v](http://rss.cnn.com/~r/services/podcasting/cnnnewsroom/rss/~5/7y6nlSBXSn4/the.daily.11.16.cnn.m4v) -o /home/scott/Videos/test.m4v  -endpos 00:01:00 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame


one hour recording of the dev/video0
mencoder /dev/video0 -o $(date +%A-%m-%d-%Y+%kH-%Mm-%Ss).avi -endpos 01:00:00 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame

two hour recording of the dev/video0
mencoder /dev/video0 -o $(date +%A-%m-%d-%Y+%kH-%Mm-%Ss).avi -endpos 02:00:00 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame

three hour recording of the dev/video0
mencoder /dev/video0 -o $(date +%A-%m-%d-%Y+%kH-%Mm-%Ss).avi -endpos 03:00:00 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame


mencoder /dev/video0 -o $(date +%A-%p-%m-%d-%Y+%T).avi -endpos 00:10:00 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame


---

