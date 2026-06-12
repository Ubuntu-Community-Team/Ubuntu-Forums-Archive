---
title: "Howto fix microphone on Ubuntu 9.10"
date: 2009-11-27
forum: General Help
---

### Post by TDK800 on 2009-11-27
1. From ubuntu menu go to System > Administration > Synaptic Package Manager

2. Search for "linux-backports-modules-alsa-2.6.31-15-generic" - the version number of this package should match your current (latest) kernel. To find out your kernel version type "uname -a" in terminal.

3. From ubuntu menu to to System > Preferences > Sound > Input Tab
Make sure input sound is not muted and that the volume is on the "unamplified" mark or the sound will be distorted (in case you have previously dragged it to max to fix the mic). Some of you who previously had mic1 and mic2 under the "choose a device for sound input", should now have "Internal audio analog stereo" as the only option there.


Be sure to post back if this fixes the mic problem for you!

---

### Post by koba101 on 2009-11-27
alright you need to install the server part as well and then restart your system

Thanks

---

### Post by dkeats on 2009-11-27
It fixed it for me!
Thanks and regards.

---

### Post by mdurham on 2009-11-27
Hi TDK800, I posted this problem in another thread but have had no replies, I thought I might possibly have better luck with you.

I have a usb phone handset plugged in permanently.
How do I get the received sound from Skype to come from the usb phone and all other sounds from the computer sound card?

**I can get all sounds from phone only or all sounds from the card only.** How do I select for only Skype sound to come from the usb phone? There doesn't seem to be a way to do this.

I have no problem with the microphone as I can select the sound source when Skype is running using "Pulseaudio Device Chooser".
Any help would be most appreciated.

Cheers, Mike

---

### Post by iceman85 on 2009-11-27
THANKS A LOT TDK800!!!!!

Now everything works ;)

---

### Post by crpenaherrera on 2009-11-28
> **TDK800 said:**
> 1. From ubuntu menu go to System > Administration > Synaptic Package Manager

2. Search for "linux-backports-modules-alsa-2.6.31-15-generic" - the version number of this package should match your current (latest) kernel. To find out your kernel version type "uname -a" in terminal.

3. From ubuntu menu to to System > Preferences > Sound > Input Tab
Make sure input sound is not muted and that the volume is on the "unamplified" mark or the sound will be distorted (in case you have previously dragged it to max to fix the mic). Some of you who previously had mic1 and mic2 under the "choose a device for sound input", should now have "Internal audio analog stereo" as the only option there.


Be sure to post back if this fixes the mic problem for you!

Bad news for me... it is not working. But I seemed a problem of the system. Sudenly today the sound for launching programs or the welcome music has stopped. Do you know what should be the problem? Is there any command I could you to display errors in my systems?

Thanks in advance..

---

### Post by bredgeo on 2009-11-28
Hello to all,

I have a laptop (Toshiba equium L350) and cannot seem to get my built in mic to work... nor can I get the 3.5 plug mic to work.

Note: When I was using 8.10, and them 9.04 I was able to use the 3.5 plug mic. So I did not really bother with the built in mic.

This said, now that I am using 9.10... I followed the steps to install "linux-backports-modules-alsa-2.6.31-15-generic". All that went well, but now when I try to go to System > Preferences > Sound > Input Tab... once I click on Sound I get "Waiting For Sound System To Respond"..... ???????

I re-booted, and it gives me the same thing. I did go to Skype, I did notice that I know have a few choices for the mic (compared to one choice before) but none seem to work for the built in nor the 3.5 mic........ :frown:

Help.... Thank you.

Oh yes, this is my first post! ;)

regards,
Bredgeo

---

### Post by Waldvogel on 2009-11-28
This hasn't solved the problem unfortunately.

---

### Post by ok_dr on 2009-11-28
No nothing fixed for me. With Jaunty and intrepid at least the external mic would work, only the laptop's internal mic didn't work, now neither of them is of any use. I use Skype a lot so this really is forcing me to stay on Windows most of the time.

---

### Post by mdurham on 2009-11-28
Have you tried installing an older version of Skype? 2.0.0.72 worked for me. This allows for selecting input & output and isn't locked to pulse.
Just a thought!

---

### Post by Waldvogel on 2009-11-28
Well it's not a problem with skype-e.g. I can't record sound with audacity either.

---

### Post by bxcrx on 2009-11-28
Confirmed the same problem here running 9.10 with a single analog mic which worked since 8.10-9.04

---

### Post by NathanLT on 2009-11-28
Hi

I updated from Kubuntu 9.04 to 9.10 and experienced similar problems with my microphone. The linux-backports-module-alsa package didn't fix the issue for me, but I managed to get my microphone input working by installing PulseAudio.

I'm not using Ubuntu so I don't know how you'd do this in the new Ubuntu Software Centre, but here's how to do it from a terminal:

```
sudo apt-get install pulseaudio paman pavumeter
```

(if you already have PulseAudio installed, you will get a message telling you this)

then restart your computer. If you are using Kubuntu, you can change your default sound capture device to the PulseAudio server by clicking on System Settings > Multimedia, then in the left hand menu selecting 'Audio Capture'. Next, in the Multimedia section of the Kickoff menu select 'PulseAudio Volume Control' (or press Alt+F2 and enter 'pavucontrol'). Fiddling around with the volume settings in there got my microphone working.

If you already have PulseAudio installed, check that it is running by searching for it in the System Monitor, and check that the PulseAudio server is set as your default sound capture device. If that still doesn't solve the problem, try looking [here]("https://wiki.kubuntu.org/DebuggingSoundProblems/KarmicCaveats").
  	 	 	* 
Is this problem caused by Karmic assuming that people are running PulseAudio? 


Nathan

---

### Post by Uglamugla on 2009-11-28
i continue with the same problem, i'm using ubuntu 9.10 the first tutorial didn't solved my problem, then i used the idea of nathan but it didn't solved either, when i go to system preferences sound, in the input tab i can't change anything to de pulseaudio.

if anyone knows other ways than tell us please

---

### Post by bredgeo on 2009-11-29
WOW!!!! Okay!!!! 

After having re-read, re-done what I had already did, getting the sound manager back up --thank you NathanLT for the command. Going to ***EVERY*** link, up dating, re-installing etc. 

Its all works the way I want it to (well, the 3.5 mic does not... but the built in mick does!!!!).:popcorn: Good enough for me!!! Don,t need to go back to Windows all the time.

Thank you all! :D

---

### Post by Big JT on 2009-11-29
NathanLT you definately have provided the much needed piece of this puzzle.  I am running Ubuntu 9.10 64 bit on an Acer Aspire 4520 and I have tried everything to get the microphone to work (installing "linux-backports-modules-alsa-2.6.31-15-generic" and going to the terminal and running "alsamixer") and trying this and that with no luck!  Finally the problem is not alsa, it's configuring the pulse audio component.  I went to Synaptic Package Manager and searched for "pavumeter" which did come up.  I marked it for installation and it told me I had to install additional packages (one being "paman" and many more).  I did this and after installing I went to "Applications"->"Sound & Video"->"PulseAudio Volume Control".  I clicked on the "Input Devices" tab and selected Microphone 2 on the "Port:".  At the bottom of the window you can see "Show" and choose "Hardware Input Devices" and you should notice a moving bar with the words "Silence", "Base", and "Max" above it.  Hopefully it is moving if the microphone is picking up sound.  Mine is!  I tested the microphone using "Sound Recorder" program and guess what...IT WORKS!!!!!  Finally!!!!  Now I can embrace Ubuntu instead of defaulting to Windows Vista!  Thanks again NathanLT

---

### Post by Gendor on 2009-11-29
I have an Intel-based sound card on a HP laptop. I had some issues with sound in Skype on 9.04, and configured the *Sound out* and *Ringing* settings to "pulse", with *Sound In* still configured as "HDA Intel (hw:Intel,0)" and it worked like a charm. 

After upgrading to 9.10, any sound from within Skype would be very intermittent/scratchy/garbled. Changing the settings to "HDA Intel (hw:Intel,0)" would just result in no sound. But when I **leaved** the settings on "HDA Intel (hw:Intel,0)" and **restarted** (you might have to restart your computer as Skype doesn't want to close on its own) it worked perfectly.

I'm hypothesizing that if you have your Skype settings on "pulse" and you change it to something else, Skype is still connected to the Pulseaudio server, but when you (force) exit it disconnects, and on restart it's able to play the sound through your ALSA sound mixer. Anybody's thoughts on this?

---

### Post by bxcrx on 2009-11-29
I still have the problem with my external microphone not working after installing the following packages:

linux-backports-modules-alsa-2.6.31-15-generic <= didn't work
linux-backports-modules-alsa-karmic <= didn't work
pulseaudio paman pavumeter<= didn't work

I uninstalled all of those packages and booted with a Live 9.10 CD and my microphone works fine from the live CD.  The program that I was using was "Sound Recorder" which is stock with the install of 9.10

I compared the sound settings from the Live CD with the fully booted desktop running a clean install of 9.10 with all of those packages uninstalled (above) and no luck as of yet

I'm guessing there either was an update that broke alsa, or I somehow have the wrong driver/module loaded

Any ideas?

---

### Post by wintolinux on 2009-11-29
Hi,  I am new ubuntu. 

I have the same problem as others in the post. Read some of them and did new package installs. But nothing seems to work. 

It is HP G60-530 laptop. 
 
I installed both of these pacakges. It still does not work. 

linux-backports-modules-alsa-2.6.31-15-generic  
linux-backports-modules-alsa-karmic

Is the below information helps to guide me ?

                description: Audio device              product: 82801I (ICH9 Family) HD Audio Controller 
             vendor: Intel Corporation              
physical id: 1b
              bus info: pci@0000:00:1b.0
              version: 03              
width: 64 bits 
             clock: 33MHz              
capabilities: pm msi pciexpress bus_master cap_list 
              configuration: driver=HDA Intel latency=0 
             resources: irq:22 memory:d4700000-d4703fff
Thanks

---

### Post by pdoma on 2009-11-30
I'm also having the same problem, my laptop does not have an internal mic. just a 3.5mm plug. I fallowed this post (and a few other ones) step by step and had no luck at all. I love that canonical constantly improves ubuntu but the fact that almost every time they brake something along the way that was working just fine in previous release is just crazy.

---

### Post by eessau on 2009-11-30
> **TDK800 said:**
> 1. From ubuntu menu go to System > Administration > Synaptic Package Manager

2. Search for "linux-backports-modules-alsa-2.6.31-15-generic" - the version number of this package should match your current (latest) kernel. To find out your kernel version type "uname -a" in terminal.

3. From ubuntu menu to to System > Preferences > Sound > Input Tab
Make sure input sound is not muted and that the volume is on the "unamplified" mark or the sound will be distorted (in case you have previously dragged it to max to fix the mic). Some of you who previously had mic1 and mic2 under the "choose a device for sound input", should now have "Internal audio analog stereo" as the only option there.


Be sure to post back if this fixes the mic problem for you!
I did this. Now I cant configure sound. When I go to System > Preferences > Sound says "wating for the sound system".
I've removed "linux-backports-modules-alsa-2.6.31-15-generic" but even I've restarted still the same... now I'm installing sound system back but I think microphone problem will continue. By the way I'm using vaio-vgn ns21z sony laptop. I think it is a particular problem for laptops isn't it...

---

### Post by bxcrx on 2009-12-01
> **pdoma said:**
> I'm also having the same problem, my laptop does not have an internal mic. just a 3.5mm plug. I fallowed this post (and a few other ones) step by step and had no luck at all. I love that canonical constantly improves ubuntu but the fact that almost every time they brake something along the way that was working just fine in previous release is just crazy.

Did you try booting from the Live 9.10 CD to see if it works in evaluation mode?

---

### Post by pdoma on 2009-12-01
Yep, works fine when booted from live CD of 9.10.

---

### Post by bxcrx on 2009-12-01
It looks like a few folks, including myself, have the same problem with the microphone working with the LiveCD and not when booted from the hard drive O/S found on launchpad here:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/460351](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/460351)

---

### Post by Waldvogel on 2009-12-02
I've read many of the possible solutions and tries to put them into practice but none of them work.

Surely there should be some update for ubuntu?

---

### Post by DenisGLX on 2009-12-03
I performed all of the above suggestions. PulseAudio shows that internally the microphone works, but I do not hear any sound from the mic... Obs.: The microphone is not muted and I am listening to all my songs as I always did. 

Message to the experts of the forum: Please, don't give up of us...

---

### Post by Waldvogel on 2009-12-04
Well it's really annoying because I'd love to be able to recommend Ubuntu to people but I really couldn't for reasons such as this.

---

### Post by crpenaherrera on 2009-12-05
Hey folks, one question... does any body of you use Skype for internet calls? I have realized that my problems started when installing skype. Since then I have a conflict when using it (as it uses pulseaudio) with the alsa drivers. Even my rhythmbox freezes sometimes.

In 9.04 it worked fine. For me it seems that I will need to downgrade my ubuntu version, there is no other choice :(. But anyway I will post the bug in launchpad, and would recommend everybody do the same. 

Cheers my ubuntu-friends,

CP

---

### Post by elzear on 2009-12-07
i had same problem.

Nothing dont work for me, upgrade alsa or PA

I found this when i serch information about my MIC.

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

i have HP compaq nx6325 and after writed some lines and reload alsa my MIC, start recording.

---

### Post by TDK800 on 2009-12-07
I think the reason why it is solving the problem for some people, but not for eveyrone is that the issue is caused by internal microphone not detected correctly (newer/too old laptop models?) and after the update, it correctly identified the microphone for some people, but there may be internal microphones that still are not detected even after the update which provides new driver information.

There was just a kernel update for ubuntu 9.10 few days ago, maybe a new alsa package for that kernel version is also available that fixes it for you this time.

And type "alsamixer" in terminal and make sure your mic volume is not turned down.

---

### Post by TDK800 on 2009-12-08
ok, since the latest kernel updates a few days ago, it's not working again... and I am unable to fix it with this method.

This is a critical bug imho.

---

### Post by bxcrx on 2009-12-08
> **TDK800 said:**
> ok, since the latest kernel updates a few days ago, it's not working again... and I am unable to fix it with this method.

This is a critical bug imho.

Can you ask the mod's to remove the "[SOLVED]" from this thread then?

Does your microphone work while booted from the 9.10 LiveCD?

Also when your booting from the 9.10 LiveCD what is your output for this?

/etc/modprobe.d/alsa-base.conf 

&

amixer


When your booted from your hard drive what is the output of 

/etc/modprobe.d/alsa-base.conf 

& 

amixer

?

---

### Post by iceman85 on 2009-12-12
this solution works with Skype v. 2.0 not with 2.1 :(

---

### Post by pdoma on 2009-12-28
After almost giving up i fixed my microphone problem with the help of a link posted by bxcrx. Basicaly I edited the alsa-base.conf file to the bellow by adding the lines in [COLOR="Red"]red[/COLOR]...

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N [COLOR="Red"]model=auto[/COLOR]

Honestly i was kinna shooting in the dark by adding what seemed to work for other people and doing the above worked fine. My microphone works perfectly fine now.

---

### Post by thom# on 2009-12-30
I am new to Ubuntu & I'm have been unsuccessful to get my microphone to work.

I am running Ubuntu 9.10 on a Dell Dimension 3000 with SB04100 (Sound Blaster Live) sound card.

My sound card is set to CA0106 Soundblaster Analog Stereo.

[B]
Methods I have tried:[/B]


[LIST=1]
[*]adjusting the levels in System > Preferences > Sound > Input
[*]installing "linux-backports-modules-alsa-2.6.31-16-generic"
[*]adjusting levels in "alsamixer" and ensuring that the microphone is set to capture.
[*]installing PulseAudio components "pulseaudio paman pavumeter etc"
[*]adjusting levels in "pavucontrol"
[*]adding the following lines (in red) to "alsa-base.conf"
[/LIST]
[INDENT]> [COLOR=Red]options snd-hda-intel enable_msi=1[/COLOR]
[COLOR=Red] options snd-hda-intel model=F1734 position_fix=2
[/COLOR]options snd-hda-intel power_save=10 power_save_controller=N [COLOR=Red]model=auto[/COLOR][/INDENT]I have tried connecting the headset to both the soundblaster input & the onboard input, however neither of these methods give me any output in "pavumeter --record".

Any help would be greatly appreciated. :)

---

### Post by adept_king on 2009-12-30
i hear my microphone on my speaker, but skype does not hear it no matter which of the 20 different mixers i try to find a "select this recording source" in (very few of these mixers make any sense, they certainly do not have any 'select this recording source' button.) 

pulseaudio device chooser shows skype picking up on my input, but it is simply not true, because test calls record nothing after the beep.   

if i had the extra time to waste discovering a temporary fix in lieu of the next snafu, i would, but being that i am not a developer or a programmer, its just a waste of time. people pay for windows because it just works.  blue screens are a big linux joke, but they are cake compared to tying my shoes (so to speak) in ubuntu. 

:(

the open source community almost seems sabotaged.  at least google chrome works now.

---

### Post by thom# on 2009-12-30
*Update:*

I have managed to hear my microphone through my speakers, by muting IEC958 in the playback section of AlsaMixer. (Shared Mic/Line In is set to 'Mic in' in the capture section.)

However, I still cannot view anything on the PulseAudio Volume Meter (Recording).

I can view sound playing on the PulseAudio Volume Meter (Playback), however I cannot view the sound that is generated from the microphone.

---

### Post by pdoma on 2009-12-30
Thom#

Read the bellow thread,  when you edit the file you need to put in the info that reflects your hardware. They have the hole list there.

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Thanks.

---

### Post by fragos on 2009-12-30
I think there are two parts to this problem. The 1st is having your microphone recognized by Ubuntu. I accomplished that with installing any packages or going to the command line. It appears that the default mic selection is wrong. Going to the Sound Preferences Input tab I found two input options with the same description. The 1st was selected and the connector selection above was Analog Input. I tried the second and the connector selection changed to "Analog Microphone/Input 1/Microphone 1". The Input level meter now responded to my voice and application like Sound Recorder worked where they hadn't before. Skype however won't work for Voice. When I try the Echo/Sound Test which worked in prior versions I get the message "Problem with Audio playback".

I just tried Skype again and got voice working. In Skype Options I selected Sound Options. Sound In, Out and Ringing all their own parameters which were set to Default Device. When changing them there were a number of options. My PC has VIA 8237 sound hardware. For VIA there were 4 options. I tried "VIA 8237 (plughw:V8237,0)" for both sound in and out -- Skype echo test now works. With 9.10 it appears that the issues are configuration and software, at least for me anyway.

---

### Post by thom# on 2009-12-31
Sorry, I forgot to mention earlier that I'd tried a range of options for Dell PCs, as listed at:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
None of these seemed to make any difference.

I decided to go back to basics, assuming I'd made an error with the configuration of ALSAmixer, and boot Ubuntu 9.10 from the live CD.

I noticed that in the Capture section of ALSAmixer, Digital Source was set to 'is2 in'. After setting Analog Source to Mic, and Shared Mic/Line In to Mic, Ubuntu was able to recognise my microphone.

Skype 2.1 is also able to recognise my microphone.

Thank you for your help :)

---

### Post by pdoma on 2009-12-31
I would also like to add that the fix i found for my microphone problem created yet another problem. Now my audio output goes out to both speakers and headphones at all time. Before it would switch from the internal speakers to headphones when I plugged them in. But I guess I can live with that as long as i can use Skype.

---

### Post by bxcrx on 2010-01-02
I'm running:

Pulse Audio v 0.9.21
Alsa v 1.0.20 (Stock with 9.10)

I got my microphone to work finally, probably from messing with alsamixer, but there are some lingering issues that I'm still watching.

After everything was working as it should I had to save my alsamixer settings via:

sudo alsactl store 0

After a restart my gnome volume would be muted so I had to do the following:

I commented out line 372 in /etc/init.d/alsa-utils:

# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1

Also my input settings for my microphone in the Gnome Sound Preferences sometimes has a check box in "muted" that I have to remove after a restart sometimes -- I'm still tracking that down

Here is my working alsamixer settings :

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 28 [90%] [-4.50dB] [on]
  Front Right: Playback 28 [90%] [-4.50dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Shared'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Center/LFE Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 30 [97%] [10.50dB] [on] Capture [off]
  Front Right: Playback 30 [97%] [10.50dB] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [12.00dB] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [12.00dB] [off] Capture [off]
  Front Right: Playback 31 [100%] [12.00dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Analog to IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Exchange Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Swap Surround Slot',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

Here is my default.pa settings:

Here are my working Gnome Sound Preferences

Internal Audio
1 Output / 1 Input
Analog Stero Duplex

Input
Analog Microphone/Microphone 1
Internal Audio Analog Stero

Output
Internal Audio Analog Stero
Analog Output / No Amplifier

---

### Post by adept_king on 2010-01-02
> **thom# said:**
> Sorry, I forgot to mention earlier that I'd tried a range of options for Dell PCs, as listed at:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
None of these seemed to make any difference.

I decided to go back to basics, assuming I'd made an error with the configuration of ALSAmixer, and boot Ubuntu 9.10 from the live CD.

I noticed that in the Capture section of ALSAmixer, Digital Source was set to 'is2 in'. After setting Analog Source to Mic, and Shared Mic/Line In to Mic, Ubuntu was able to recognise my microphone.

Skype 2.1 is also able to recognise my microphone.

Thank you for your help :)

the is2 in thing really did the trick.
dont know why it works, but thanks for the voodoo!

---

### Post by alldaylong on 2010-01-16
Hey I had all of the problems mentioned here, and finally fixed it by getting rid of pulseaudio and using ALSA instead. Now skype 2.1 works on karmic for me, as well as the mic (which wasn't working), and the speakers now actually mute when you plug the headset in (ie, functions like it should).

I'm posting this in case anyone else out there is having the same problems that I did. Here's the thread that fixed the issue for me [http://ubuntuforums.org/showthread.php?p=8675681&posted=1#post8675681](http://ubuntuforums.org/showthread.php?p=8675681&posted=1#post8675681)

---

### Post by olofcadiz on 2010-01-17
For me the microphone is working after follokwing adjustments
Gnome volume preferences

[IMG]http://olofpark.com/volym10.png[/IMG]
[IMG]http://olofpark.com/volym11.png[/IMG]

Choose the microphone and adjust sound level
Test here to find out if microphone works

[IMG]http://olofpark.com/volym12.png[/IMG]
[IMG]http://olofpark.com/volym13.png[/IMG]

alsamixer -V all
and adjust sound levels like this

[IMG]http://olofpark.com/alsa4.png[/IMG]
[IMG]http://olofpark.com/alsa5.png[/IMG]
[IMG]http://olofpark.com/alsa6.png[/IMG]

Install skype-ubuntu-intrepid_2.1.0.47-1_i386.deb
and open options>sound and adjust like this

[IMG]http://olofpark.com/skypetest.png[/IMG]

Make a testcall
Now it work for me
Good Luck

---

### Post by Animedude3000 on 2010-01-19
> **TDK800 said:**
> 1. From ubuntu menu go to System > Administration > Synaptic Package Manager

2. Search for "linux-backports-modules-alsa-2.6.31-15-generic" - the version number of this package should match your current (latest) kernel. To find out your kernel version type "uname -a" in terminal.

3. From ubuntu menu to to System > Preferences > Sound > Input Tab
Make sure input sound is not muted and that the volume is on the "unamplified" mark or the sound will be distorted (in case you have previously dragged it to max to fix the mic). Some of you who previously had mic1 and mic2 under the "choose a device for sound input", should now have "Internal audio analog stereo" as the only option there.


Be sure to post back if this fixes the mic problem for you!


> **NathanLT said:**
> Hi

I updated from Kubuntu 9.04 to 9.10 and experienced similar problems with my microphone. The linux-backports-module-alsa package didn't fix the issue for me, but I managed to get my microphone input working by installing PulseAudio.

I'm not using Ubuntu so I don't know how you'd do this in the new Ubuntu Software Centre, but here's how to do it from a terminal:

```
sudo apt-get install pulseaudio paman pavumeter
```(if you already have PulseAudio installed, you will get a message telling you this)

then restart your computer. If you are using Kubuntu, you can change your default sound capture device to the PulseAudio server by clicking on System Settings > Multimedia, then in the left hand menu selecting 'Audio Capture'. Next, in the Multimedia section of the Kickoff menu select 'PulseAudio Volume Control' (or press Alt+F2 and enter 'pavucontrol'). Fiddling around with the volume settings in there got my microphone working.

If you already have PulseAudio installed, check that it is running by searching for it in the System Monitor, and check that the PulseAudio server is set as your default sound capture device. If that still doesn't solve the problem, try looking [here]("https://wiki.kubuntu.org/DebuggingSoundProblems/KarmicCaveats").
                * 
Is this problem caused by Karmic assuming that people are running PulseAudio? 


Nathan

Thanks! I was finally able to fix it thanks to your help. My external mic now works with Skype, Sound Recorder and Audacity :D

---

### Post by funfrank on 2010-06-14
OK.  This is a really great problem.  Like a few others in the forum, my microphone functions only with the live CD.  Unlike a few others, the above solutions have not solved my problem.  Alsamixer with the live CD displays the following channels:

Master
PCM
Front
CD
Mic
Capture
Beep
Caller
Off hook

After installing, alsamixer displays only 

Master
PCM
CD
CAPTURE
BEEP
Caller ID
INPUT SOURCE (mic or cd are the available selections)
Off hook

As you can see, the microphone is not available in the installation.  My alsa-base.conf files are identical for the live CD and my installation, so that means something else is changing my ALC861 controls.  Any idea what that may be?  I need to be able to use skype in order to donate money to poor aliens on Neptune -- it's really important!

---

### Post by jvin248 on 2010-07-14
> **TDK800 said:**
> ...

3. From ubuntu menu to to System > Preferences > Sound > Input Tab
Make sure input sound is not muted and that the volume is on the "unamplified" mark or the sound will be distorted (in case you have previously dragged it to max to fix the mic). Some of you who previously had mic1 and mic2 under the "choose a device for sound input", should now have "Internal audio analog stereo" as the only option there.


Be sure to post back if this fixes the mic problem for you!

After a lot of searching and testing and changes, this is what fixed the 'no mic' problem for me.  Dell Latitude D630 with STAC9205 sound card.

---

### Post by TDK800 on 2010-08-02
Glad to see it fixed the problem for so many people. If anyone here is still having mic problems, post your PC make and internal/external mic information.

On all Ubuntu 10.04 and Ubuntu 10.10 fresh installs and upgrades internal microphone has worked perfectly so far.

---

### Post by Bryan55 on 2010-10-21
Hi.
I think I have tried about everything to get my mic working in Karmic except for editing the alsa-base.conf file but I can not get it to open. I tried the text below in the Terminal but got "command not found"
/etc/modprobe.d/alsa-base.conf

How do I go about getting it?

Thank in advance for any help.

Bryan.

---

### Post by funfrank on 2010-10-21
bryan,

the line you typed is just a location in your file system.  try typing sudo gedit in front of the location.  sudo gives you permission and gedit is a command to open a text editor.

---

### Post by Bryan55 on 2010-10-21
I put the "sudo" but not the "gedit"

I did the edits but still no joy.

Cheers anyway
Bryan.

---

### Post by bxcrx on 2010-12-16
> **Bryan55 said:**
> I put the "sudo" but not the "gedit"

I did the edits but still no joy.

Cheers anyway
Bryan.

I would consider upgrading if possible.

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by Bryan55 on 2010-12-16
bxcrx wrote> I would consider upgrading if possible.I tryed the live cd for 10.10 about 2 weeks ago and there were more options for input microphones and I manage to get it working, although there was a lot of hissing.

Haven't done the upgrade yet.

Cheers
Bryan.

---

### Post by Alexarm on 2011-01-11
> **TDK800 said:**
> 1. From ubuntu menu go to System > Administration > Synaptic Package Manager

2. Search for "linux-backports-modules-alsa-2.6.31-15-generic" - the version number of this package should match your current (latest) kernel. To find out your kernel version type "uname -a" in terminal.

3. From ubuntu menu to to System > Preferences > Sound > Input Tab
Make sure input sound is not muted and that the volume is on the "unamplified" mark or the sound will be distorted (in case you have previously dragged it to max to fix the mic). Some of you who previously had mic1 and mic2 under the "choose a device for sound input", should now have "Internal audio analog stereo" as the only option there.


Be sure to post back if this fixes the mic problem for you!


You are the best!!!! :D I've tried every other solution but didn't work for me!! THANKS!!!!!

---

### Post by bayners123 on 2011-02-26
Thanks a lot, that worked perfectly. I'm on a VAIO VGN-SR16GN for people searching.

---

