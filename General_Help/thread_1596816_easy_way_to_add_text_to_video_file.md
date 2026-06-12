---
title: "easy way to add text to video file"
date: 2010-10-14
forum: General Help
---

### Post by earthpigg on 2010-10-14
hi,

i've never really gotten into video editing.

how would i go about adding text to the bottom of a short video file, a la subtitles to translate from the language being spoken to one the viewer will be familiar with?

i don't want to create a fancy subtitle file, just overlay text on top of the video.

simple and easy pointy-clicky methods preferred, and i'm not looking for any fancy transitions or font effects.

---

### Post by earthpigg on 2010-10-14
playing with subtitleeditor. 

tutorials i'm seeing say to start with waveform -> generate waveform from video.

Problem is... the language being spoken is sign language, and the video has no audio track.

---

### Post by earthpigg on 2010-10-14
OK.

Got the video, and a seperate file containing the subtitles text. I can open them both in movie player and it's all synced and whatnot, now trying to figure out how to overlay the text so it's a permanent part of the video.

---

### Post by qyot27 on 2010-10-14
Since it's sign language, what you should do is while watching the video in question, use your normal text editor to write down what the appropriate times are for the subtitles to appear.  As the sentence starts to be said, pause the video and write down the time in hours:minutes:seconds, and do the same when the sentence ends.  Continue this for all of the relevant lines to be subtitled.

You can then use these times to compose an SRT script file*, which can then either be hardcoded onto the video stream with something like mencoder, or you could use a container like MKV to make the subtitles selectable (and this doesn't require re-encoding the video in any way).  Someone more knowledgeable about mencoder can comment on the exact way to do that.  It is also possible to use mencoder to transcode the softsubbed MKV to a new hardsubbed file, but again this is dependent on settings (and perhaps also the version of mencoder).


*SRT is a very simple subtitle format that can be composed in a regular text editor with minimal effort.  It's formatted like this:
```
1
hh:mm:ss,nnn --> hh:mm:ss,nnn
Subtitle text

2
hh:mm:ss,nnn --> hh:mm:ss,nnn
Subtitle text

3
hh:mm:ss,nnn --> hh:mm:ss,nnn
Subtitle text
```
(the --> and commas to separate the seconds and hundredths of seconds values are required)

Just write up the subtitles in the above format, save it with a .srt extension, and then (for the MKV option) use MKVMergeGUI from the mkvtoolnix package to add the video file, add the subtitles, and then mux them together.  Then as long as your video player supports subtitles, you can enable them on playback.

---

### Post by earthpigg on 2010-10-14
ty qyot27, that worked perfectly.

I used the subtitles i had created in subtitleeditor and it was done in 2 or 3 clicks.

---

### Post by earthpigg on 2010-10-14
thread marked as solved, and here's the vid if anyone is interested: [http://www.youtube.com/watch?v=YgtRPAuAt6s](http://www.youtube.com/watch?v=YgtRPAuAt6s)

---

