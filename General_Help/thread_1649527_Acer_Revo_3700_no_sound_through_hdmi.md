---
title: "Acer Revo 3700 no sound through hdmi"
date: 2010-12-20
forum: General Help
---

### Post by UptownRiot on 2010-12-20
I've just installed ubuntu 11.04 on my recently purchased acer aspire  revo 3700. After completing the initial install of ubuntu, running all  available critical and recommended updates, and installing and  activating the 3rd party driver for the nvidia card I'm having trouble. I  am getting good video through the hdmi cable to my sony bravia 32" tv,  but no sound (sound works fine in regular tv or xbox use). 

I'm relatively inexperienced with linux so I'm not entirely sure what  information would be relevant and helpful to assisting me with  deciphering this issue, but I will do my best. 

I've found no proprietary driver for sound through the nvidia ion  processor, only one for the graphics arm. I would assume they are  sharing a driver, but as its not stated I cannot be sure. The  'additional drivers' control panel calls it the 'NVIDIA accelerated  graphics driver (version current)' The chip is the nvidia GT218-ION.

Settings in sound preferences are high definition audio controller  digital stereo (hdmi) selected for output.

results from aplay are:

UR@UR-Acer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1  Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1  Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Through searching and reading forum posts here and elsewhere i've tried editing a few files but none have had any amount of success, i  haven't changed them back as of yet:

1) gksudo gedit /etc/modprobe.d/sound.conf

then added the following to what was a blank file

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

2) sudo nano ~/.asoundrc

and added to what was also a blank file

defaults.pcm.device 3


Ultimately nothing so far has worked. I'm not getting any sound from any  application or the sound tests in the preferences hardware tab. If  there is any other information I can provide that would help I will  provide it. 

Any thoughts on what could be causing this strange issue?

---

### Post by UptownRiot on 2010-12-20
I've also tested in all the multimedia applications. Video files, and just mp3 files. Still no sound.

---

### Post by UptownRiot on 2010-12-20
I've also removed and reinstalled alsa-utils. Currently installed version is 1.0.23-2ubuntu3.4

I tested the front headphone jack and got no sound there either. I did switch the setting back to analog for the headphone test. No joy.

---

### Post by UptownRiot on 2010-12-22
Still have no luck. Any ideas?

---

### Post by philneko on 2010-12-22
Sorry i dont have a answer, as i am in the same boat as you with the 3700 . Hopefully someone can shed some light on this issue

---

### Post by UptownRiot on 2010-12-22
Have you tried anything that I haven't tried, or have anything to add to your situation that might help zero in on the problem?

---

### Post by philneko on 2010-12-22
Not really mate, i only got my 3700 few hrs ago,

I have dhama 10 installed to hdd via live disc, it seems that this is already running the latest alsa 1.0.23 (as when i went to upgrade it asked if i wanted to upgrade 1.0.23 to 1.0.23)

I have checked the mixer for muted channels etc

And have tried a few things out of [http://forum.xbmc.org/showthread.php?t=84723](http://forum.xbmc.org/showthread.php?t=84723)

There are quite a few threads on forum.xbmc.org but it seems that all different things are working for different people, not just one straight fix

---

### Post by timgood on 2010-12-22
> **philneko said:**
> Not really mate, i only got my 3700 few hrs ago,

I have dhama 10 installed to hdd via live disc, it seems that this is already running the latest alsa 1.0.23 (as when i went to upgrade it asked if i wanted to upgrade 1.0.23 to 1.0.23)

I have checked the mixer for muted channels etc

And have tried a few things out of [http://forum.xbmc.org/showthread.php?t=84723](http://forum.xbmc.org/showthread.php?t=84723)

There are quite a few threads on forum.xbmc.org but it seems that all different things are working for different people, not just one straight fix

I have the 3700 with XBMC Dharma installed. If you go to the sound settings in XBMC, you can set the sound to HDMI and it works fine.

---

### Post by philneko on 2010-12-22
Thanks for the reply, unfortunately im having no luck with the settings via xbmc audio

I have tried:
Audio output: HDMI
Audio output device: hdmi
Passthrough output device: hdmi

then all the variations


including on advice in another thread
Audio output device: plughw:1,7 (and also plug:dmixer)
Passthrough output device: plughw:1,7

But still nothing, it seems strange that for a few people this issue occurs

---

### Post by UptownRiot on 2010-12-22
> **timgood said:**
> I have the 3700 with XBMC Dharma installed. If you go to the sound settings in XBMC, you can set the sound to HDMI and it works fine.

I have tried this, but my problem clearly goes much deeper as I am not getting sound anywhere at all. XBMC, which is installed, is not part of the problem. No application at all is getting sound, and even as far as using the sound test. I want to say it is a driver issue, but given my unfamiliarity with Linux I can't put my finger on it.

---

### Post by philneko on 2010-12-22
Yes it seems a bit harder to pin point because this is running linux which most are not to familiar with.

I am hoping to find a fix for this as i do not really want to have to change to win7...

If anyone is up with commands i am unable to edit a file to check:

[INDENT] gksudo gedit /etc/modprobe.d/sound.conf 
-bash: gksudo: command not found

[/INDENT]Anyone seen this problem?

Thanks guys

---

### Post by UptownRiot on 2010-12-22
I doubt that will solve your problem. As you can see up in my OP I tried that edit already and found no joy.

---

### Post by UptownRiot on 2010-12-22
Removing and reinstalling the nvidia driver doesn't help either.

---

### Post by axept on 2010-12-22
Try this:

Go to terminal

run: alsamixer

Go to the right and try un-mute/mute S/PDIF (You must set the output sound device to HDMI first, and play a song in a player). Maybe one must be muted and two un-muted or something, just try. IF you get sound, exit alsamixer (Esc) then run:

sudo alsactl store

---

### Post by UptownRiot on 2010-12-22
I'm there but i don't know how to mute/unmute. It's not giving me any options to make changes, or at least so it appears to me.

I figured out how to mute/unmute and tried every variation but there was no change.

---

### Post by axept on 2010-12-23
> **UptownRiot said:**
> I'm there but i don't know how to mute/unmute. It's not giving me any options to make changes, or at least so it appears to me.

I figured out how to mute/unmute and tried every variation but there was no change.

Okay.. 

Hopes it works out for you!

---

### Post by philneko on 2010-12-23
hey riot,

possibly check this new thread?

[http://forum.xbmc.org/showthread.php?t=88369&highlight=revo+3700](http://forum.xbmc.org/showthread.php?t=88369&highlight=revo+3700)

I have swapped to win7 for the time being and it works fine =(

---

### Post by UptownRiot on 2010-12-23
Ok, I tried the following:

sudo wget [http://pastebin.com/download.php?i=ApvUwtUX](http://pastebin.com/download.php?i=ApvUwtUX) -O /etc/asound.conf

sudo wget [http://pastebin.com/download.php?i=f2e38265](http://pastebin.com/download.php?i=f2e38265) -O /usr/share/alsa/cards/HDA-Intel.conf

And that had no effect. Still no sound what-so-ever. Anyone else have any ideas?

---

### Post by UptownRiot on 2010-12-27
Still no luck. Anyone have any more ideas?

---

### Post by philneko on 2011-01-06
riot i think in that thread on xbmc.org i linked to, a dev or someone is asking for clean install then a log so they can have a look at the issue

you could possibly try posting a log up

---

### Post by UptownRiot on 2011-01-06
I've started the RMA process. I'm just having the thing replaced and hoping it was a hardware issue.

---

### Post by lidex on 2011-01-07
Look here:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by UptownRiot on 2011-01-07
@lidex wow, I'm not sure how that thread never came up in my searches. Thanks for pointing it out! I will give the solutions a try when I get home tonight and report back.

---

### Post by UptownRiot on 2011-01-08
@lidex Ok, i have a few issues. The first, those solutions say they are for 10.04 and not 11.04 which is what I am using. The second is that [post #8]("http://ubuntuforums.org/showpost.php?p=9732345&postcount=8") which is referenced starts off ok, but then quickly becomes difficult for a relative beginner to follow what they are intending for me to do. The '[See this first]("http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7")' link at the very top is way over my head. I read the post but was completely unsure of what they want us to be doing.

---

### Post by lidex on 2011-01-09
I just realized something here. I guess i missed it coming in at the back end of the thread.
You're using natty? You know this is alpha software, right? If you need to post for help you
need to do it in the development forum:
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

### Post by tjones00 on 2011-01-09
I'll try to chime in here as well instead of relay through pms.

I'm not exactly sure whats going on in 11.04 atm but unless you absolutely require it for some reason I'd really recommend sticking with 10.04 or 10.10. 

They're always messing with pulseaudio and kms not to mention the Unity desktop that will be rolled out standard with 11.04. (required 3d support doesn't sound good to me at least)

As to steps setting up hdmi on a gt218 (ion2) it boils down to this.

1) make sure you're using alsa 1.0.23 provided from ubuntu resources (kernel or module update) to avoid any kernel conflicts or missing module updates/patches. This requires a 2.6.35+ kernel (standard in 10.10) or an alsa upgrade through an ubuntu backport.

To check your kernel version type the following in a terminal:
```

uname -r
```To check your alsa version (1.0.23 should be built into a 2.6.35+ kernel)

```
cat /proc/asound/version
```2) discover which of the 4 devices on the nvidia card is responsible for hdmi audio (the eld information)

3) setup alsa and pulseaudio to use that device. Or as documented in the nvidia post a proper probemask should correct alsa, pulseaudio might still require an hdmi sink modification.

Edit: updated the original ion2 sound post added the nvidia probemask options and tried to make it easier to understand with "sections"

---

### Post by UptownRiot on 2011-01-09
> **lidex said:**
> You're using natty? You know this is alpha software, right? 

I definitely did not realize that was in its alpha stage. The nettop I put this on doesn't have a cdrom drive. So, I created a bootable usb stick with UNetbootin to install Ubuntu. It must have grabbed the wrong version somehow. I will reinstall with 10.10 today and see if that helps. 

If I run into trouble after reinstalling the proper version I will run back through the previously mentions steps.

---

### Post by forbzie22 on 2011-01-09
@uptownriot - Did you manage to resolve your issues with sound via HDMI ?

Am also thinking of getting a 3700 but am hearing lots of people having same issue as you.

Apparently if you buy an optical cable (toslink) and use SPDIF output it will work. You just have to invest in the optical cable which is annoying.

Think i might get the revo 3610 instead.

Def issue with the ION 2 from nvidia.

---

### Post by UptownRiot on 2011-01-09
@forbzie22 I haven't yet resolved it. At work currently so I haven't been able to try installing 10.10 yet. I didn't get a chance to test sound when windows 7 was installed as for some reason win7 couldn't display properly via the hdmi. The picture was too distorted to try anything, which led me to installing Ubuntu. I'll update this thread once I've had a chance to install 10.10 and see if that works.

---

### Post by forbzie22 on 2011-01-09
Have you tried using 10.04 as thats the long term support release.

Ill prob get the 3610 as buying it this week.

this is from xbmc forums

"
I have just sorted mine, it took 2 nights of work due to me being a linux noob but now it's working like a dream with Ubuntu 10.04.

I had to install alsa 1.0.23: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

Then I had to unmute the channels in alsamixer, once I had done this I had to add some options to the following file:

gksudo gedit /etc/modprobe.d/sound.conf

then add this line

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

Don't forget to change your hardware to Digital HDMI out in the sound options window (found in: system>preferences>sound)

---

### Post by UptownRiot on 2011-01-10
> **tjones00 said:**
> 2) discover which of the 4 devices on the nvidia card is responsible for hdmi audio (the eld information)

3) setup alsa and pulseaudio to use that device. Or as documented in the nvidia post a proper probemask should correct alsa, pulseaudio might still require an hdmi sink modification.

Edit: updated the original ion2 sound post added the nvidia probemask options and tried to make it easier to understand with "sections"

Ok, good news and bad news. Good news after dealing with several hurdles I got 10.10 x64 installed. I now get sound from the headphone jack. I am still not getting any sound from the HDMI.

I verified that I have the correct kernel and alsa versions.

I checked the eld info and I have none for any of those devices as you indicated. I tested 1.0, 2.0, 3.0, and 4.0. I'm not sure if there were other number combinations that I should have tested though. I had no eld info for any of the 4 I checked. I'm not sure how, or if, I should go about creating it? Which obviously prevents me from setting up alsa and pulseaudio to use it. 

I'm not sure what a probemask is and if thats the solution to not having any eld info. This link which I think is whats supposed to tell me how to create a probemask is difficult for me to understand what I'm meant to do.

However, there is progress being made, and its proven that its not a hardware problem so I've cancelled the RMA. Hopefully with a little more guidance I'll have this thing ironed out!

---

### Post by tjones00 on 2011-01-11
What do you mean you tested 1.0, 2.0, 3.0, 4.0? Eld data is kept in the following files for card 1 /proc/asound/card1/eld#0.0 eld#1.0 eld#2.0 eld#3.0

You would check it in the following way.

cd /proc/asound/card1/
cat eld#0.0
cat eld#1.0
cat eld#2.0
cat eld#3.0

There are now examples of what a positive and negative hit for eld data looks like.

If you find the thread confusing just take your time and try to understand what each step is doing. 

Ignore any probemask for now even the guys at Nvidia said those ones on the xmbc link didn't make sense. None of them worked for me when I was setting up my ion2. If you use any probemask try the offical nvidia suggestions.


Post the output from ```
cat /proc/asound/card1/eld*
```Edit:

Some additional details to help clear things up. Eld stands for "EDID Like Data". EDID is the information that your display sends your video card upon probe that lists the specific technicals of the display. What resolutions/modes etc it supports. Within the EDID there are also audio specifications for the display. How many channels what frequencies what format of audio it can handle etc. Without viable eld information you will not get ANY audio over a nvidia hdmi connection no matter how many things you update/reconfigure/unmute.

This is why it's very important to establish you have eld data and on which device before you can continue setting up audio. If there is no eld data you have to muck with either the kernel or alsa until there is. snd_hda_intel the alsa module responsible for nvidia hdmi audio requires eld data to work via hdmi.

Until this past summer you had to upgrade to a properly patched alsa 1.0.23 or 2.6.35+ kernel for the nvidia card to be recognized and to correct a faulty pin sense issue. The proper alsa 1.0.23 patches in the 2.6.35+ kernel were official as of this past summer. The "current" issue is that udev (or some other hardware probe/setup service) and pulseaudio still believe that nvidia hdmi interfaces only have 1 possible audio device (default NVidia,3). eg hw:1,3. Typically with an ion2 defined as card 1 hw:1,7 or 1,9 is the hdmi audio device not 1,3. ****to correct this Nvidia suggested using a probemask (the nvidia link in that thread) BUT it is not required you can still set it up without a probemask.

Setting up an ion2 today merely involves discovering which device is responsible for audio (eld query and audio confirmation) then setting it up properly since all the automagic configuration stuff is still borked.

---

### Post by UptownRiot on 2011-01-11
doublepost

---

### Post by UptownRiot on 2011-01-11
Ok, when i did the intial eld check, I got what you listed as a 'bad result' for all 4 options. That is 0.0, 1.0, 2.0, and 3.0. However, I had not yet activated the proprietary nvidia driver. After I did that I now get eld data on 1.0:

xbmc@xbmc-xbmc:/proc/asound/card1$ cat eld#1.0
monitor_present        1
eld_valid        1
monitor_name        SONY TV
    
connection_type        HDMI
eld_version        [0x2] CEA-861D or below
edid_version        [0x3] CEA-861-B, C or D
manufacture_id        0xd94d
product_id        0x4201
port_id            0x10000
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x1] FL/FR
sad_count        2
sad0_coding_type    [0x1] LPCM
sad0_channels        2
sad0_rates        [0xe0] 44100 48000 88200
sad0_bits        [0xe0000] 16 20 24
sad1_coding_type    [0x2] AC-3
sad1_channels        6
sad1_rates        [0xe0] 44100 48000 88200
sad1_max_bitrate    640000

---

### Post by tjones00 on 2011-01-11
So the device you want to test is hw:1,7 plughw:1,7 with aplay. eld#1.0 corresponds to device 7.

card 1 device 7

---

### Post by UptownRiot on 2011-01-11
Ok, so I got no sound from the test, but perhaps I didn't do it right. There were no .wav files in /usr/share/sounds/alsa/ so I had to download one.

xbmc@xbmc-xbmc:~$ aplay -Dplughw:1,7 /home/xbmc/Downloads/j.wav
Playing WAVE '/home/xbmc/Downloads/j.wav' : Unsigned 8 bit, Rate 11025 Hz, Mono
xbmc@xbmc-xbmc:~$ aplay -Dhw:1,7 /home/xbmc/Downloads/j.wav
Playing WAVE '/home/xbmc/Downloads/j.wav' : Unsigned 8 bit, Rate 11025 Hz, Mono
aplay: set_params:1053: Sample format non available
Available formats:
- S16_LE
- S32_LE
xbmc@xbmc-xbmc:~$ aplay -Dhdmi:NVidia /home/xbmc/Downloads/j.wav
aplay: main:654: audio open error: Device or resource busy

After none of those did I hear any sound.

---

### Post by tjones00 on 2011-01-11
Thats odd.

/usr/share/sounds/alsa/*.wav is part of the default alsa install.

This might sound odd but do you have alsa-utils installed?

sudo apt-get install alsa-utils

check /usr/share/sounds/alsa again after that.

As to no sound did you confirm that 1,7 is not muted in alsamixer?

MM denotes muted 00 denotes unmuted.

follow up:

Is the x server running?

I've noticed from your last post that the user and computer name is xbmc. Is this an xbmc stand alone system with no desktop environment?

If so launch xbmc and go to the audio section type in a custom digital passthru and device as plughw:1,7 now test audio from within xbmc itself.

If this is a stand alone xbmc system w/o a desktop/pulseaudio etc that is all that should be required. You do not have to mess with .asoundrc/asound.conf or pulse audio hdmi sinks or probemasks etc.

Edit: it should be noted that j.wav file you were trying is no good look at the rate and format (bit) vs your eld information. They're incompatible. Try to find a file that offers 48000 as a rate or try specifying the rate at 48000 in aplay with the -r 48000 option I believe.

[http://linux.die.net/man/1/aplay](http://linux.die.net/man/1/aplay) <--using aplay options.

---

### Post by UptownRiot on 2011-01-11
Ok, I checked alsa mixer and all 4 are unmuted under the HDA NVidia card. That is not the first card that shows up however. I have to switch to that from Intel by hitting F6 and then selecting it from the menu. Does that sound right?

Under the intel card 'S/PDIF' and 'S/PDIF Def' are both unmuted. Does that matter? Someone earlier in the thread thought it might.

I tried to install alsa-utils and it said 'alsa-utils is already the newest version.'

I think I know what you're referring to in the last part, but I'm not sure. This is a full install of Ubuntu 10.10. I'm launching a terminal from the accessories menu. I named the user and machine xbmc because thats all i intend to use it for once its finally working. XBMC isn't even installed on the machine yet. Given that the sound is not working I thought it would be a waste of efforts to bother installing and configuring it before I knew the machine would work.

Edit:

I figured out the reason for the missing .wav files. I was looking in /usr/share/alsa and not /usr/share/SOUNDS/alsa. That's my mistake. However, i'm still not getting sound from the TV though. :(

---

### Post by tjones00 on 2011-01-11
Now the issue is most likely pulseaudio control/use of alsa in your desktop environment.

type the following in a terminal

pactl list | less

if you see that pulse audio is still trying to route hdmi to 1,3 make the asound.conf and default.pa edits listed in the original thread.

---

### Post by UptownRiot on 2011-01-11
Ok, I found the default.pa and i just changed what was '#load-module module-alsa-sink' to 'load-module module-alsa-sink device=hw:1,9'

However, I thought I'd found the asound.conf file, but that wasn't it. Where is it supposed to be located?

---

### Post by tjones00 on 2011-01-11
For you it's 

load-module module-alsa-sink device=hw:1,7

Your device is 1,7 remember? 1,9 is used in my examples because that is the device on my lenovo ion2 card.

If there is nothing at /etc/asound.conf make it yourself ;)

```
gksudo gedit /etc/asound.conf
```

Remember to use the proper device definition in this file as well.

---

### Post by UptownRiot on 2011-01-11
Ahhhh! It works! It's a miracle!!!!!

---

### Post by tjones00 on 2011-01-11
Good stuff.

---

### Post by UptownRiot on 2011-01-11
Thank you very much for your help. I definitely would not have gotten it done with out it. 

Now to set about the task of installing, and configuring xbmc. That, however, is for another forum. ;-)

---

