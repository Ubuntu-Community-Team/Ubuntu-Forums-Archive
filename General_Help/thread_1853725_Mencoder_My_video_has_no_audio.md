---
title: "Mencoder: My video has no audio"
date: 2011-10-02
forum: General Help
---

### Post by Maylin86 on 2011-10-02
Hello,

I am having a problem getting my audio sound to work after I convert my  video using Mencoder.  If I just type this into the Terminal:  

mencoder Desktop/tutorial_movie.ogv -ovc xvid -oac mp3lame -xvidencopts pass=1 -o Desktop/tutorial_movie.avi

I get really good video quality, but my audio to my video is absolutely  gone.  All I want to do is just upload a video to youtube.  I've tried  rendering my video in DeVeDe, but then my video plays to fast for my  audio.  =(  So then I tried Mencoder, but once I get it converted to a  .avi, there's no audio.  I'm using Ubuntu 10.10.  I've watched many  videos as to how people used DeVeDe and Mencoder to get their videos to  convert easily (HA!!), but to no prevail have I had any success to get  my video to work. :sad:

At the beginning, I used Avidemux to copy the audio from a video and  saved it as a .mp3.  Then I took another video and opened it in Pitivi,  and then added the audio I saved from Avidemux to this new video as it's  new audio.  I saved the video and new audio together in Pitivi  and  rendered it as an ogg file and so have successfully, up to this point,  have used Mencoder to convert it to a .avi with good quality video, now  if I can just get my audio back...  X@  Also, my video dimensions are  1280X976 and I used "Desktop recorder" to make the video.  Any help  would be appreciated.  I appreciate anyone for their time and patience  in helping me with this matter.  I've been working on this all day,  about ready to try to see if my ogv file will convert better to a .avi  in kdelive...:(

Thank You,
Maylin86 

P.S.  I think the reason I'm having such a horrible time getting  anything accomplished is that I wanted to use "Desktop recorder" to do a  computer tutorial video, but I also wanted people to hear me speak.  So  I had a camera that can record, and so I took the sound off the camera  video to try to merge it with the "Desktop recorder" video to make it  one video.  I'm sure people who do computer desktop tutorials have a  microphone, and so that may be what makes all the difference on making a  video for all I know.  :|  Sorry this question is so long.  I didn't  want to be vague with my question, but I just wanted to make sure I hit  all the bases with anything that would help anyone figure out what I'm  doing wrong.:confused:

---

### Post by SeijiSensei on 2011-10-03
First, try playing the Ogg file with mplayer.  Do you hear the audio?  

Also check to make sure you have all the codecs you need with 

```

mencoder -oac help
mencoder -ovc help

```

If the Ogg file plays properly with mplayer, then I'm not sure what else to suggest.  You could try remuxing the audio and video into the Matroska (.mkv) container with mkvmerge, part of the [mkvtoolnix]("http://packages.ubuntu.com/lucid/mkvtoolnix") package.  I'm pretty sure YouTube accepts source files in Matroska.

---

