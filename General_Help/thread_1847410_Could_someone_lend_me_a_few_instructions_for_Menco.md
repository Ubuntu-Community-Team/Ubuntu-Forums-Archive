---
title: "Could someone lend me a few instructions for Mencoder and CLi encoding with ffmpeg?"
date: 2011-09-20
forum: General Help
---

### Post by AlexOnVinyl on 2011-09-20
I would be really grateful if someone could please introduce me to using a Cli for encoding video - I've seen a lot of howto's here but none that explain the commands in detail and what they define.

If someone could be so nice as to help me out, that would be great.

Thank you in return.

---

### Post by howefield on 2011-09-20
Thread moved to "*General Help*"

---

### Post by andrew.46 on 2011-09-21
> **AlexOnVinyl said:**
> I would be really grateful if someone could please introduce me to using a Cli for encoding video - I've seen a lot of howto's here but none that explain the commands in detail and what they define.

Have you had a look at FakeOutdoorsman's excellent guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

If you like I can go through one of the sample commands seen on this guide, perhaps this one:

```

ffmpeg -i input \
       -acodec libfaac -aq 100 \
       -vcodec libx264 -preset slow -crf 22 \
       -threads 0 output.mp4

```

If I am understanding your question correctly?

---

### Post by AlexOnVinyl on 2011-09-21
> **andrew.46 said:**
> Have you had a look at FakeOutdoorsman's excellent guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

If you like I can go through one of the sample commands seen on this guide, perhaps this one:

```

ffmpeg -i input \
       -acodec libfaac -aq 100 \
       -vcodec libx264 -preset slow -crf 22 \
       -threads 0 output.mp4

```If I am understanding your question correctly?

Yes sir you are understanding my question perfectly, I tried looking at the man pages of mencoder but it was very vague when it got down to the conf file samples.  And it didnt exactly tell me what each of the settings meant... it gave me some syntax but the way it was written didnt really help me... so I need some extra help, maybe more explanation than what was given... if you understand me?

---

### Post by andrew.46 on 2011-09-21
Well the following is a pretty solid encoding string for FFmpeg and should furnish and excellent starting point for further usage of this amazing application:

```
ffmpeg -i input \
       -acodec libfaac -aq 100 \
       -vcodec libx264 -preset slow -crf 22 \
       -threads 0 output.mp4
```

In the interest of clarity I will keep the explanation pretty basic, there is a great deal more involved and extra choices that can be made but the very basics are:

[LIST]
[*]**ffmpeg -i input:** The -i option simply tells FFmpeg what the input file is.
[*]**-acodec libfaac:** The -acodec option selects the audio codec for the sound conversion and in this case aac sound has been selected using the external faac application. (Libraries external to FFmpeg always are named with a 'lib' prefix).
[*]**-aq 100:** The -aq option selects the quality of the sound, some use -ab to manually specify the bitrate, something like *-ab 128k* would then be used.
[*]**-vcodec libx264:** The -vcodec option selects the video codec to be used for the conversion. x264 encoding is pretty much the best encoding to use at the moment and again you see the 'lib' prefix indicating that you are not using an encoder 'native' to FFmpeg.
[*]**-preset slow:** The encoder comes with a bewildering number of options but there are several lists of options that can be selected, as has been done here, with the -preset option.
[*]**-crf 22:** This option selects the quality of the output video and indicates 'Constant Rate Factor', 22 is a reasonable number to start with.
[*]**-threads 0:** The -threads option allows a single FFmpeg process to have multiple levels of activity with this single process. This will enable your encoding job to run faster. The '0' value allows x264 to decide how many threads it can safely use rather than you selecting a value.
[*]**output.mp4:** This specifies the out file name and creates an mp4 container, another safe option here would be 'output.mkv'.
[/LIST]

Hopefully this makes things a little clearer?

---

### Post by AlexOnVinyl on 2011-09-23
> **andrew.46 said:**
> Well the following is a pretty solid encoding string for FFmpeg and should furnish and excellent starting point for further usage of this amazing application:

```
ffmpeg -i input \
       -acodec libfaac -aq 100 \
       -vcodec libx264 -preset slow -crf 22 \
       -threads 0 output.mp4
```In the interest of clarity I will keep the explanation pretty basic, there is a great deal more involved and extra choices that can be made but the very basics are:

[LIST]
[*]**ffmpeg -i input:** The -i option simply tells FFmpeg what the input file is.
[*]**-acodec libfaac:** The -acodec option selects the audio codec for the sound conversion and in this case aac sound has been selected using the external faac application. (Libraries external to FFmpeg always are named with a 'lib' prefix).
[*]**-aq 100:** The -aq option selects the quality of the sound, some use -ab to manually specify the bitrate, something like *-ab 128k* would then be used.
[*]**-vcodec libx264:** The -vcodec option selects the video codec to be used for the conversion. x264 encoding is pretty much the best encoding to use at the moment and again you see the 'lib' prefix indicating that you are not using an encoder 'native' to FFmpeg.
[*]**-preset slow:** The encoder comes with a bewildering number of options but there are several lists of options that can be selected, as has been done here, with the -preset option.
[*]**-crf 22:** This option selects the quality of the output video and indicates 'Constant Rate Factor', 22 is a reasonable number to start with.
[*]**-threads 0:** The -threads option allows a single FFmpeg process to have multiple levels of activity with this single process. This will enable your encoding job to run faster. The '0' value allows x264 to decide how many threads it can safely use rather than you selecting a value.
[*]**output.mp4:** This specifies the out file name and creates an mp4 container, another safe option here would be 'output.mkv'.
[/LIST]

Hopefully this makes things a little clearer?

You sir, are my new favorite.  Thank you so much.  I will come back to you if I have any other trouble. going to Scrapbook this thread so I can refer to it later.

Thank you very much Andrew.46

Hope the weather down there is as nice and sunny as my friends from the coast have told me :)

---

### Post by FakeOutdoorsman on 2011-09-23
I'll have to remember this thread as well to forward curious users. A little more info:
[list]
[*]**-aq** This option is encoder dependent meaning that each encoder may use different values. It will usually create a VBR output as opposed to CBR that *-ab* would give you (I think). I never did find out appropriate values for the included "native" audio encoders, but for external encoders you should refer to the help system for the encoder itself. For example, the *-aq* option is similar to *faac -q* (when using *-acodec libfaac*) or *lame -V* (when using *-acodec libmp3lame*). I generally use this option more often that *-ab*, but it's a little harder to figure out appropriate values.

[*]**-preset** This chooses certain x264 settings to give a particular encoding speed vs compression tradeoff. A slower preset gives better (or more efficient) compression at the cost of a slower encode. Choose the slowest preset that you have patience for. For a list of presets see *x264 --help*. You may notice a preset named "placebo" in that list. Ignore it as it's a joke and a waste of time.

[*]**-crf** Choose the highest value that creates an acceptable quality. A higher value is lower quality.
[/list]

Once you have the preset and crf value that you like you can use these settings for the rest of your set of files to encode. You don't need to test the whole file to figure out your settings. You can test a short section with the *-ss* and *-t* options to get a general idea.

Note that this command we are explaining to you is specific to creating H.264 video and AAC audio in MP4 container format while using a compiled FFmpeg. The syntax will be different for those using the ffmpeg binary from the repository, and can change if you occasionally update FFmpeg.

---

### Post by andrew.46 on 2011-09-23
> **AlexOnVinyl said:**
> You sir, are my new favorite.  Thank you so much. 

My pleasure :). Bear in mind that I have simplified things somewhat...

> Hope the weather down there is as nice and sunny as my friends from the coast have told me :)

Beautiful spring weather here, nice to pack the heaters away until next winter!

---

### Post by AlexOnVinyl on 2011-09-24
> **FakeOutdoorsman said:**
> I'll have to remember this thread as well to forward curious users. A little more info:
[LIST]
[*]**-aq** This option is encoder dependent meaning that each encoder may use different values. It will usually create a VBR output as opposed to CBR that *-ab* would give you (I think). I never did find out appropriate values for the included "native" audio encoders, but for external encoders you should refer to the help system for the encoder itself. For example, the *-aq* option is similar to *faac -q* (when using *-acodec libfaac*) or *lame -V* (when using *-acodec libmp3lame*). I generally use this option more often that *-ab*, but it's a little harder to figure out appropriate values.
[*]**-preset** This chooses certain x264 settings to give a particular encoding speed vs compression tradeoff. A slower preset gives better (or more efficient) compression at the cost of a slower encode. Choose the slowest preset that you have patience for. For a list of presets see *x264 --help*. You may notice a preset named "placebo" in that list. Ignore it as it's a joke and a waste of time.
[*]**-crf** Choose the highest value that creates an acceptable quality. A higher value is lower quality.
[/LIST]

Once you have the preset and crf value that you like you can use these settings for the rest of your set of files to encode. You don't need to test the whole file to figure out your settings. You can test a short section with the *-ss* and *-t* options to get a general idea.

Note that this command we are explaining to you is specific to creating H.264 video and AAC audio in MP4 container format while using a compiled FFmpeg. The syntax will be different for those using the ffmpeg binary from the repository, and can change if you occasionally update FFmpeg.

I'm fairly new to Linux/Ubuntu and UNIX systems in general.  I just started using linux a month or 2 ago, so a lot of the time using a program from the cli is definitely intimidating.  When you view it in cli as a opposed to GUI it makes it seem almost foreign, and often, because there are so many variables into making a good script for this program, I get a little overwhelmed.. This has helped a bit, but constructing my own scripts is still going to be hard..

---

### Post by AlexOnVinyl on 2011-09-24
> **andrew.46 said:**
> Well the following is a pretty solid encoding string for FFmpeg and should furnish and excellent starting point for further usage of this amazing application:

```
ffmpeg -i input \
       -acodec libfaac -aq 100 \
       -vcodec libx264 -preset slow -crf 22 \
       -threads 0 output.mp4
```In the interest of clarity I will keep the explanation pretty basic, there is a great deal more involved and extra choices that can be made but the very basics are:

[LIST]
[*]**ffmpeg -i input:** The -i option simply tells FFmpeg what the input file is.
[*]**-acodec libfaac:** The -acodec option selects the audio codec for the sound conversion and in this case aac sound has been selected using the external faac application. (Libraries external to FFmpeg always are named with a 'lib' prefix).
[*]**-aq 100:** The -aq option selects the quality of the sound, some use -ab to manually specify the bitrate, something like *-ab 128k* would then be used.
[*]**-vcodec libx264:** The -vcodec option selects the video codec to be used for the conversion. x264 encoding is pretty much the best encoding to use at the moment and again you see the 'lib' prefix indicating that you are not using an encoder 'native' to FFmpeg.
[*]**-preset slow:** The encoder comes with a bewildering number of options but there are several lists of options that can be selected, as has been done here, with the -preset option.
[*]**-crf 22:** This option selects the quality of the output video and indicates 'Constant Rate Factor', 22 is a reasonable number to start with.
[*]**-threads 0:** The -threads option allows a single FFmpeg process to have multiple levels of activity with this single process. This will enable your encoding job to run faster. The '0' value allows x264 to decide how many threads it can safely use rather than you selecting a value.
[*]**output.mp4:** This specifies the out file name and creates an mp4 container, another safe option here would be 'output.mkv'.
[/LIST]

Hopefully this makes things a little clearer?

I do have a few questions about this, how do I know what sound codecs I have installed on my Ubuntu as well as the video quality?

---

### Post by andrew.46 on 2011-09-25
> **AlexOnVinyl said:**
> I do have a few questions about this, how do I know what sound codecs I have installed on my Ubuntu as well as the video quality?

Your best bet is to follow Fakeoutdoorsman's great FFmpeg guide and then you will have access to libfaac and x264 + the most modern FFmpeg available. With the most recent version the command to show available codecs is:

```
ffmpeg -codecs
```

but conventionally when searching for available codecs you would pipe tp grep as follows:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -codecs | grep x264[/COLOR]**
ffmpeg version N-32821-g0bc5d4f, Copyright (c) 2000-2011 the FFmpeg developers
  built on Sep 24 2011 07:51:57 with gcc 4.5.2
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-zlib --enable-libxvid --enable-libfreetype --enable-x11grab --enable-nonfree --enable-gpl --enable-version2
  libavutil    51. 17. 0 / 51. 17. 0
  libavcodec   53. 17. 0 / 53. 17. 0
  libavformat  53. 13. 0 / 53. 13. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 43. 3 /  2. 43. 3
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10

```

This shows that I have the **[COLOR="Red"]E[/COLOR]**ncoder x264 for **[COLOR="Red"]V[/COLOR]**ideo encoding. As for the video quality FakeOutdoorsman's guide suggests 22 for 1 pass crf encoding, simply play around a little with this number and see what looks right on the device you are using for playback.

---

### Post by AlexOnVinyl on 2011-09-28
> **andrew.46 said:**
> Your best bet is to follow Fakeoutdoorsman's great FFmpeg guide and then you will have access to libfaac and x264 + the most modern FFmpeg available. With the most recent version the command to show available codecs is:

```
ffmpeg -codecs
```but conventionally when searching for available codecs you would pipe tp grep as follows:

```

andrew@skamandros~$ **[COLOR=Red]ffmpeg -codecs | grep x264[/COLOR]**
ffmpeg version N-32821-g0bc5d4f, Copyright (c) 2000-2011 the FFmpeg developers
  built on Sep 24 2011 07:51:57 with gcc 4.5.2
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-zlib --enable-libxvid --enable-libfreetype --enable-x11grab --enable-nonfree --enable-gpl --enable-version2
  libavutil    51. 17. 0 / 51. 17. 0
  libavcodec   53. 17. 0 / 53. 17. 0
  libavformat  53. 13. 0 / 53. 13. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 43. 3 /  2. 43. 3
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10

```This shows that I have the **[COLOR=Red]E[/COLOR]**ncoder x264 for **[COLOR=Red]V[/COLOR]**ideo encoding. As for the video quality FakeOutdoorsman's guide suggests 22 for 1 pass crf encoding, simply play around a little with this number and see what looks right on the device you are using for playback.

So let me get this straight. the 'EV' section shows the codecs and what they can be used to create as far as containers?

---

### Post by AlexOnVinyl on 2011-09-28
> **andrew.46 said:**
> Your best bet is to follow Fakeoutdoorsman's great FFmpeg guide and then you will have access to libfaac and x264 + the most modern FFmpeg available. With the most recent version the command to show available codecs is:

```
ffmpeg -codecs
```but conventionally when searching for available codecs you would pipe tp grep as follows:

```

andrew@skamandros~$ **[COLOR=Red]ffmpeg -codecs | grep x264[/COLOR]**
ffmpeg version N-32821-g0bc5d4f, Copyright (c) 2000-2011 the FFmpeg developers
  built on Sep 24 2011 07:51:57 with gcc 4.5.2
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-zlib --enable-libxvid --enable-libfreetype --enable-x11grab --enable-nonfree --enable-gpl --enable-version2
  libavutil    51. 17. 0 / 51. 17. 0
  libavcodec   53. 17. 0 / 53. 17. 0
  libavformat  53. 13. 0 / 53. 13. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 43. 3 /  2. 43. 3
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10

```This shows that I have the **[COLOR=Red]E[/COLOR]**ncoder x264 for **[COLOR=Red]V[/COLOR]**ideo encoding. As for the video quality FakeOutdoorsman's guide suggests 22 for 1 pass crf encoding, simply play around a little with this number and see what looks right on the device you are using for playback.

Also, I feel almost guilty using any sort of GUI anymore on Linux. would it be appropriate to use a GUI at all such as WinFF? or would Cli be better?

---

### Post by FakeOutdoorsman on 2011-09-28
> **AlexOnVinyl said:**
> So let me get this straight. the 'EV' section shows the codecs and what they can be used to create as far as containers?

At the top of the output from *ffmpeg -codecs* you'll see a list:
```
 D..... = Decoding supported
 .E.... = Encoding supported
 ..V... = Video codec
 ..A... = Audio codec
 ..S... = Subtitle codec
 ...S.. = Supports draw_horiz_band
 ....D. = Supports direct rendering method 1
 .....T = Supports weird frame truncation
```
Then look at a codec in the list:
```
DEA    flac            FLAC (Free Lossless Audio Codec)
```
This one is a **[color=#FF6600]D[/color]**ecoder **[color=#FF6600]E[/color]**ncoder **[color=#FF6600]A[/color]**udio codec.

> **AlexOnVinyl said:**
> Also, I feel almost guilty using any sort of GUI anymore on Linux. would it be appropriate to use a GUI at all such as WinFF? or would Cli be better?
You could use WinFF, but you will have to use the repository ffmpeg because the presets in WinFF are too old to use with anything recent. The presets in WinFF may not be "optimal", but you could always make your own I think.

---

