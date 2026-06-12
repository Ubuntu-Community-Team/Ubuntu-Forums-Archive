---
title: "New release: Audio Recorder Applet v0.1 seeks users."
date: 2010-08-08
forum: General Help
---

### Post by moma on 2010-08-08
Hello,

I just uploaded "Easy-to-use Audio Recorder" project to the package archive. It's available from 
[https://launchpad.net/~osmoma/+archive/rec-applet](https://launchpad.net/~osmoma/+archive/rec-applet)

Source code is hosted on:
[https://launchpad.net/rec-applet](https://launchpad.net/rec-applet)

Enjoy.

---

### Post by moma on 2010-08-17
Hello again,

I have now released v0.2 of the Audio Recorder Applet.
[https://launchpad.net/~osmoma/+archive/rec-applet](https://launchpad.net/~osmoma/+archive/rec-applet)

It has got a lot of improvements since the first release. See
[https://code.launchpad.net/~osmoma/rec-applet/trunk](https://code.launchpad.net/~osmoma/rec-applet/trunk)

With this program you can easily record ALL AUDIO that passes through your computer's loudspeakers.
I use this app to record radio castings and music from the internet.
This application is so easy and quick to use!

* There are packages for Ubuntu 10.04 (Lucid). 

* Packages for Ubuntu 9.10 (Karmic) are also ready.

* No packages for Maverick yet. 
  There are some issues when ran on the Maverick. Wait till Maverick has stabilized and this application has been fixed!

I will try to get this application translated on the Launchpad. See
[https://translations.launchpad.net/rec-applet](https://translations.launchpad.net/rec-applet)
**Please contribute with translations if you can**. It's very easy and "short" application to translate.

I consider this v0.2 release as "[COLOR="Blue"]**final**[/COLOR]" for this season. 

You are welcome to test it.

---

### Post by popeye_so on 2010-10-09
But why in the Synaptic the application is marked as unsecured? I mean why it is not in the official repository? I will install it asap after it will be! Very-very useful!!! Looking for it but please put it into repository of Ubuntu!!!

---

### Post by Ionic-user on 2010-10-10
> **popeye_so said:**
> But why in the Synaptic the application is marked as unsecured? I mean why it is not in the official repository? I will install it asap after it will be! Very-very useful!!! Looking for it but please put it into repository of Ubuntu!!!

I echo Popeye - this app is all an app should be, simple to use, easily accessible and very flexible where audio formats are concerned. It's as good, if not better in its simplicity, than the Wiretap Pro program on Macs. It's so good that I shan't be upgrading from Lucid to the Meerkat until I hear Audio Recorder runs without a hitch on the latter.

---

### Post by macaque1 on 2010-11-03
I'm running on Ubuntu 10.10 Maverick Mercat. My Audio Recorder Applet doesn't work right. MP3 option missing.

I have mp3 play in my Maverick Mercat (gstreamer0.10-fluendo-mp3 is installed on the system). Is this OK?


[IMG]http://img832.imageshack.us/img832/5849/recorder.jpg[/IMG]

---

### Post by Peter7K on 2010-12-31
> **macaque1 said:**
> I'm running on Ubuntu 10.10 Maverick Mercat. My Audio Recorder Applet doesn't work right. MP3 option missing.

I have mp3 play in my Maverick Mercat (gstreamer0.10-fluendo-mp3 is installed on the system). Is this OK?


[IMG]http://img832.imageshack.us/img832/5849/recorder.jpg[/IMG]

Since I upgraded to 10.10 the applet no longer works for me either :(

---

### Post by moma on 2011-02-12
Hello all,
The rec-applet has been replaced by a new product. 
Please see:
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)
and 
[http://i1.no/0cd0/](http://i1.no/0cd0/)

Install and run "audio-recorder" instead of the old rec-applet.
This new audio-recorder will become compatible with Ubuntu's Unity and GNOME 3.0 Desktops.

Notice: Fluendo's gstreamer0.10-fluendo-mp3 package provides MP3 playback, but no MP3 encoding (It cannot be used for audio recording, only for playback of existing MP3 files). Please see the above links for more info about supported audio formats and packages.

I would like to have help to update the translations 
[https://translations.launchpad.net/audio-recorder](https://translations.launchpad.net/audio-recorder)

---

### Post by pt123 on 2011-02-18
> **moma said:**
> 
Notice: Fluendo's gstreamer0.10-fluendo-mp3 package provides MP3 playback, but no MP3 encoding (It cannot be used for audio recording, only for playback of existing MP3 files). Please see the above links for more info about supported audio formats and packages.
Thanks for the non-applet version, can't you use LAME for mp3 encoding?

---

### Post by moma on 2011-02-20
Hello,

**EDIT:** @pt123, I think you are right. We could use the old "lame" encoder directly.  
This GStreamer pipeline might work right??

$ gst-launch-0.10 pulsesrc ! queue ! audioconvert ! lame ! filesink location=test.mp3

However, Lame encoder has been marked [deprecated...]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/gst-plugins-ugly-plugins-lame.html")
----

Audio-recorder gets its media profiles (and audio encoders) from GNOME's GConf registry. Please start gconf-editor
$ gconf-editor 

And browse to:
system -> gstreamer -> 0.10 -> audio -> profiles -> mp3/pipeline

[COLOR="DimGray"]audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc target=0 quality=6 ! xingmux ! id3v2mux [/COLOR]

You can see that the MP3 pipeline employs "lamemp3enc". 

Audio-recorder uses these pipeline-fragments from GConf-registry to do the recording job.

Please study [media-profiles.c]("http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/media-profiles.c") and [gst-recorder.c]("http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/gst-recorder.c") [look for function rec_create_pipeline(...)].

Learn more about [GStreamer pipelines...]("http://ubuntuforums.org/showpost.php?p=9589123&postcount=4")
**GStreamer is all and everything**.

Gst-inspect tool can show you details about various GStreamer plugins and elements (encoders):
$ gst-inspect
$ gst-inspect lamemp3enc
$ gst-inspect lame

---

### Post by rusljam on 2011-11-16
Hi! This is an awesome applet and I’ve  used to utilise  it. But now I’ve moved to 64 platform.  Is there a version for amd64 10.04 (Lucid)?
Thanks!

---

