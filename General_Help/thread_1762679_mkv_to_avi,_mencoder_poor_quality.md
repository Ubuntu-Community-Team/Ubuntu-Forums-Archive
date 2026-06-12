---
title: "mkv to avi, mencoder poor quality"
date: 2011-05-19
forum: General Help
---

### Post by qwertyjjj on 2011-05-19
I have an 8Gb mkv file, which I tried to encode to avi using mencoder, it took more than 6hrs and when completed, the quality of the avi was pretty poor.
Is there a way to increase the quality or is there a program that can encode mkv files? The mkv will not play on my system without stuttering badly.
I also tried Acid Rip DVD ripper but it won't load mkv files.

---

### Post by SeijiSensei on 2011-05-19
First, Matroska ("MKV") is just a "container" as is AVI.  The quality of the video and audio tracks will depend on the codecs that were used, not the container format in which they are stored.

Next, what codec did you use to create the AVI version?  XviD?  Did you do two-pass encoding?  What video bitrate did you specify in the second pass? Here's an example:

```
mencoder -o /dev/null  -oac mp3lame -ovc xvid -xvidencopts pass=1 input.mkv
mencoder -o output.avi -oac mp3lame -ovc xvid -xvidencopts pass=2:bitrate=2000 input.mkv
```

The first pass doesn't generate any output (hence "-o /dev/null") but it does create a file in the same directory as the media source that can be used to improve the encoding in the second pass.  A bitrate of 2000 ought to be more than adequate.

The problems you're having playing the video aren't due to it being a Matroska file.  I'm guessing if its 8 GB in size, the video is probably in 1080p and encoded with H.264.  If so, the more likely obstacle is your computer's hardware.  What video card do you have?  What video player software are you using?  If it's an NVIDIA card, are you using the VDPAU driver?

---

### Post by lmn. on 2011-05-19
use handbrake..

---

### Post by qwertyjjj on 2011-05-19
> **SeijiSensei said:**
> First, Matroska ("MKV") is just a "container" as is AVI.  The quality of the video and audio tracks will depend on the codecs that were used, not the container format in which they are stored.

Next, what codec did you use to create the AVI version?  XviD?  Did you do two-pass encoding?  What video bitrate did you specify in the second pass? Here's an example:

```
mencoder -o /dev/null  -oac mp3lame -ovc xvid -xvidencopts pass=1 input.mkv
mencoder -o output.avi -oac mp3lame -ovc xvid -xvidencopts pass=2:bitrate=2000 input.mkv
```

The first pass doesn't generate any output (hence "-o /dev/null") but it does create a file in the same directory as the media source that can be used to improve the encoding in the second pass.  A bitrate of 2000 ought to be more than adequate.

The problems you're having playing the video aren't due to it being a Matroska file.  I'm guessing if its 8 GB in size, the video is probably in 1080p and encoded with H.264.  If so, the more likely obstacle is your computer's hardware.  What video card do you have?  What video player software are you using?  If it's an NVIDIA card, are you using the VDPAU driver?

1st pass?
I just used this command:
mencoder /home/j/Desktop/TheKingsSpeech/The.Kings.Speech.2010.1080p.AC3.DTS.Eng.Spa.NLSubs-DMT.mkv -oac mp3lame -ovc lavc -o output_movie.avi

It took 6hrs to run.
If I do 2 passes that is 12hrs to encode!

The vid card is a a shared mem one that I had to use as a replacement, not great. NVIDIA GEForce Go 6800 or the equivalent ATI one.

I tried using winff but get this error:
Cannot read file '/home/j/Desktop/TheKingsSpeech/TheKingsSpeech.log-0.log': No such file or directory
Error reading log file '/home/j/Desktop/TheKingsSpeech/TheKingsSpeech.log-0.log' for pass-2 encoding
Press Enter to Continue

Am I supposed to create those files first? Shouldn't the program do that?

---

### Post by JohnAStebbins on 2011-05-19
> **lmn. said:**
> use handbrake..

HandBrake can not output AVI files.  But as another poster noted, the stuttering problem is most likely due to inadequate horsepower. You will need to re-encode to a lower resolution which is something HandBrake can do.  If you would like to give it a try...

[http://handbrake.fr/](http://handbrake.fr/)

```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk handbrake-cli

```

---

### Post by andrew.46 on 2011-05-19
> **qwertyjjj said:**
> It took 6hrs to run.
If I do 2 passes that is 12hrs to encode!

Welcome to the world of video encoding :). My computer is woefully underpowered so I usually set the process running and go to bed. Best to do a test encode first of a small section though otherwise you just have to start again....

---

### Post by lmn. on 2011-05-19
> **JohnAStebbins said:**
> HandBrake can not output AVI files.  But  as another poster noted, the stuttering problem is most likely due to  inadequate horsepower. You will need to re-encode to a lower resolution  which is something HandBrake can do.  If you would like to give it a  try...

[http://handbrake.fr/](http://handbrake.fr/)

```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk handbrake-cli

```


nowadays, avi is a bad idea anyway
you probably know how mkv supports much higher compression algorithms.

would suggest whacking down the 8gb to a 1-3gb mkv looking at a bitrate  of 500-1500 you will retain most of the quality and should play with  ease on low spec systems/ resolution is not so much an issue but more of data throughput.

be sure to run a test check of your config before encoding the lot.

---

### Post by qwertyjjj on 2011-05-20
> **lmn. said:**
> nowadays, avi is a bad idea anyway
you probably know how mkv supports much higher compression algorithms.

would suggest whacking down the 8gb to a 1-3gb mkv looking at a bitrate  of 500-1500 you will retain most of the quality and should play with  ease on low spec systems/ resolution is not so much an issue but more of data throughput.

be sure to run a test check of your config before encoding the lot.

Use handbrake to recode down to 1gb? Can I select the file size or will a bitrate adjustment do that?
would mp4 be ok?
Most vides on the wev seem to be avi, why's avi a bad idea?

---

### Post by JohnAStebbins on 2011-05-20
> **qwertyjjj said:**
> Use handbrake to recode down to 1gb? Can I select the file size or will a bitrate adjustment do that?
would mp4 be ok?
Most vides on the wev seem to be avi, why's avi a bad idea?

There is a "target size" option in HandBrake 0.9.5, but it has been removed from current code and is generally not recommended.  The previous poster suggested that just lowering the bitrate (and not the resolution of the video) would be enough to make it play smoother.  In my experience, this is not correct.  You will need to reduce the resolution.  If fact, in some cases raising the bitrate can make the video play smoother.  E.g. disabling some advanced encoder features will result in higher bitrates but lower decoder cpu usage.

I suggest selecting the "Normal" preset, change the output format to mkv, then open the picture settings window and lower the resolution (uncheck "Optimal for source" first to enable the width and height controls). If your original video width was 1920, I would start by lowering it to 1280.  Encode a sample and see if it plays smoothly.  If not, keep lowering the width till it does (the height will adjust automatically to maintain the proper aspect ratio).

The "Normal" preset uses constant quality mode (as do all of handbrake's presets).  So the output file size will vary depending on the characteristics of the source you are encoding.  This is a good thing (unless you have strict file size requirements).  It means that the encoder will pick the right number of bits to use so that all your encodes will have the same quality.

mp4 doesn't support the same variety of codecs that mkv does.  For example, you can't put DTS audio in the mp4 container.  So if you have sources with DTS audio that you want to pass through to the output without re-encoding, you would need to use mkv.  mkv also supports a wider variety of subtitle formats.

avi is simply out-dated.  It's original design didn't support a lot of features that are common in modern containers (E.g. multiple audio and subtitle tracks, variable frame rate video).  Hacks have been applied to compensate for it's shortcomings in recent implementations.  But it is a standard that is on it's way out.  New devices will support newer standards better.

---

