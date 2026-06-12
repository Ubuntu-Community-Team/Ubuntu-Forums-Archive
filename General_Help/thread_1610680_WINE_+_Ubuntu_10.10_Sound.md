---
title: "WINE + Ubuntu 10.10 Sound"
date: 2010-11-01
forum: General Help
---

### Post by HiImTye on 2010-11-01
Ok, here's the issue: I am having sound issues while playing some games under WINE. for this I will use World of Warcraft as it has options for different sound engines. The problem is that I will have sound running fine for a while after a fresh reboot. It will seem fine for a good half hour to an hour and then suddenly it will stop. It will still be present in the applications list in sound preferences listed as 'ALSA plug-in [wine-preloader]'. muting/unmuting and adjusting the slider has no effects. Enabling and disabling sound in the game also has no effects. Here is what I have tried thus far to try to remedy it:


[LIST=1]
[*]tried all of the various sound options in winecfg (some simply don't produce any sound at all on a fresh reboot - OSS, for instance)
[*]tried with and without padsp
[*]tried the various sound engines in Config.wtf
[*]tried WINE from the Ubuntu repositories and the developer's PPA
[*]tried lowering the sample rate and the bits per sample in the audio tab of winecfg
[*]tried fiddling with the sound preferences applications controls
[/LIST]
I am not adventurous enough to try to install OSSv4 so that doesn't seem like an option for me. it is important to note that sounds not coming from WINE function as normal even while WINE is producing no sounds.

---

### Post by phreakincool on 2010-11-07
Have you tried removing/disabling pulse audio? That's what I did.

---

### Post by HiImTye on 2010-11-27
I tried switching to OSS but when I rebooted I had no sound at all (and it was a sunday night) so I gave in and switched back to pulseaudio

---

### Post by HiImTye on 2010-12-01
update: I tried using both (separately):

pasuspender
```
env <variables> pasuspender wine "Drive:\Path\File.exe"
```

and telling pulseaudio to stop running
```
pulseaudio -k
```

and more of the same

---

### Post by NCLI on 2010-12-01
This may be irrelevant, but have you opened the "Sound" section of "winecfg"? You usually have to look at it once to make Wine setup sound properly.

---

### Post by HiImTye on 2010-12-02
yeah and I use a different prefix for each program too so I can install only what I need for each program (and each program has a 'clean install' basically)

---

### Post by HiImTye on 2010-12-12
tried various versions of wine and they all have the same result

---

### Post by ubun2d00d on 2010-12-29
Hi there,
I got the same problems after upgrading from Lucid to Maverick. After the upgrade Spotify wouldn't play music and the audio test feature in wine config failed. After quite a bit of Googling I found this:

[http://georgia.ubuntuforums.org/showthread.php?t=1610170](http://georgia.ubuntuforums.org/showthread.php?t=1610170)

I went into wine config and set my settings to the following, as per the suggestion in the thread:

[LIST]
[*]Driver: ALSA only
[*]Hardware Acceleration: Emulation
[*]Sample Rate: 44100
[*]Bits per Sample: 16
[/LIST]
After i did that I logged out and back in again and, hey presto, problem solved! I know you said that you had already tried fiddling about with the audio settings in wine config so you might have already tried this, but I thought I might mention it anyway.

I am using wine 1.3. 
Hope this helps.

---

### Post by kipp195 on 2011-01-07
Thanks! :)
I had the same problem with spotify/wine as you described (after upgrading from lucid to maveric), and alsa/emulation/44100/16 worked perfectly, I didn't even have to log out and in. Also, now, using ALSA, the vol up/down special keys on my laptop affects the sound volume in Spotify (which it didn't earlier when it only worked with OSS).

---

### Post by ubun2d00d on 2011-01-08
Glad I could be of assistance! :D

---

### Post by HiImTye on 2011-01-23
I managed to fix it by installing OSS4 using this [guide]("http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html") (although I skipped some stuff and I chose to add OSS4 to pulseaudio, rather than removing pulseaudio)

here's what I did:

in a terminal, run
```
sudo dpkg-reconfigure linux-sound-base
```choose OSS

reboot

install oss4 from the repositories
```
 sudo apt-get install oss4-base oss4-dkms oss4-gtk
```oss4-source is not in the repos right now for some reason so I had to install it from the [ubuntu website]("https://launchpad.net/ubuntu/lucid/+package/oss4-source") (note: it's for lucid)

edit pulseaudio's config
```
gksu gedit /etc/pulse/default.pa
```search for and replace:
```
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
```with:
```
load-module module-oss device="/dev/dsp" sink_name=output source_name=input mmap=0
```I didn't comment out any modules like it says to in the guide

I already had this installed but if you don't then
```
sudo apt-get install gstreamer0.10-plugins-bad
```then run
```
gstreamer-properties
```under audio (the first tab it brings you to) choose for both input and output 'OSS - Open Sound System Version 4' for the plugin. I left the device for both the same ('Default')

create a new text file
```
gedit ~/.asoundrc
```paste this into it
```
pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }
```load winecfg
```
winecfg
```on the sound section put a check next to OSS and uncheck ALSA
repeat for all your prefixes (if you use them)
```
env=$HOME/.wine-WoW winecfg
``````
env=$HOME/.wine-Curse winecfg
```(yes, the curse client has its' own prefix so it can use internet exploder 7)

now my sound doesn't disappear

---

### Post by HiImTye on 2011-01-27
additional note: don't use the PPA suggested on that site, use ossxmix instead (it takes a bit to figure out but it also doesn't prevent you from getting updates)

if you did add the PPA, however, then purge it using this command:
```
sudo ppa-purge ppa:dtl131/ppa
```

---

### Post by Bluestars on 2011-04-23
> **HiImTye said:**
> I managed to fix it by installing OSS4 using this [guide]("http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html") (although I skipped some stuff and I chose to add OSS4 to pulseaudio, rather than removing pulseaudio)

here's what I did:

in a terminal, run
```
sudo dpkg-reconfigure linux-sound-base
```choose OSS

reboot

install oss4 from the repositories
```
 sudo apt-get install oss4-base oss4-dkms oss4-gtk
```oss4-source is not in the repos right now for some reason so I had to install it from the [ubuntu website]("https://launchpad.net/ubuntu/lucid/+package/oss4-source") (note: it's for lucid)

edit pulseaudio's config
```
gksu gedit /etc/pulse/default.pa
```search for and replace:
```
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
```with:
```
load-module module-oss device="/dev/dsp" sink_name=output source_name=input mmap=0
```I didn't comment out any modules like it says to in the guide

I already had this installed but if you don't then
```
sudo apt-get install gstreamer0.10-plugins-bad
```then run
```
gstreamer-properties
```under audio (the first tab it brings you to) choose for both input and output 'OSS - Open Sound System Version 4' for the plugin. I left the device for both the same ('Default')

create a new text file
```
gedit ~/.asoundrc
```paste this into it
```
pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }
```load winecfg
```
winecfg
```on the sound section put a check next to OSS and uncheck ALSA
repeat for all your prefixes (if you use them)
```
env=$HOME/.wine-WoW winecfg
``````
env=$HOME/.wine-Curse winecfg
```(yes, the curse client has its' own prefix so it can use internet exploder 7)

now my sound doesn't disappear


Idid all of this.  It did not work so I uninstalled OSS4,reinstalled pulseaudio and alsa (maybe im missing a package?) and rebooted.  When I reboot my sound works intially, but after a while of use the sound stops working.

How do I reverse this?

---

### Post by HiImTye on 2011-05-10
> **Bluestars said:**
> Idid all of this.  It did not work so I uninstalled OSS4,reinstalled pulseaudio and alsa (maybe im missing a package?) and rebooted.  When I reboot my sound works intially, but after a while of use the sound stops working.

How do I reverse this?
to reverse it, it is in the guide :)

[LIST=1]
[*]quickly, you want to reconfigure to ALSA```
sudo dpkg-reconfigure linux-sound-base
```
[*]rename the old config file```
mv ~/.asoundrc ~/.asoundrc_bak
```
[*]set GStreamer to use PulseAudio by default```
gstreamer-properties
```
[*]check gconf keys```
gconf-editor
```navigate to ' system/gstreamer/0.10/audio/default' - check if anything is set to osssink - if they are change them to pulsesink
[*]remove oss```
sudo apt-get remove oss-linux
```
[/LIST]
If you have any other questions dont be afraid to ask

---

### Post by HiImTye on 2011-05-10
for anyone interested I have OSS4.2 working with PulseAudio in 11.04 using the OSS4 binary from the OpenSound website. this is what I did:


[LIST=1]
[*]download OSS4 from the [website]("http://www.opensound.com/download.cgi"). take note of where you save it to.
[*]restart and at the login screen choose your username and at the bottom choose 'recovery console' (if you have Ubuntu set to log you in automagically then after restarting, log out)
[*]a command line interface will appear. in this, change to the folder you have it in (if you saved it to Downloads then it will be in '/home/<your username>/Downloads')```
cd /path/to/file
```
[*]install the binary```
dpkg -i oss-<tab>
```
[*]reconfigure to OSS```
sudo dpkg-reconfigure linux-sound-base
```choose OSS
[*]type 'exit' and restart. when you log in make sure it says 'Ubuntu' rather than 'recovery console'
[*]edit pulseaudio's config```
gksu gedit /etc/pulse/default.pa
```uncomment this line:```
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
```
[*]and add mmap=0 at the end
[*]if you don't have the bad gstreamer plugins then install them```
sudo apt-get install gstreamer0.10-plugins-bad
```
[*]configure gstreamer```
gstreamer-properties
```choose OSS4 for both (I'm not typing out the long names)
[*]create your asoundrc```
gedit ~/.asoundrc
```paste this into it:```
pcm.!default 
{
  type oss
  device /dev/dsp
 }
mixer.!default
 {
  type oss
  device /dev/dsp
}
```
[*]set up your various wine configs
[*]I use a mic for Mangler/Skype so I had to set it up in ossxmix, if you use one you will likely want to do this also
[/LIST]
edit: applications that use GStreamer over OSS4 will respect the gnome volume control. programs that use OSS4 rather than PA will not (for instance: flash). I haven't figured this one out yet but it has its' advantages. I can set Rhythmbox's volume with my audio controls on my keyboard while setting WINE programs seperately. the disadvantage is that sometimes that isn't what you want

---

