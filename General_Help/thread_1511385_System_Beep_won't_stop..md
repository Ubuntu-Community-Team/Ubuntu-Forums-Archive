---
title: "System Beep won't stop."
date: 2010-06-16
forum: General Help
---

### Post by Dex73 on 2010-06-16
I have a HP Laptop with Ubuntu Hardy installed.

The system beep makes rapid clicking sound at login window that slowly dissipate and clicking that, so far I can only fix by rebooting, when I play music, reboot after hibernating, and when waking up from suspend. 

I've turned the system beep off in System/Preferences/Sound but it doesn't do anything.

Any ideas?

---

### Post by bondo101 on 2010-06-16
Check your sound card drivers , It sounds like you have two files some how got screw up Usually laptops don't beep when posting and some desktops don't either. usually a single continious beep means mobo going bad. Try deleating the sound drivers.Try to remember what you did before this happend and trace it forwards.Laptops are freakey when it comes to Ubuntu.
I know my vaio won't load ubuntu unless i clear off the drive.
 Just trying to help.

---

### Post by Dex73 on 2010-06-16
I'm barely above a noob. I found some sound driver files but I really don't know what I'm looking at. Is there a list of specific drivers your talking about? I don't want to mess up my computer.

I'm also not sure what you mean by "continuous" beep. Just making sure my first post was clear, it sounds kind of like a clock that's ticking really fast.

The started as soon as Installed Hardy. I've tried Intrepid and Lucid. Intrepid wouldn't play any audio files and I've downloaded Lucid from two different severs, then burnt them to two CDs, they both gave an error message. And they did the same thing to another laptop of mine which is running great with Hardy, so my copy must be fine (also passes the check option when it loads up).

I really want to fix the other(newer) one. Maybe even try Lucid on my old one.

---

### Post by lidex on 2010-06-16
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by wojox on 2010-06-16
Have you blacklisted it?

```
gksudo gedit /etc/modprobe.d/blacklist
```

Then add **blacklist pcspkr** to the end of the file and reboot.

---

### Post by Dex73 on 2010-06-17
uname -a
Linux one-laptop 2.6.24-28-generic #1 SMP Thu May 27 00:16:49 UTC 2010 i686 GNU/Linux


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


dpkg -l | grep "alsa"
ii  alsa-base                                  1.0.16-0ubuntu4                                      ALSA driver configuration files
ii  alsa-oss                                   1.0.15-1                                             ALSA wrapper for OSS applications
ii  alsa-utils                                 1.0.15-3ubuntu2                                      ALSA utilities
ii  gnome-alsamixer                            0.9.7~cvs.20060916.ds.1-1                            ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                         0.10.18-3                                            GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.38-0ubuntu9                                      Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-1.10.10-plugins-alsa                 1.10.10-1ubuntu6                                     Portable Windows Library Audio Plugin for th
ii  libsdl1.2debian-alsa                       1.2.13-1ubuntu1                                      Simple DirectMedia Layer (with X11 and ALSA 


head -n l /proc/asound/card*/codec#*
head: l: invalid number of lines

I'll try the blacklist idea when I have time later. Thanks for the help.

---

### Post by lidex on 2010-06-17
> **Dex73 said:**
> uname -a
Linux one-laptop 2.6.24-28-generic #1 SMP Thu May 27 00:16:49 UTC 2010 i686 GNU/Linux


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


dpkg -l | grep "alsa"
ii  alsa-base                                  1.0.16-0ubuntu4                                      ALSA driver configuration files
ii  alsa-oss                                   1.0.15-1                                             ALSA wrapper for OSS applications
ii  alsa-utils                                 1.0.15-3ubuntu2                                      ALSA utilities
ii  gnome-alsamixer                            0.9.7~cvs.20060916.ds.1-1                            ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                         0.10.18-3                                            GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.38-0ubuntu9                                      Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-1.10.10-plugins-alsa                 1.10.10-1ubuntu6                                     Portable Windows Library Audio Plugin for th
ii  libsdl1.2debian-alsa                       1.2.13-1ubuntu1                                      Simple DirectMedia Layer (with X11 and ALSA 


head -n l /proc/asound/card*/codec#*
head: l: invalid number of lines

I'll try the blacklist idea when I have time later. Thanks for the help.

That command should have the digit 1, not letter l. Try it again - just copy-and-paste:
```
head -n 1 /proc/asound/card*/codec#*
```

You could probably do with an alsa upgrade. Follow the alsa-upgrade link in my sig.

---

### Post by undrline on 2010-06-17
HP indicates hardware issues with repetitive beeps.  Depending on the model and the number/style of beep, it could be telling you different things.  In my case, my RAM wasn't seated correctly and I was getting five beeps over and over.  Take a look at the HP beep code lists and see if that helps before you start doing things like editing system files to disable your onboard speaker:

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=bph07107](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=bph07107)

---

### Post by Dex73 on 2010-06-17
head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9250

==> /proc/asound/card0/codec#1 <==
Codec: Motorola Si3054


I checked out the HP website link and it goes over what the beeps are supposed to mean but none of it matches what this computer is doing. Good idea though. I'm trying to fix this write instead of just finding a way to disable my system beep. Hopefully that's not my only choice.

---

### Post by lidex on 2010-06-17
What's your laptop model?

---

### Post by Dex73 on 2010-06-17
The model is HP Pavilion dv4-1465dx

---

### Post by lidex on 2010-06-17
You could probably do with an alsa upgrade. Follow the alsa-upgrade link in my sig.

[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio")
[http://www.linlap.com/wiki/hp+pavilion+dv4-1100]("http://www.linlap.com/wiki/hp+pavilion+dv4-1100")
[http://www.linlap.com/wiki/hp+pavilion+dv4t]("http://www.linlap.com/wiki/hp+pavilion+dv4t")

---

### Post by Dex73 on 2010-06-18
> **lidex said:**
> You could probably do with an alsa upgrade. Follow the alsa-upgrade link in my sig.

[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio")
[http://www.linlap.com/wiki/hp+pavilion+dv4-1100]("http://www.linlap.com/wiki/hp+pavilion+dv4-1100")
[http://www.linlap.com/wiki/hp+pavilion+dv4t]("http://www.linlap.com/wiki/hp+pavilion+dv4t")

This worked to stop the rapid beeps at login, and waking up from suspend and hibernate. Loads better!

Still beeps when I try to play any audio though. Just beeps rapidly and then stops if I stop playing the file. Also different files play different tones.? Also says "No volume control GStreamer plugins and/or devices found" when I click on the volume control icon, which now has a do not symbol over it. No warnings or messages at all when playing files though.

---

### Post by lidex on 2010-06-18
Try this to make sure gstreamer packages are in place.
```
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

---

### Post by Dex73 on 2010-06-18
> **lidex said:**
> Try this to make sure gstreamer packages are in place.
```
sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Package gnash is not installed, so not removed 
Package gnash-common is not installed, so not removed 
Package icedtea-gcjwebplugin is not installed, so not removed 
Package libflash-mozplugin is not installed, so not removed 
Package libflashsupport is not installed, so not removed 
Package mozilla-plugin-gnash is not installed, so not removed 
Package openjdk-6-jre is not installed, so not removed 
Package openjdk-6-jre-headless is not installed, so not removed 
Package openjdk-6-jre-lib is not installed, so not removed 
Package swfdec-mozilla is not installed, so not removed 
The following packages were automatically installed and are no longer required: 
  libdns35 linux-headers-2.6.24-23-generic linux-headers-2.6.24-23 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
gstreamer0.10-ffmpeg is already the newest version. 
gstreamer0.10-plugins-bad is already the newest version. 
gstreamer0.10-plugins-bad set to manually installed. 
gstreamer0.10-plugins-ugly is already the newest version. 
gstreamer0.10-plugins-ugly-multiverse is already the newest version. 
gstreamer0.10-pitfdll is already the newest version. 
liblame0 is already the newest version. 
liblame0 set to manually installed. 
E: Couldn't find package non-free-codecs 

Also, I tried to play another music file after I ran this and the file still doesn't play but there is no beeping!!! :)  The do not symbol is still over the volume control.

---

### Post by Dex73 on 2010-06-18
I just ran alsamixer in the command line to see if I could adjust the sound settings at all and it kicked back "function snd_ctl_open failed for default: No such file or directory"

---

### Post by lidex on 2010-06-19
Can we see this again please:
```

aplay -l
dpkg -l | grep "alsa"

```

And try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot.

---

### Post by Dex73 on 2010-06-20
aplay -l 
aplay: device_list:205: no soundcards found...

dpkg -l | grep "alsa" 
ii  alsa-base                                  1.0.16-0ubuntu4                                      ALSA driver configuration files 
ii  alsa-utils                                 1.0.15-3ubuntu2                                      ALSA utilities 
ii  gstreamer0.10-alsa                         0.10.18-3                                            GStreamer plugin for ALSA 
ii  libesd-alsa0                               0.2.38-0ubuntu9                                      Enlightened Sound Daemon (ALSA) - Shared lib 
ii  libpt-1.10.10-plugins-alsa                 1.10.10-1ubuntu6                                     Portable Windows Library Audio Plugin for th 
ii  libsdl1.2debian-alsa                       1.2.13-1ubuntu1                                      Simple DirectMedia Layer (with X11 and ALSA 

After reboot the do not symbol remains and so does the error message. The music player came up and the slider and time left indicate that it's playing. No sound though.

---

### Post by Dex73 on 2010-06-20
Just tried to play a video with VLC and the first time the screen went black and the second time it started to look mosaic. Both times I had to shut down hard to unlock the computer.

---

### Post by lidex on 2010-06-21
Try upgrading your alsa install - it's ancient. Follow the alsa-upgrade link in my sig.

---

### Post by Dex73 on 2010-06-24
> **lidex said:**
> Try upgrading your alsa install - it's ancient. Follow the alsa-upgrade link in my sig.

Sorry this took so long. I've been busy.
I got to the second step and... 

$ tar xvf AlsaUpgrade-1.0.23-2.tar 
tar: AlsaUpgrade-1.0.23-2.tar: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now

---

### Post by bondo101 on 2010-06-25
Try retyping the code again. Make sure its exact or cut and paste it if ya can. How old is the laptop ? Mabey try a different version of ubuntu mabey 7.04 or 8.04. . And did the beep occur when windows was on the machine?
                 just trying to help . bondo101

---

### Post by lidex on 2010-06-25
> **Dex73 said:**
> Sorry this took so long. I've been busy.
I got to the second step and... 

$ tar xvf AlsaUpgrade-1.0.23-2.tar 
tar: AlsaUpgrade-1.0.23-2.tar: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now

Make sure you cd into the directory into which you downloaded the file. Default download location would be:
```
cd ~/Downloads
```
Once in that directory, double-check that it's there with this command:
```
ls
```
That lists the folder contents.

---

### Post by Dex73 on 2010-06-25
I'm in the right spot.
$ ls
aeskulap_0.2.1-2_i386.deb
alsa-driver-1.0.23
alsa-driver-1.0.23.tar.bz2
install_flash_player_10_linux.deb
picasa_3.0-current_i386.deb
skype-debian_2.1.0.81-1_i386.deb
youtube-dl_2007.08.24-1~hyperair1_all.download

I've copied and pasted it directly from the ALSA upgrade script.
I don't know what it did when windows was on it. I've had bad enough experiences with Vista that I didn't even give it a chance.

The command is "tar xvf AlsaUpgrade-1.0.23-2.tar". What does the -2 mean? Am I using the wrong script?

---

### Post by lidex on 2010-06-25
This download:
[http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001]("http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001")

---

### Post by Dex73 on 2010-06-26
Same place, same message. I downloaded it by clicking on the link you provided.

$ ls
aeskulap_0.2.1-2_i386.deb
alsa-driver-1.0.23.tar.bz2
install_flash_player_10_linux.deb
picasa_3.0-current_i386.deb
skype-debian_2.1.0.81-1_i386.deb
youtube-dl_2007.08.24-1~hyperair1_all.download

$ tar xvf AlsaUpgrade-1.0.23-2.tar
tar: AlsaUpgrade-1.0.23-2.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by lidex on 2010-06-26
You're doing something wrong. Yeah, it's you....:rolleyes:
Try this:
```
sudo updatedb
```
Now this:
```
locate AlsaUpgrade-1.0.23-2.tar
```

---

### Post by Dex73 on 2010-06-26
I didn't mean you gave me a bad link, just telling you where I got it.

"sudo ./AlsaUpgrade-1.0.23-2.sh -c"  gave me this at the end...
91: error: implicit declaration of function &#8216;hrtimer_forward_now&#8217;
make[3]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/drivers/dummy.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/drivers] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.23/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-28-generic'
make: *** [compile] Error 2

***************************************************************************
*  alsa-driver-1.0.23 make failed

---

### Post by Dex73 on 2010-10-03
I've fixed it by installing 10.04. Thanks for all the help though.

---

