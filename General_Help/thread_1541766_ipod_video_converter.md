---
title: "ipod video converter"
date: 2010-07-29
forum: General Help
---

### Post by tal32123 on 2010-07-29
Is there any video converter software for ubuntu/kubuntu/linux i need to convert videos for my ipod

---

### Post by didac on 2010-08-05
Try Avidemux. It has GUI and comes with an option to encode to iPod. Menu: Auto => Apple

Download:

sudo apt-get install avidemux

---

### Post by amsterdamharu on 2010-08-05
ffmpeg is a command line based converter but you can use winff for the gui.

If avidemux doesn't work, if ffmpeg doesn't work try to install libavcodec-unstripped-52

```
sudo apt-get install libavcodec-unstripped-52
```

---

### Post by birdmanuk on 2010-08-05
Give handbrake a try, it's awesome.

sudo add-apt-repository ppa:stebbins/handbrake-snapshots

Once installed, either use the GUI and the iPod / iPhone presets, or run the CLI version.

---

### Post by bakegoodz on 2010-08-05
Another vote for Handbrake

---

### Post by FakeOutdoorsman on 2010-08-05
Another option is FFmpeg (as mentioned before).  An iPod encoding example is shown here:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

The example command will encode in high quality, attempt to copy any metadata, and will automatically resize yor video to the (hopefully) correct dimensions.

---

### Post by marcusfurius on 2010-08-07
You could also try [Furius iConverter]("http://www.marcus-furius.com/?page_id=200"). This is a GUI for ffmpeg designed specifically for the iPod / iPhone.
Some of it's key features are:
Easy to use
Converts any video
No configuration needed
Supports drag and drop
Supports batch conversion
Automatically creates high quality videos for your device
Automatically fixes codec errors
Automatically detects source video aspect ratio and converts appropriately

[IMG]http://www.marcus-furius.com/wp-content/uploads/2010/08/scrot1-300x185.png[/IMG]

---

### Post by tal32123 on 2010-08-07
Thank yo guys very much :)

---

### Post by tal32123 on 2010-08-15
sorry, but none of these options worked for me. winff doesnt have an ipod touch/iphone preset and furious doesnt work for some reason

---

### Post by MooPi on 2010-08-15
Would you be able to handle some command line mplayer/mencoder fun.
I have used mencoder to convert video for my palm phone. Have a couple of custom scripts to scale and encode. I guess it all depends on the input files.

---

### Post by tal32123 on 2010-08-15
> **MooPi said:**
> Would you be able to handle some command line mplayer/mencoder fun.
I have used mencoder to convert video for my palm phone. Have a couple of custom scripts to scale and encode. I guess it all depends on the input files.

i guess, but i rather not have to type the whole file names and directories. i also need to see the status so i can know it works. but ultimately i really want a gui lol :)

---

### Post by Agent Smith on 2010-08-15
Winff can be set to do iphone/touch devices. If you install it in windows first, you can then export the ipod settings and then import them into your linux version as i did. I had to restrt the program and now i can convert my videos to my iphone. If the export/import doesnt work you can always write down the settings from windows install and type them in manually. Hope this helps.

---

### Post by Agent Smith on 2010-08-15
These are my settings for iphone/touch

Preset Command Line:

-r 29.97 -vcodec libx264 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -crf 21 -bt 256k -refs 1 -coder 0 -me_method full -me_range 16 -subq 5 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -s 480x320 -aspect 16:9 -acodec libfaac -ab 112kb -ar 48000 -ac 2

Output File Extention: m4v "no "." before" 
Catagory: ipod/itunes
Preset Name: ipoditunesWS
Prerset Label: iPhone WideScreen

---

### Post by birdmanuk on 2010-08-15
I really think Handbrake fits the bill for your requirements....

Easy to use GUI with iPhone presets. If you don't mind the command line, then it's simply:-

./HandBrakeCLI -i /Volumes/DVD -o movie.mp4 --preset="iPhone & iPod Touch" 

I'm amazed by the quality of the encoding, I have recently made my DVD collection digital, it's hard to tell it's not on DVD, but only 700mb :-)

---

### Post by tal32123 on 2010-08-15
> **Agent Smith said:**
> Winff can be set to do iphone/touch devices. If you install it in windows first, you can then export the ipod settings and then import them into your linux version as i did. I had to restrt the program and now i can convert my videos to my iphone. If the export/import doesnt work you can always write down the settings from windows install and type them in manually. Hope this helps.

i cant get the preset off windows, can you please upload it or tell me where i can download it?

---

### Post by TimEnid on 2010-08-15
my vote is for handbrake.

---

### Post by Cpierce on 2010-08-15
Another vote for Handbrake GUI

---

### Post by tal32123 on 2010-08-15
> **TimEnid said:**
> my vote is for handbrake.

how exactly do i get it, since i tried to download it, but couldnt.......i know im a noob, can you please give me a direct link to the .deb or how to install?

---

### Post by tal32123 on 2010-08-16
> **tal32123 said:**
> how exactly do i get it, since i tried to download it, but couldnt.......i know im a noob, can you please give me a direct link to the .deb or how to install?

never mind i found it. all seems well.

---

