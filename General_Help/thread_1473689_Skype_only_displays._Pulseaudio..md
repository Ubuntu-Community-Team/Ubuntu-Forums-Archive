---
title: "Skype only displays. Pulseaudio."
date: 2010-05-05
forum: General Help
---

### Post by chrispche on 2010-05-05
I'm getting pissed off, I went out bought a new mic. No joy, I even bought a USB sound card. No joy. I'm using 64bit 10.04 and I simply, simply cannot talk to my kids in South Africa. It's my only communication with them. If this keeps up I'm going to roll back to Ubuntu 9.10. Which I do not want to do. How do I get the ALSA drivers up and running in Skype? No one seems to be able to help me on here or on IRC. It's like I'm the only one with the problem.

My sound card is: ATI Technologies Inc SBx00 Azalia (Intel HDA)
My Mic is: Plantronics

THERE HAS TO BE A WAY AROUND THIS!

PS I'm installing Windows XP in Virtual Box in the hope I can get Skype working in that. I need to speak to my kids in South Africa daily. I'm in the UK.

---

### Post by lidex on 2010-05-05
Have you looked here:
[https://help.ubuntu.com/community/Skype]("https://help.ubuntu.com/community/Skype")

Can you describe the problem in detail? Is your sound working otherwise? What is broken?

---

### Post by kostkon on 2010-05-05
It's easy to setup Skype to use your USB card, don't worry. Just install the *PulseAudio Device Chooser* utility and use the pulseaudio volume control to select an input and output device for Skype.

---

### Post by Bucky Ball on 2010-05-05
Yea, my wife's laptop had probs when she bought a USB headset. Sound was working fine before, Skype wasn't working though. I ended up uninstalling Pulse and it worked fine until I went to the volume control, chose that headset device (USB) and try to adjust the output volume. The left channel went down and stayed down, won't move. Right channel fine.

Weird. Pulse has always been problematic for me, but that could be me. ;)

---

### Post by chrispche on 2010-05-05
> **lidex said:**
> Have you looked here:
[https://help.ubuntu.com/community/Skype]("https://help.ubuntu.com/community/Skype")

Can you describe the problem in detail? Is your sound working otherwise? What is broken?

The mic is not picking up my voice. In Sound Preferences there input level indicator shows no activity, even when the mic is up to 100%.

---

### Post by chrispche on 2010-05-05
I'm GETTING REALLY REALLY ANNOYED with Ubuntu 10.04. I have changed the driver to e-sound as the article suggests. No joy. I have reset back to pulseaudio no joy. Now I have lost my volume control bar. This f'ing ****. I want to be able to do a simple thing like use Skype to talk to my kids. After 5 years of using Ubuntu, I might go for Windows 7 if this **** keeps up.

---

### Post by chrispche on 2010-05-05
Sorry I've calmed down now. Just did a little meditation. Arghhhh how it's frustrating to hear your 5 year old daughter and not be able to respond. I never had any of this trouble in 9.10.

---

### Post by fragos on 2010-05-05
Have you tried running alsa-mixer in a terminal window. It gave me more items to adjust sound level and muting for. select with left/right mouse, vol wuth up/down and toggle mute with "M".

---

### Post by chrispche on 2010-05-05
Tried all that.

---

### Post by lidex on 2010-05-05
So your mic is unmuted in alsamixer? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by chrispche on 2010-05-06
And it seems I've got someone who knows what they are talking about sure, here you go.

```
chrispche@chrispche-laptop:~$ uname -a
Linux chrispche-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
chrispche@chrispche-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
chrispche@chrispche-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
chrispche@chrispche-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card0/codec#3 <==
Codec: Realtek ALC262
chrispche@chrispche-laptop:~$ 

```

My Laptop make is a Samsung R20.

Thanks, I'm praying to all the Buddha's and holy beings you can help me here.

Cheers.

---

### Post by lidex on 2010-05-06
Something screwy in the way alsa sees your devices. Try an alsa upgrade first. Click the alsa-upgrade-script link in my sig and follow directions there.

Did you make any changes in configuration files in the course of troubleshooting? And if so, what?

---

### Post by chrispche on 2010-05-06
I changed to esound. I'm going to re-install my system, everything is backed up. I want a fresh start to do this.

---

### Post by sammy07 on 2010-05-06
Had the same problem here, really annoying. Have a look, this fixed it for me:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574504](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574504)

---

### Post by palexv on 2010-05-06
> **sammy07 said:**
> Had the same problem here, really annoying. Have a look, this fixed it for me:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574504](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574504)

Yes, this should help! I thought I became crazy while resolving it.

Spent more than 2 days for this :mad:

---

### Post by chrispche on 2010-05-06
I have come to a different resolution. I spared 5 Gig from my Hard Drive and installed Xubuntu 9.10, minimal installation. Only have Skype on it. So when I want to speak to my kids in South Africa I just dual boot into 9.10 Xubuntu. It works perfectly.

It's a solution till a bug fix is released.

---

### Post by Ahunt on 2010-05-06
I am having the same problem here. I have installed Skype on an Acer AOA 150 netbook running Ubuntu 10.04 for my wife's daughter. Everything works fine except that Skype is not accepting the audio input from the built in mic. I tested the mic on the Sound Recorder and it works just fine.

I thought I had it figured out based on the info at [http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html) and installed ALSA-OSS from the Ubuntu Software Center, but it didn't help.

The launchpad post above looks promising, except that Launchpad is down - what does it say there?

---

### Post by lidex on 2010-05-06
> **Ahunt said:**
> I am having the same problem here. I have installed Skype on an Acer AOA 150 netbook running Ubuntu 10.04 for my wife's daughter. Everything works fine except that Skype is not accepting the audio input from the built in mic. I tested the mic on the Sound Recorder and it works just fine.

I thought I had it figured out based on the info at [http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html) and installed ALSA-OSS from the Ubuntu Software Center, but it didn't help.

The launchpad post above looks promising, except that Launchpad is down - what does it say there?

LOL. Probably just getting hammered. Here you go:
> 

Fixed it!

1. Added [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu") to sources list

2. sudo apt-get install linux-alsa-driver-modules-$(uname -r)

And it works!!! It took me 2 days to figure out.

Guys, this should work from clean install. Its very bad to waste days to figure out such single thing as record from mic.


To add PPA on lucid:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
```

---

### Post by Ahunt on 2010-05-06
lidex: Thank you for that. True, Launchpad is probably a bit "oversubscribed" right now! Let me give that a try and see if it works. I'll post back here when I have tried that.

---

### Post by palexv on 2010-05-06
If briefly

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```

---

### Post by chrispche on 2010-05-07
Problem here.

```
chrispche@chrispche-laptop:~$ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5

gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com
gpg: key 72B194E5: "Launchpad Ubuntu Audio Dev team PPA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
chrispche@chrispche-laptop:~$ 
chrispche@chrispche-laptop:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-22-generic
chrispche@chrispche-laptop:~$ 

```

---

### Post by palexv on 2010-05-07
This is correct 

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```

---

### Post by sammy07 on 2010-05-07
You have to make a 
sudo apt-get update

after adding the repository to update the package information. Microphone should work after reboot. Good luck.

---

### Post by chrispche on 2010-05-07
> **palexv said:**
> This is correct 

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```

Thank you. I forgot about that.

---

### Post by chrispche on 2010-05-07
Nah didn't work. Anything else anyone think of?

---

### Post by chrispche on 2010-05-07
Actually I made a mistake it works.

---

### Post by lidex on 2010-05-07
> **chrispche said:**
> Actually I made a mistake it works.
Whoa...fantastic. Could you mark the thread as solved using 'Thread Tools' up top please. Will help others with same problem.

---

### Post by zbyszek26104 on 2010-05-10
Didn't work for me.. Tried everything, got ubuntu 64 and Asus G50Vt. And need skype very much...

---

### Post by fragos on 2010-05-10
Have you considered that your trouble may be the 64 bit version? As an experiment, why not dual boot a 32 bit Ubuntu Generic and see if that solves your problem.

---

### Post by zbyszek26104 on 2010-05-11
Ok, but I didn't have any troubles in 9.10 64 bit. I've decided to install new 10.04 and still nothing helped..

Any idea?

---

### Post by zbyszek26104 on 2010-05-11
I need it very much... Could anyone help me?

---

### Post by zbyszek26104 on 2010-05-13
Another update and still nothing changed..

---

### Post by john1066 on 2010-05-13
I have the same problem with my Acer Aspire 6930G. Skype won't make a test call won't show video. Audacity won't record sound. Cheeses does work. Had the same problems with 9.10 and now with 10.04. All of this works fine with Vista (performance sucks though) so I'm amazed that Ubuntu can't get this going. Given all the difficulties Ubuntu has with sound I doubt this will ever be solved. I've ordered Windows 7 as my best way out.

Good luck.

John

---

### Post by john1066 on 2010-05-13
And can we remove the solved flag. It's not.

John

---

### Post by keljaden on 2010-05-13
Are people unable to use the "edit" button? what's with all the double and triple posts on this forum.

---

### Post by lidex on 2010-05-13
> **john1066 said:**
> And can we remove the solved flag. It's not.

John

Sorry, it is solved for the OP.
Perhaps you could install ubuntu-tweak and use the source editor to add the skype repository. Also: gnome-alsamixer is your friend as well as an alsa upgrade...

---

### Post by zbyszek26104 on 2010-05-14
Tried everything in gnome alsa mixer and still nothing happened :/

---

### Post by Bucky Ball on 2010-05-14
Can you open the Pulseaudio Volume Control? If so, get an audio stream going. That will appear in Playback streams. Right click on the playback stream and 'Move Stream' to the appropriate sound device.

Just a shot.

---

### Post by zbyszek26104 on 2010-05-17
Anyone else? The only solution is to change system?

---

### Post by e-Gee on 2010-05-17
Open gedit and paste this line in

/bin/sh -c "PULSE_SERVER=127.0.0.1 skype"

and save somewhere and name it skypelouncher then in main menu change skype louncher, path to that file you created in gedit.

---

### Post by zbyszek26104 on 2010-05-17
I tried all input options from the list and still don't have sound :(

---

### Post by soltanis on 2010-05-17
Didn't read the whole thread but it sounds like the solution is to UNINSTALL PULSEAUDIO.

```

sudo apt-get purge pulseaudio
sudo apt-get install alsa-utils alsa-base
sudo dpkg-reconfigure linux-sound-base # and make sure ALSA is selected
sudo reboot

```

Solved the problem for me pretty quickly.

Seriously why do we keep pushing the extremely broken, extremely useless Pulseaudio package? It simply doesn't work. Until it does, it has no business being the default audio server in a supposedly stable distribution.

---

### Post by zbyszek26104 on 2010-05-17
Still didn't help..

---

### Post by Bucky Ball on 2010-05-18
Pulse working fine for me on 8.04. Beautiful in fact. Read this, post #8:

[http://ubuntuforums.org/showthread.php?t=1478754](http://ubuntuforums.org/showthread.php?t=1478754)

---

### Post by zbyszek26104 on 2010-05-19
I found that "solution":

[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

But I don't have so many options in "System -> Preferences -> Sound". It's totally different :(

---

### Post by Slex on 2010-05-19
> **soltanis said:**
> Didn't read the whole thread but it sounds like the solution is to UNINSTALL PULSEAUDIO.

```

sudo apt-get purge pulseaudio
sudo apt-get install alsa-utils alsa-base
sudo dpkg-reconfigure linux-sound-base # and make sure ALSA is selected
sudo reboot

```Solved the problem for me pretty quickly.

Seriously why do we keep pushing the extremely broken, extremely useless Pulseaudio package? It simply doesn't work. Until it does, it has no business being the default audio server in a supposedly stable distribution.

It did the job for me. I had tried all the other proposed solutions in this thread but with no success. It just seems that Acer laptops and Pulse audio on Ubuntu don't get along very well.

---

### Post by zbyszek26104 on 2010-05-19
Ah, but on Asus PulseAudio still doesn't work..

---

### Post by velko on 2010-05-20
Guys I found it!

I am with lucid (10.04) and with the padevchooser apt package installed and 

sudo apt-get install linux-alsa-driver-modules-$(uname -r)

and FINALLY going into the padevchooser > volume > input devces section and unmuting the mic with the red buton - it now works... D..n it!

I am not sure if the linux-alsa-driver-modules-$(uname -r) package helped - test 1st ommiting this step.

Long version for beginners:

sudo apt-get install padevchooser

launch padevchooser with krunner (Alt+F2) or the start menu (search there for pulse ).

Then go click the little black icon with a jack in the Tray - choose Volume Control > Input devices (4th tab or so) - click on the red button to unmute your mic.

No changes in skype needed.

Then do a skype test call (search in skype users for echo123 or "test")

if not ok - install the linux-alsa-driver-modules-$(uname -r) with


sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update (sudo remembers prev usage for 15 min so really not needed here)
sudo apt-get install linux-alsa-driver-modules-$(uname -r)


End of story for me.

Thanks all.


Going back to my exciting work [COLOR="Blue"]with [The #1 Wordpress Theme Generator. Instantly (< 5 min) create great looking and professional Wordpress Themes.](http://click.linksynergy.com/fs-bin/click?id=mQdtww1Dp4k&offerid=173675.10000002&type=3&subid=0" )
[IMG]http://ad.linksynergy.com/fs-bin/show?id=mQdtww1Dp4k&bids=173675.10000002&type=3&subid=0[/IMG][/COLOR]

---

### Post by Bucky Ball on 2010-05-20
Don't forget, if sound is not coming out of the desired device, start your sound app (Pulse, a music player, Firefox, whatever you are trying to listen to sound with) open Pulse Volume Control and the audio stream should be showing there in Playback Streams. Right click it and 'Move Stream ...'. Pick your device.

This way you can have, for instance, Skype through your USB headset, Firefox through your speakers, whatever you happen to have set up and available.

Good to hear it's all happening. ;)

---

### Post by zbyszek26104 on 2010-05-22
Still didn't help... :( I've tried everything

---

### Post by Bucky Ball on 2010-05-23
> **zbyszek26104 said:**
> Still didn't help... :( I've tried everything

Try running through the steps in the two links in post #8 on this thread:

[http://ubuntuforums.org/showthread.php?t=1478754](http://ubuntuforums.org/showthread.php?t=1478754)

---

### Post by myrandomstuff on 2010-05-31
ok just got my skype working - try checking cross checking your gstreamer-properties and your sound prefs for the mic - then run test calls - worked for me

---

### Post by ticket on 2010-06-27
Try this - worked for me:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359)

but with a slight difference:

  install linux-backports-modules-alsa-lucid-generic and reboot.

(ie. lucid, not karmic, as I am using lucid).

I had previously upgraded from karmic to lucid (didn't do a fresh install of lucid). The problem might not arise on a fresh lucid install.

I have a P7P55D EVO motherboard.

---

