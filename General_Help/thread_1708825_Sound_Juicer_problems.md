---
title: "Sound Juicer problems"
date: 2011-03-17
forum: General Help
---

### Post by mozart1 on 2011-03-17
I am not a v/literate computer user, but have been working with Ubuntu for a few years now.  I am also new to this forum, so am hoping someone can help me.

For a number of years I was ripping & converting CD tracks via Nero's *MP3pro *on my Windows installation.  However, this is a temperamental programme, & stalls a lot for no reason at all.  

Having finally cursed Nero to hell for the next few millenia, I installed Sound Juicer, in the hope of converting these tracks into MP3s (for my iPod) on my Linux installation, thus washing my hand of Windows forever!!.  

However, when I open a CD in Sound Juicer & click "*extract*", it gives me the  error message - *"Could not open resource for writing."  *What does this mean, & how do I fix it?

mozart1

---

### Post by Vi3tHoneyX on 2011-03-17
Welcome to the Forums! :D

Have you installed the "ubuntu-restricted-extras" package?

[Community documentation on Sound Juicer]("https://help.ubuntu.com/community/CDRipping")

> 
**Installing Additional Audio  Formats**

 This section provides instructions on how to enable support for  audio formats not installed by default in Ubuntu.  
 
**MP3 Encoding**

 **WARNING:** the gstreamer LAME plugin, used in  the instructions below, is broken and will produce substandard quality MP3s. You  can track the bug [here]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483").  If you want to create MP3s, it is recommended not to use Sound Juicer; use a  program that doesn't interface with LAME through gstreamer instead. Good  examples are [RubyRipper]("http://ubuntuforums.org/community/CDRipping#RubyRipper") and [ABCDE]("http://ubuntuforums.org/community/CDRipping#ABCDE").  
     [IMG]http://ubuntuforums.org/community/CDRipping?action=AttachFile&do=get&target=mp3-profile.png[/IMG]

 If you live in a country where it is legal to use this format,  to encode MP3s, you can use Sound Juicer which uses gstreamer and the LAME mp3  encoder. The following should also work with other programs that use gstreamer:   

[LIST=1]
[*] [Enable the  universe and multiverse repositories]("http://ubuntuforums.org/community/AddingRepositoriesHowto"). Then, install the package  ubuntu-restricted-extras.
[*] If you now restart Sound Juicer via Applications > Sound  & Video > Audio CD Extractor you will find the new audio formats  available under Edit > Preferences.
[/LIST]
  
**AAC Encoding**

 If you live in a country where it is legal to use this format,  to encode AAC files, you can use Sound Juicer which uses gstreamer and the FAAC  encoder. The following should also work with other programs that use gstreamer:   

[LIST=1]
[*] [Enable the  universe and multiverse repositories]("http://ubuntuforums.org/community/AddingRepositoriesHowto"). Then, install the  gstreamer0.8-faac and gstreamer0.8-ffmpeg packages to encode  AAC files, and the gstreamer0.8-mad package to play them back.
[*]Open Sound Juicer, click "Preferences" from the "Edit Menu", click "Edit  Profiles" and choose "New". Call your new profile "AAC Encoding", or whatever  else you feel like.
[*] Edit this profile and set Gstreamerpipeline to  audio/x-raw-int,rate=44100,channels=2 ! faac ! ffmux_mp4.
[*]Finally, set File Extension to m4a, click the Active checkbox and then OK.
[*]Restart Sound Juicer for the changes to take effect.
[/LIST]
 For a full explanation of all of the options that faac takes,  run gst-inspect faac|less in the Terminal and look at the end under  "Element Properties".  
E.g. to create a low complexity AAC use  audio/x-raw-int,rate=44100,channels=2 ! faac profile=2 ! ffmux_mp4 some  mobile players better support LC AAC. 

---

