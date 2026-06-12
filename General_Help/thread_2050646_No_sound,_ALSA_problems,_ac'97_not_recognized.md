---
title: "No sound, ALSA problems, ac'97 not recognized"
date: 2012-08-31
forum: General Help
---

### Post by greatsirkain on 2012-08-31
Hi, no sound at all, checked the volume etc was at max, been trying for days to sort it out. I've been a windows user since 95 and learned to loath microsoft so any  response should be given as if you're talking to a retarded chipmunk  (seriously, I spent a whole day looking for the task manager). All of this started when I tried to fix the right speaker that wasn't  working (which still does using a live ubuntu cd) by updating alsa as indicated when I looked around the internet, I also  downloaded and installed all the latest releases from their site and  used synaptic to get everything alsa related, nothing has worked, if I  could afford to buy a new card (or even better a new pc) I would, I know  the sound is onboard, it's a Dell optiplex 7...something, slimline  version...annoying thing is I think I still have the soundmax.exe  drivers for windows on disk somewhere, sorry for the long post but any  help would be appreciated

Here's some details:
lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

aplay
ALSA lib confmisc.c:768:sad:parse_card) cannot find card '0'
ALSA lib conf.c:4184:sad:_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:sad:snd_func_concat) error evaluating strings
ALSA lib conf.c:4184:sad:_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:sad:snd_func_refer) error evaluating name
ALSA lib conf.c:4184:sad:_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4663:sad:snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2212:sad:snd_pcm_open_noupdate) Unknown PCM default
aplay: main:660: audio open error: No such file or directory
(note the above sad faces...Irony)

sudo lshw -C multimedia
*-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff

I tried:
                                  sudo nano /etc/modprobe.d/alsa-base
and adding this as the last line:
Code:
"options snd-intel8x0 ac97_quirk=3"
  along with various other things like purging ALSA reinstalling

sudo modprobe snd- (tab) displays 167 sound card drivers but mine isn't one of them

pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.


wmmixer
wmmixer : Unable to open mixer device /dev/mixer'.

alsamixergui: function snd_ctl_open failed: no such file or directory

---

### Post by greatsirkain on 2012-08-31
update
ubuntu 11.10
after manually downloading and going through the packages (wow was that boring) from ALSA I found "Downloads/alsa-driver-1.0.25/pci/ac97" but there isn't a config file I can click on or an install file that I could get at from the terminal, there's only:
ac97_codec.patch
ac97_id.h
ac97_proc.c
ac97_pcm.c
If I go back to the alsa-driver-1.025 file there's a config file, a INSTALL file and intall-sh file but apparently praying doesn't get alsa to load my driver, the install file is just text unlike other install files I have come across...I'm presuming install-sh is shell and thats what I'm looking for...clicking on it got me a text file, trying from terminal sudo...If I die I want you all to know it's your fault for not helping me sooner

edit:
nothing happened.
Downloads/alsa-driver-1.0.25$ sudo install-sh
sudo: install-sh: command not found
Downloads/alsa-driver-1.0.25$ sudo install
install: missing file operand
Try `install --help' for more information.
Downloads/alsa-driver-1.0.25$ sudo ./install
sudo: ./install: command not found
Downloads/alsa-driver-1.0.25$ sudo ./install-sh
sudo: ./install-sh: command not found
I then tried copying the text from install-sh into the terminal, the terminal just soiled itself and closed.....Help

edit 2: tried running all the configure files with geany then tried sudo modprobe snd- again, no ac97 there, am I looking for the right thing?....Help

---

### Post by greatsirkain on 2012-08-31
My Dear Beloved (Ubuntu community)

By the time you read this I will no longer be amongst the conscious having plunged myself into the sweet depths of a large bottle of port, had you at least acknowledged my bitter struggle against computer deafness I may have been able to bare this immense burden but, alas, t'is a burden no man can be asked to bare alone. So with a heavy heart, and a large *****, this was me Greatsirkain, just wanting to say I loved you.

sudo ./play_stevie_wonder_i_just_called_to_say_i_love_you 
error: No such file or directory

...bump...

furious edit:
aww c'monn??! Nobody know what stupid little thing I've done wrong? 108 views and not one opinion? not even 'have you checked your computer is plugged in?'  Do I really, with my tail between my legs and a hangover, have to go back to windows in the morning like some sort of ugly wife?! THE MOST annoying thing is that I already tried to load windows to hear the shrieks and moans on my adult entertainment (battlefield 3 vids) and because the powers that be decided having the firewall set to enabled as default was a bad idea I had to boot from a live disk (with no hardware drivers) because every single DLL is gone! SO I DONT HAVE SOUND ON WINDOWS EITHER....Seriously?....Really?

---

### Post by greatsirkain on 2012-08-31
....desperate bump....

---

### Post by BLuFeNiX on 2012-08-31
> **greatsirkain said:**
> 
furious edit:
aww c'monn??! Nobody know what stupid little thing I've done wrong? 108 views and not one opinion? not even 'have you checked your computer is plugged in?'  Do I really, with my tail between my legs and a hangover, have to go back to windows in the morning like some sort of ugly wife?! THE MOST annoying thing is that I already tried to load windows to hear the shrieks and moans on my adult entertainment (battlefield 3 vids) and because the powers that be decided having the firewall set to enabled as default was a bad idea I had to boot from a live disk (with no hardware drivers) because every single DLL is gone! SO I DONT HAVE SOUND ON WINDOWS EITHER....Seriously?....Really?


Please calm down. It hasn't even been a day yet. I am looking for a solution for you.

---

### Post by BLuFeNiX on 2012-08-31
please run this command and post the output:
```
echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done; echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done
```

---

### Post by greatsirkain on 2012-08-31
wellll, I figured being over dramatic was friendlier than typing loads of caps out of frustration...also...port wasn't a lie :P

[B]Sound cards recognized by the system:
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
Sound cards recognized by ALSA:
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
Sound cards recognized by ALSA, and activated:
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
[/B]
...if that's true why wont it let me access or change? It has a dummy output set up and I don't seem to have any control over it (also a day for you, a week plus before i realised i needed help, been trying on this for 60 plus hours
but thanks for the help....you deserve a kain hug, full of vitamins and love just without the gay

---

### Post by BLuFeNiX on 2012-08-31
> **greatsirkain said:**
> wellll, I figured being over dramatic was friendlier than typing loads of caps out of frustration...also...port wasn't a lie :P

[B]Sound cards recognized by the system:
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
Sound cards recognized by ALSA:
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
Sound cards recognized by ALSA, and activated:
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
[/B]
...if that's true why wont it let me access or change? It has a dummy output set up and I don't seem to have any control over it (also a day for you, a week plus before i realised i needed help, been trying on this for 60 plus hours
but thanks for the help....you deserve a kain hug, full of vitamins and love just without the gay

Haha =D

The output looks fine. Please run this command and post the output:
```
aplay -l
```

And just to be sure your groups are fine, run this: 
```
sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```

---

### Post by greatsirkain on 2012-08-31
aplay -l
device_list:240: no soundcards found...

---

### Post by BLuFeNiX on 2012-08-31
> **greatsirkain said:**
> aplay -l
device_list:240: no soundcards found...

okay run these commands and then reboot:
```
sudo apt-get install --reinstall libasound2
sudo dpkg-reconfigure pulseaudio
sudo dpkg-reconfigure alsa-base

```

If it says that something "is not installed", please install it with apt-get. If this doesn't at least change *something* then I'm not sure what to do next.

---

### Post by greatsirkain on 2012-08-31
nope still 'dummy output' but at least they're screaming in my ears..

---

### Post by BLuFeNiX on 2012-08-31
> **greatsirkain said:**
> nope still 'dummy output' but at least they're screaming in my ears..

What do you mean by that? They are producing sound?

---

### Post by greatsirkain on 2012-09-01
nope, it was just the static cos I'd turned my T.V volume up that loud hoping to hear something, still nothing but I appreciate your help, especially since I was 'a little tired' last night shall we say lol (waking up to static with a bad head is awesome)

---

### Post by pqwoerituytrueiwoq on 2012-09-01
after doing all that you probably have to reset the sound profile
```
rm -rf ~/.pulse
```logout and in and see what you have
how to use speaker-test if the  above did not get the job done
```
~$ aplay -l | grep card
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
card 0: SB [HDA ATI SB], device 2: VT1708S HP [VT1708S HP]
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
~$ speaker-test -c 2 -r 48000 -D hw:1,7
```the 1 and 7 are [card],[device]
try each one, till you hear sound (static playback)
when you found the combination that works
```
echo "load-module module-alsa-sink device=hw:[CARD],[DEVICE]" | sudo tee -a /etc/pulse/default.pa
```

---

### Post by BLuFeNiX on 2012-09-01
> **pqwoerituytrueiwoq said:**
> after doing all that you probably have to reset the sound profile
```
rm -rf ~/.pulse
```

Oh, good idea! I always seem to forget the little things...

---

### Post by greatsirkain on 2012-09-02
aplay -l | grep card
aplay: device_list:240: no soundcards found...


Playback device is hw:2,5
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Playback open error: -2,No such file or directory

and I got the same result for every combo I tried :(

---

### Post by greatsirkain on 2012-09-04
still messing around with it trying to get it working, something new cropped up:

$ pulseaudio
E: [pulseaudio] socket-server.c: bind(): Address already in use
E: [pulseaudio] module.c: Failed to load module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.


....Did I break something new? lol

Edit: ahh cheers

---

### Post by BLuFeNiX on 2012-09-04
> **greatsirkain said:**
> still messing around with it trying to get it working, something new cropped up:

$ pulseaudio
E: [pulseaudio] socket-server.c: bind(): Address already in use
E: [pulseaudio] module.c: Failed to load module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.


....Did I break something new? lol

That just means that pulseaudio is already running.

---

### Post by pqwoerituytrueiwoq on 2012-09-04
> **greatsirkain said:**
> aplay -l | grep card
aplay: device_list:240: **no soundcards found**...
that would explain why you have no sound
```
lspci | grep Audio
```

---

### Post by greatsirkain on 2012-09-04
reported from the live cd (where the sound kind of works)

```
aplay -l
```card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ubuntu@ubuntu:~$ 

```
lshw
``` *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff



HDD ubuntu

```
lspci -v | grep -A7 -i "audio"
```00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Dell Device 017a
    Flags: bus master, medium devsel, latency 0, IRQ 3
    I/O ports at ee00 [size=256]
    I/O ports at edc0 [size=64]
    Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
    Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>



```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```(in case I had broken anything)

```
sudo apt-get update
```reboot

...W're getting somewhere, now I have sound but only comming from the internal speakers, the sound is set up like that but it's supposed to mute and come out of the headphones as soon as you plug the jack in, right now no sound from the headphones from the front or rear jack...But it's recognizing the card now so I presume this is just a mixer problem...Last bit was a quick fix, the jack was out :D
Hmmmm, the left speakers seems a tin tin tiny bit louder than the right, any idea of a fix that doesn't involve having to change the balance? :P

Edit: P.S Thanks for the help, don't know about you  guys but I'm going to celebrate with a prolonged horizontal one man Mexican wave

---

