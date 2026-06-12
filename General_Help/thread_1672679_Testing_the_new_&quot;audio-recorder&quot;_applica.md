---
title: "Testing the new &quot;audio-recorder&quot; application."
date: 2011-01-21
forum: General Help
---

### Post by moma on 2011-01-21
Hello,

I would like to have help to test the new audio-recorder program for Ubuntu. This new software replaces the old "rec-applet" product. Rec-applet was a toolbar applet, but applets cannot be used neither in the forthcoming Unity nor GNOME 3.x Desktops. So here comes a very new audio-recorder that rocks in all GNOME 2.x/3.x and Unity Desktops, in all Linuxes.

[[img]http://bildr.no/thumb/805395.jpeg[/img]](http://bildr.no/view/805395) [[img]http://bildr.no/thumb/844348.jpeg[/img]](http://bildr.no/view/844348)

This new recorder has a lot of awesome features, eg. it can automatically record your Skype calls. By default it puts all recordings to $HOME/Audio directory.

You can read more about it here.
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

There is no ready-made packages yet, so you have to compile it from source. The compilation is very easy. 

0) First read the README and INSTALL files.

1) Then install dependencies (as told in the INSTALL file). Compilation from source requires more packages than normal program execution.

**EDIT: This is for GTK 2.x. The latest audio-recorder v0.6+ requires GTK/GDK 3 header files and libraries.**
```
sudo apt-get install libgtk2.0-dev libglib2.0-dev libgconf2-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libgnome-media-dev libpulse-dev libdbus-1-dev libdbus-glib-1-dev build-essential autotools-dev automake autoconf gettext  intltool bzr
```
Install support for audio formats:
```
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-base

```
Get also these packages if you want more audio encoders (mp3, and that type of closed things):
gstreamer0.10-plugins-ugly 
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-bad-multiverse

You may also need the "libappindicator-dev" package. 
Please read the below notes.
```
sudo apt-get install libappindicator-dev
```
2) Download the source from Launchpad
```
bzr branch lp:audio-recorder
```

3) Configure, compile and install (copy & paste one line at a time)
```
cd audio-recorder*

./configure

make clean 

make

sudo make install
```
4) Test it
```
audio-recorder
```
You can also start it from Applications -> Sound & Video menu. 

Activate the tray-icon in the Settings -> [Additional settings] dialog.

Notice that you can click/**right-click** the tray icon.
You can also **right-click** the [Start recording] button in the GUI. 
You can also right-click the [Close] button.

Please report bugs and wishes to:
[https://bugs.launchpad.net/audio-recorder](https://bugs.launchpad.net/audio-recorder)

5) I would like to have help to 
* Make new icons and images for this product (see the pixmaps/ folder).
* Improve the *.html manuals in the data/ folder. Better English.
* Find bugs.

6) More Translations.
You are welcome to add new translations. 
[https://translations.launchpad.net/audio-recorder](https://translations.launchpad.net/audio-recorder)
Also the old translations (which I copied from the rec-applet product) need to be updated.

Known issues: 
* Recording from/via Totem does not work well. Totem does not fully respect the MPRIS standard.
* Application icon is not visible in the Applications -> Sound & Video menu. 

Please report your findings here or file a bug-report.

This app should rock in Lucid (10.04), Maverick (10.10) and Natty (11.04 daily) distros.

And of course, it is completly GPL.

[COLOR="Red"]Notes[/COLOR]: 

The libappindicator-dev package:

The new Unity Desktop (and I think GNOME 3.0 as well) will have new type of systray icons (AppIndicators).
You can test the AppIndicators by editing the **src/systray-icon.c** file.
Remove or comment/uncomment the "#undef HAS_APP_INDICATOR" line. I forgot the line there before uploading the source.

AppIndicators need also "libappindicator-dev" package (during compilation) and "indicator-applet" package (during runtime). You may test the compilation and runtime by installing/removing these packages. After installing the package, run all; ./configure && make && sudo make install.

---

### Post by VastOne on 2011-01-21
Welcome back Moma!  Good to see you again...

I have compiled and testing and I am impressed

A couple of questions...

At Launchpad there is this quote

The recording can be atomatically controlled by:
* RhytmBox audio player.
* Banshee audio player.
* Amarok and other MPRIS compatible players.

Can you elaborate more on this and the settings to accomplish this?  I have looked but do not see the method to link a player to Audio-Recorder

Is there an option or method so that you can stop recording on silence, start again on a new sound, AND have it start as a new file/name upon the new sound/recording?  

Great work!

---

### Post by moma on 2011-01-21
Hello and good to hear from you too.
> **VastOne said:**
> Can you elaborate more on this and the settings to accomplish this?  I have looked but do not see the method to link a player to Audio-Recorder

Some Media Players can control the recording via DBus. So if you start a player (let's say Banshee) and you change the song/track, it will send a message to the audio-recorder via DBus. 

Media Players usually send several types signals/messages to the DBus: Track change signal, Play song signal, Pause song and Stop/Quit signals.

Some well-designed players are [MPRIS-compatible]("http://xmms2.org/wiki/MPRIS"). This means that the DBus-interface and messages are well specified and know. Amarok is such a good player. It implements the DBus interface well. See the src/dbus-mpris.c (and src/dbus-player.c) modules.

RhytmBox and Banshee (and Totem) _do not_ follow the [MPRIS-spesification]("http://en.wikipedia.org/wiki/Media_Player_Remote_Interfacing_Specification") to the point, so I had to make special DBUs-modules for them. See these handcrafted modules src/dbus-banshee.c and src/dbus-rhythmbox.c. 

In an ideal world, all Media Players would follow the MPRIS-spec 100%, but this is not the case yet. 

So currently, we have Amarok, Banshee and RhytmBox that work well with this new audio-recorder. All these communicate through the DBus. Other players can be added by coding new dbus-xxx.c modules.

We have also Skype that uses DBus messaging. See src/dbus-skype.c. The benefit of this Skype-interface i obvious. 

IMPORTANT:
It's up to you (the end users) to find the meaning/usefulness/benefit of this AUDIO RECORDER - MEDIA PLAYER interface. What is it good for? 
Myself, I like to record radio broadcastings from Banshee. The recording is controlled by Banshee.
----

> **VastOne said:**
> Is there an option or method so that you can stop recording on silence, start again on a new sound, 
AND have it start as a new file/name upon the new sound/recording?

Yes, you can pause the recording when signal level drops under a certain value. Eg. this timer command might work:

start if|on voice|audio|sound DELAY LEVELVALUE.

Samples:
start if sound 
start on sound 3s
start on voice 3s 4.5%
start if sound 3s -17 dB

These commands should automatically PAUSE when the level drops under 4.7%. You can either type the value in % or dB (decibels).

Unfortunately this command does not change the output file. It records everything to the same file until you stop/restart the recording.

It maybe hard to find a correct level-value (in decibel dB or %). The manual page for the Timer is not complete yet.

You may start the audio recorder with --debug-signal=1 option to see the level values (RMS value) in dB and %. Pay attension to the very last value on the line (Avg.rms). That's what the src/timer.c (fed by src/gst-listener.c) is testing against.

$ audio-recorder -d 1
Then play sound, select the device and activate the timer.

Study the src/timer.c module.

**Thanks for testing this program.**

---

### Post by VastOne on 2011-01-21
> **moma said:**
> Hello and good to hear from you too.


Some Media Players can control the recording via DBus. So if you start a player (let's say Banshee) and you change the song/track, it will send a message to the audio-recorder via DBus. 

Media Players usually send several types signals/messages to the DBus: Track change signal, Play song signal, Pause song and Stop/Quit signals.

Some well-designed players are MPRIS-compatible. This means that the DBus-interface and messages are well specified and know. Amarok is such a good player. It implements the DBus interface well. See the src/dbus-mpris.c (and src/dbus-player.c) modules.

RhytmBox and Banshee (and Totem) do not follow the MPRIS-standard to the point, so I had to make special DBUs-modules for them. See these handcrafted modules src/dbus-banshee.c and src/dbus-rhythmbox.c. 

In an ideal world, all Media Players would follow the MPRIS-spec 100%, but this is not the case yet. 

So currently, we have Amarok, Banshee and RhytmBox that work well with this new audio-recorder. All these communicate through the DBus. Other players need too be added via programming (by adding new dbus-xxx.c modules) to the project.

We have also Skype that uses DBus messaging. See src/dbus-skype.c. The benefit of this Skype-interface i obvious. 

IMPORTANT:
It's up to you (the end users) to find the meaning/usefulness/benefit of this AUDIO RECORDER - MEDIA PLAYER interface. What is it good for? 
I like to record radio broadcastings from Banshee. The recording is controlled by Banshee.
----



Yes, you can pause the recording when signal level drops under a certain value. Eg. this timer command might work:

start if voice/audio/sound DELAY LEVELVALUE.

Samples:
start if sound 
start if sound 3s
start if voice 3s 4.5%
start if sound 3s -17 dB

These commands should automatically PAUSE when the level drops under 4.7%. You can either use %-values or decibel (dB) values.

Unfortunately this command does not change the output file. It records everything to the same file until you stop/restart the recording.

It maybe hard to find a correct level-value (in decibel dB or %). The manual page for the Timer is not complete yet.

You may start the audio recorder with --debug-signal=1 option to see the level values (RMS value) in dB and %. Pay attension to the very last value on the line (Avg.rms). That's what the src/timer.c (feeded by src/listener.c) is testing against.

$ audio-recorder -d 1
Then play sound, select the device and set the timer.

Study the src/timer.c module.

Yes, I work with dbus quite a bit.. I thought that there was some physical link you were referring to like an add on or plug in

All of the timer options are well displayed in the help file, I was just hoping for the ability to separate files but that is not possible

Thanks

---

### Post by surajit697 on 2011-01-25
When this audio-recorder will be available? Inform here please...

---

### Post by moma on 2011-01-28
I will make installation packages for audio-recorder in week 6 (that is around 7. - 12. feb). Will be visiting [Madeira...]("http://en.wikipedia.org/wiki/Madeira")/Funchal till then. Talk to you later.
Thanks for testing this product.

[SIZE="1"]ps. check also [ClipArt-Finder]("https://launchpad.net/~osmoma/+archive/clipart-finder")[/SIZE]

---

### Post by surajit697 on 2011-01-30
@moma
Sorry for the miscommunication. you thought that I have tested this software. I didn't.
I am a beginner and I am in a need of this type of software, so i searched the forum and found the topic previously continuing "[B]Recording the internal audio is far too complicated task."
[/B]I tried to install the software through the steps you mentioned, but at the step "2) Download the source from Launchpad" when I typed that command, it says that "you have not informed bzr of your launchpad id, and you must do this to write to launchpad or access private data." and I can not continue further.

---

### Post by tredegar on 2011-01-30
> "you have not informed bzr of your launchpad id, and you must do this to write to launchpad or access private data." and I can not continue further.

I just tried this 
```
tred@vaio2:~$ bzr branch lp:audio-recorder
You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See "bzr help launchpad-login".
Branched 28 revision(s).                                                                                                           
tred@vaio2:~$ 

```
but the directory **audio-recorder** was still downloaded and filled with files.

It probably worked for you too, take a look for **audio-recorder**

PS: The application seems to work just fine (10.04)

---

### Post by moma on 2011-02-08
Hello again,

Installation packages for Ubuntu 10.10 (Maverick) are now ready. Both 32 og 64bit systems are supported.

Please see: 
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

I hope you will find this program useful.

New translations are welcomed. Please see
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder) and follow the "Translations" link.

---

### Post by mocha on 2011-03-01
Thanks for this app.  I can't seem to get the pause on silence to work very well.  I tried this,

```
start if voice 1s -22dB
pause if silence 1s -22dB
```

I also tried just the pause line.  It seems that there is some insensitivity to some of the samples coming over my line input, because the debug screen will show something like this:

```
Time: 0:01:10.419047619: rms=-16.3 dB(15.3%) peak=-0.5 dB(97.7%) decay=-0.5 dB. Value count=20 Avg.rms=-23.8 dB(6.7%)
```

but it still does not initiate the recording.  I even tried a very short duration like 0.5s and it doesn't make a difference.  One other thing I noticed is that "absolute silence" on my motherboard is around -24 dB according to your program.

---

### Post by moma on 2011-03-02
Hello Mocha,
Can you provide more information. 
1) Download the latest version of the program (if you compiled it from source). There have been some minor changes.

2) Start the program from command line with --debug-signal=1 option. 
$ [COLOR="DarkGreen"]audio-recorder -d 1[/COLOR]

Activate the timer. Audio-recorder will now print signal levels in the terminal window.

3) Play this test signal.
[http://www.futuredesktop.com/tmp/test-sound.ogg](http://www.futuredesktop.com/tmp/test-sound.ogg)
(I generated it with [this...]("http://www.futuredesktop.com/tmp/test-sound.py") python script)

4) After the test-sound.ogg finishes, take copy of the outputted lines and paste them to Ubuntu's paste-bin, here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

And show the pastebin URL here so we can grab the data.

Notice:
```
Time: 0:01:10.419047619: [COLOR="Red"]rms=-16.3dB (15.3%)[/COLOR] peak=-0.5 dB(97.7%) decay=-0.5 dB. **Value count=20 **[COLOR="red"]Avg.rms=-23.8dB (6.7%)[/COLOR].
dB = decibel, and % is dB value converted to 0 - 100%.
```

Only the "rms=" and "Avg.rms=" values have meaning here. The other values (peak and decay) are not used or tested by the program, only printed.

The value_count runs from 0 to 50 (defined in [gst-listener.c]("http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/gst-listener.c") module). 50 values represent ca. 5 seconds of data.

Avg.rms = sum(rms values)/value count.

The timer simply calls **listener_get_average_rms(...)** to get the values. This functions is defined in gst-listener.c. See also timer_test_silence(...) in [timer.c]("http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/timer.c").

So the mechanism is very simple. It may need improvements.

---

### Post by mocha on 2011-03-03
I played with your program some more and now I understand a few things better.  First of all in order to do a line-in capture properly with your program, one needs to load the pulseaudio loopback module, otherwise your program appears to only sample once per second from the non-monitor source.  Secondly, it appears that your "silence" test can only go as low as 1 second, and it doesn't accept fractional input like 0.5s.  Another issue that causes me a few problems is that the silence test is based on the average rms value, which kind of screws up sound detection in my opinion.  For example, if I'm recording a line-in source that is intermittent, and if there is sound for a few seconds the average rms might go up to -17 dB, but then when the sound stops it takes awhile for that average value to drop down below the threshold, so the program just records silence for a few seconds, but the amount of "few seconds" is different every time depending on how long the last burst of audio was.  Also, the fact that you can't do less than 1 second threshold screws up sound detection in the opposite manner, meaning that very short bursts of audio are not detected and therefore nothing is recorded.

I really like your program, if you could fix these few things it would be much more useful.  I am trying to record intermittent audio coming over a line-in, which is probably not what you intended this program to originally be for.

These types of programs for Linux intrigue me because there is very few of them, whereas in the Windows world there are many; "scanner recorder", vox-record, rec-all pro, etc...  The only 2 things that I have found that work good on Linux for this is Audacity, a python script I found, and now your program is in the league but it needs a few tweaks first.  I will try playing with source later.

---

### Post by moma on 2011-03-04
Many thanks for your input. 

> The "silence" test can only go as low as 1 second, and it 
> doesn't accept fractional input like 0.5s. 

You are right. The timer_test_silence(...) function in timer.c counts whole seconds. Notice also that the Timer itself **sleeps 2** seconds between each call. See the TIMER_CALL_FREQ variable at the top of the timer.c module. Study also the timer_func_start() function which creates the timer thread.

> Another issue that causes me a few problems is that the 
> silence test is based on the average rms value, which kind 
> of screws up sound detection in my opinion.

That's right. It uses avg.rms value for all silence/sound/audio/voice tests.

This audio-recorder uses GStreamer, and its "level" element was the best way to get the signal-data. Ref.:
[http://www.gstreamer.net/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-level.html](http://www.gstreamer.net/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-level.html)
--

Do we agree that the RMS value is the best way to detect the signal level? I don't think we can use the Peak and Decay values for anything useful?

Based on your indication:
Maybe we should stop using avg.RMS, and collect RMS values directly. Like this

A) gst-listener.c collects RMS data for the last few seconds.
See gst-listener.c, function listener_set_data(...).

B) Timer wakes up each (1) second and reads the RMS data for the last (1) second from gst-listener.c.
See timer.c, function timer_test_silence(...).
And gst-listener.c, listener_get_average_rms(...).

Link to [timer.c module.]("http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/timer.c")

Link to [gst-listener.c module ]("http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/timer.c")

**I really need help to make this program better**.
[COLOR="Red"]Notice[/COLOR]: I'm a programmer and have relatively little knowledge about sound and audio systems. I simply made this app to record audio from radio and TV-broadcasts on the net. Audio-recorder uses GStreamer to do the listening and recording jobs.
---
EDIT: Be careful when you test the timer commands.
Test one (1) command at a time. For example, these two commands;
[COLOR="DimGray"]start if voice 1s -22dB
pause if silence 1s -22dB[/COLOR]
may cause a conflict (but I haven't tested it).

You only need the the first line.
[COLOR="DimGray"]start if voice 1s -22dB[/COLOR]
It will automatically **pause** temporarily when the signal drops under the given value.

---

### Post by sheedatali on 2011-03-04
I can't seem to record correctly with Skype. It records my Microphone input, however the remote side sound playing through my speakers does not get recorded. 

I have tried all possible combinations in Advanced settings for Playback Devices. What can I do to troubleshoot ?

---

### Post by moma on 2011-03-04
Hello Sheedatali,
**EDIT:** Yes, I can see your problem.
The Skype module ([dbus-skype.c]("http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/dbus-skype.c")) is pretty nice but I need to find a better way to melt the voice channels from microphone + loudspeaker to one recording. I need to review the entire Skype module. I may seek help from [GstMixer....]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-base-libs/html/gst-plugins-base-libs-gstmixer.html"). **Most likely I need to change the GStreamer-pipeline to include two separate audio sources**. Wish me luck. Many thanks for your observation.

**EDIT:** Ok, here is a GStreamer pipeline that combines two sound sources to one recording. 
It takes microphone input + sound from the speakers and records it all to test1.oga file.

Using the [GstInterleave...]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-plugin-interleave.html") element.
$ [COLOR="SeaGreen"]gst-launch interleave name=i ! level name=level ! "audio/x-raw-float,rate=44100,channels=2" ! \
vorbisenc name=enc quality=0.5 ! oggmux ! \
filesink name=output-sink location=test1.ogg  \
pulsesrc device=alsa_input.usb-Creative_Technology_Ltd._VF0610_Live__Cam_Socialize_HD_091214_b_00556-02-HD.analog-mono name=source1 !  \
queue name=q1 ! audioconvert ! i. \
pulsesrc device=alsa_output.pci-0000_04_02.0.analog-stereo.monitor name=source2 ! queue name=q2 ! audioconvert ! i.[/COLOR]

Notice: the device names in the above command are spesific for this machine and system.

It's also possible to add ! volume volume=0.3 ! fragment after the queue elements. This will control the volume (0.0 - 1.0).

Here is an other example, that records from 3 audio devices. Using the [GstAdder...]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-base-plugins/html/gst-plugins-base-plugins-adder.html") element.
$ [COLOR="SeaGreen"]gst-launch-0.10 adder name=mix ! audioconvert ! vorbisenc ! oggmux ! filesink location=test1.ogg { 
pulsesrc device=alsa_input.usb-Creative_Technology_Ltd._VF0610_Live__Cam_Socialize_HD_091214_b_00556-02-HD.analog-mono ! queue ! mix. 
} { pulsesrc device=alsa_output.pci-0000_04_02.0.analog-stereo.monitor ! queue ! mix. } 
{ pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor  ! queue ! mix. }[/COLOR]

@Sheedatali: Things looks very promising. The GUI will also need changes because, when recording from the Skype, the user must select both the sound-card device (loudspeaker) and microphone device.

---

### Post by mocha on 2011-03-05
Moma,

I downloaded  your source and want to look into this more since your program has the most promise to be the most refined voice activated recording program for Linux.

> A) gst-listener.c collects RMS data for the last few seconds.
See gst-listener.c, function listener_set_data(...).

B) Timer wakes up each (1) second and reads the RMS data for the last (1) second from gst-listener.c.
See timer.c, function timer_test_silence(...).
And gst-listener.c, listener_get_average_rms(...).

Yes I think it would be much better to use a fixed period to calculate the average, otherwise it takes too long for the average value to fall back below the threshold value, and you end up with varying amounts of recorded silence.

I want to use your program to record scanner radio broadcasts, like public safety radio stuff, police, fire, etc.  There is a lot of intermittent audio from these sources, so it is nice to do pausing on silence.  It is also nice to be able to program a fixed amount of silence after the last broadcast.  The sequence of events is like this:

1.  Wait for audio above threshold xx dB.
2.  Start recording.
3.  When instantaneous levels drop below threshold, record for xx seconds more.
4.  Stay paused until condition 1.

I also want to say that I appreciate your use of gstreamer, it is clearly the best choice because the savvy user can make their own pipelines for on the fly encoding decisions.  Audacity and the python script only record to WAV.

In the past I've also attempted to script sox with its silence command, but it never worked properly for realtime recording. 

Here's a [link to the python script]("https://github.com/MerlijnWajer/SNARP") I was talking about.

---

### Post by moma on 2011-03-13
Hello,
I have made some changes to the audio-recorder.

It's now possible to select one or more devices for recording. Take a look at this picture.
[[img]http://bildr.no/thumb/844348.jpeg[/img]](http://bildr.no/view/844348)

@Sheedatali: Recording from Skype should now work.

I haven't uploaded the new code to the Launchpad yet, but will do it during this coming week.

[COLOR="Red"]EDIT 15.march.2011[/COLOR]
Hello again,
I have now uploaded the code to Launchpad. 
Please update your source and recompile. I do not dare to create ready-made packages yet.
We need to test the source and all its functions first ;-)

[COLOR="Red"]EDIT 16.march.2011[/COLOR]
I just uploaded some more updates.
Please see also bug-reports and comments on 
[https://bugs.launchpad.net/audio-recorder](https://bugs.launchpad.net/audio-recorder)

[COLOR="Red"]EDIT 18.march.2011[/COLOR]
There are now packages for Maverick and Natty. Version 0.4 has been delivered.
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

[COLOR="Red"]EDIT 19.march.2011[/COLOR]
Only Natty needs libappindicator-dev package.
I removed libappindicator-dev package from Maverick. Changed build-dependencies in debian/control file.

---

### Post by Yozhik on 2011-10-18
Hi ... newbie here, but will weigh in with what I can. :)

My only need for audio recording on a consistent basis has been frequent Skype conversations, for which "Skype Call Recorder" was the 'application of choice'.

However, with the recent Ubuntu 11.10 upgrade, that piece of software has been rendered worthless. :(
Ergo audio-recorder has come in to the picture as a possible solution.

Strictly for the purposes of recording Skype voice chat, I find the current version of audio-recorder unsatisfactory, when compared to that which it is needed to replace; i.e. Skype Call Recorder. Let me be specific ... with SCR you were able to 'dumb down' the bitrate and sample rate so that the resultant mp3 was 'light'. Given that Skype calls are - for the most part - simply glorified telephone calls, 44.1kHz and 192kb are simply unnecessary. Not only is it overkill in terms of quality, but it also results in a file size that is excessive for its intended purpose. It also exceeds what VoIP is typically capable of.

8kHz to 16kHz is more than enough for sampling rate for the resultant mp3 for voice calls through VoIP.
Similarly, telephone typically has a bit rate of 8kbit/s. Even if using 16kbit/s or 32kbit/s ... its a heck of a stretch to justify needing 192!!

This is reflected in the Windows only software that is available specifically for Skype here:
[http://voipcallrecording.com/Skype_Call_Recorder](http://voipcallrecording.com/Skype_Call_Recorder) ... which is NOT the recorder I was using pre-Upgrade, but DOES have the 32kHz sampling option to better reflect the needs of voice call capturing.

Now ... consider the comparative resultant filesizes when holding up the "current audio-recorder mp3" versus the "required audio-recorder mp3".

For other applications - I can't comment or offer anything.
However, for Skype recordings, I think it is an admirable attempt, and a welcome solution, but for it to be meaningful [for my personal requirements], it requires some adjustments.

To put that into context, I am regularly involved [daily] in Skype 'think tanks' and discussion groups, which last from 45mins to 2hr30mins. The mp3 that is produced then needs to be promulgated to a wider group. The audio-recorder mp3 filesize is prohibitive.

Again - hope this feedback helps.
My requirements are very specific, but in terms of being a Skype recorder, maybe the comments about it being excessive in terms of recording quality may have some merit?

Cheers.

---

