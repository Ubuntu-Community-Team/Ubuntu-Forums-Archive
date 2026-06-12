---
title: "No sound on a hp pavilion dv4-2114br (brazilian version)"
date: 2011-02-08
forum: General Help
---

### Post by gverrilla on 2011-02-08
Hey guys.
I reinstalled ubuntu,after a couple of years without it.As I couldn't make a new post (don't ask my why) on the 64 bit section,I'm trying it here.Hope I can get some help.
Well,I have spent nearly 5 hours searching on google and here to try and fix my sound problem,without success.
There was nothing about my particular pavilion,so I've tried a lot of things (which always make me feel bad when they are not successful,cause I imagine,as I am a newbie,I could be causing more problems with these failures) from other pavilions.
I remember trying everything I could with PulseAudio,ALSA,and I tried some stuff on the terminal too, adding the model=dv-4 thing.
nothing.
the thing is the system reads sounds (pulse audio meters read it), but it's not coming out loud on the external speakers.I don't have a headphone available to test right now.
Well,I thought the best way to help you guys help me would be to post my terminal history(first is newer):

aplay /usr/share/sounds/alsa/front_left.wav
(this I was using for testing)
gksudo gedit /etc/modprobe.d/alsa-base.conf
gksudo gedit /etc/modprobe.d/alsa-base
gksudo gedit /etc/modprobe.d/sound


The readouts:
sound
```
options snd-hda-intel enable-msi=1
model=hp-dv4
```

alsa-base
```
options snd-hda-intel enable_msi=1
options snd-hda-intel enable-msi=1
options snd-hda-intel enable-msi=1
options snd-hda-intel enable-msi=1
model=hp-dv4
```

alsa-base.conf
```
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv4
```


I know you guys will need more info,but ask me,cause I don't know what they are.
Thanks alot for any possible help.
Oh.well.there is something else.I installed ubuntu it has been like 15 days,and I used for a couple of hours.Then I went again onto it just yesterday.I may be wrong,but I think sound was working before some updates.
Oh,also there is a problem with playback (yes,i can open a video or audio file) : it is accelerated. Every real second contains 3 seconds more or less,it's strange.


;)

---

### Post by gverrilla on 2011-02-08
bump

---

### Post by gverrilla on 2011-02-08
nobody? :(

---

### Post by gverrilla on 2011-02-10
really ~
:(

---

### Post by gverrilla on 2011-02-12
come on guys,please
bump

---

### Post by gverrilla on 2011-02-13
bump

---

### Post by devildoc5 on 2011-02-13
same problem, different HP...Let me know if anyone comes along that can help....

---

### Post by gverrilla on 2011-02-15
Bump

---

### Post by gverrilla on 2011-02-17
bump ~

---

### Post by gverrilla on 2011-02-19
no one is able to help,really :( ~

---

### Post by gverrilla on 2011-02-21
ya

---

### Post by gverrilla on 2011-03-09
may I try another bump ~

---

### Post by gverrilla on 2011-03-19
twersdfsdf

---

### Post by gverrilla on 2011-03-30
84

---

### Post by gverrilla on 2011-04-03
wad

---

### Post by lidex on 2011-05-01
Should have posted in multimedia. See this page:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing)

---

### Post by gverrilla on 2011-08-22
that link ain't working mate
would be really grateful if you could help me
thanks alot

---

### Post by lidex on 2011-08-22
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by gverrilla on 2011-08-26
Hi mate,

the link is:
[http://www.alsa-project.org/db/?f=ac9b97a36d0885c810879e217f98a36e9440041e](http://www.alsa-project.org/db/?f=ac9b97a36d0885c810879e217f98a36e9440041e)

As I have noticed, but may most probably be wrong, alsa refers only to sound. My video ain't working too: it's going really really fast, like 3x normal.

Hope you can help me.

Thanks a lot.

---

### Post by lidex on 2011-08-28
> **gverrilla said:**
> Hi mate,

the link is:
[http://www.alsa-project.org/db/?f=ac9b97a36d0885c810879e217f98a36e9440041e](http://www.alsa-project.org/db/?f=ac9b97a36d0885c810879e217f98a36e9440041e)

As I have noticed, but may most probably be wrong, alsa refers only to sound. My video ain't working too: it's going really really fast, like 3x normal.

Hope you can help me.

Thanks a lot.

Try removing all the cruft from alsa-base.conf
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Now remove every line beginning with 
```
options snd-hda-intel
```
Add this line at the bottom:
```
options snd-hda-intel model=ref
```
Save. Close. Reboot.

---

### Post by gverrilla on 2011-08-29
> **lidex said:**
> Try removing all the cruft from alsa-base.conf
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Now remove every line beginning with 
```
options snd-hda-intel
```
Add this line at the bottom:
```
options snd-hda-intel model=ref
```
Save. Close. Reboot.

thanks for the fast reply lidex, but it ain't working
i've done what you told with sudo
and tried it on youtube as well as movie player(mp3)
the playback is really fast. It goes throught the song/movie, but faster then it should, and there is no sound
of course i've checked if mute was on

hope you have some more ideas
thanks a lot, once more

---

### Post by lidex on 2011-08-29
OK. Remove ref and replace with this:
```
hp-dv5 enable_msi=1
```

It should now look like:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

---

### Post by gverrilla on 2011-08-30
Not yet :(

---

### Post by lidex on 2011-08-30
> **gverrilla said:**
> Not yet :(

Post your amixer output:
```
amixer
```

---

### Post by gverrilla on 2011-08-30
There you go.
Thanks once more for helping me.

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 41 [64%] [-17.25dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Bass Speaker',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 252 [99%] [0.60dB]
  Front Right: Playback 252 [99%] [0.60dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'Digital Playback' 'Analog Mux 1' 'Analog Mux 2'
  Item0: 'Digital Playback'
Simple mixer control 'IEC958 Playback Source',1
  Capabilities: enum
  Items: 'Digital Playback' 'Analog Mux 1' 'Analog Mux 2'
  Item0: 'Digital Playback'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 13 [87%] [19.50dB] [off]
  Front Right: Capture 13 [87%] [19.50dB] [off]
Simple mixer control 'Digital Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]

```

---

### Post by lidex on 2011-08-30
That looks good. No sound at all?
Let's see an updated alsa-info.```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```

---

### Post by gverrilla on 2011-08-31
Hi.
That's what I got from typing in that cmd line you just sent.
Will now restart and try it out.

```
lupus@lupus-HP-Pavilion-dv4-Notebook-PC:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2011-08-31 13:47:49--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-08-31 13:47:52--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [   <=>                                 ] 27,247      50.2K/s   in 0.5s    

2011-08-31 13:47:53 (50.2 KB/s) - `alsa-info.sh' saved [27247]

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base line 5: ignoring bad line starting with 'model=hp-dv4'
WARNING: /etc/modprobe.d/sound.conf line 2: ignoring bad line starting with 'model=hp-dv4'
ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base line 5: ignoring bad line starting with 'model=hp-dv4'
WARNING: /etc/modprobe.d/sound.conf line 2: ignoring bad line starting with 'model=hp-dv4'
J


Your ALSA information is in /tmp/alsa-info.txt.HpH3pkgufo

lupus@lupus-HP-Pavilion-dv4-Notebook-PC:~$ 


```

---

### Post by gverrilla on 2011-08-31
I have just rebooted, and nothing seems to have changed.
Though the title of the topic is "no sound", my video playback is with problems aswell. It goes like 6 times faster, and with no sound too.
Any ideas ?
Thanks a lot for the tries.

PS: the audio playback is as fast as the video too

---

### Post by lidex on 2011-08-31
What is this output:
```
ls /etc/modprobe.d/
```
Please post using code tags.

---

### Post by gverrilla on 2011-09-01
```
lupus@lupus-HP-Pavilion-dv4-Notebook-PC:~$ ls /etc/modprobe.d/
alsa-base               blacklist.conf              blacklist-oss.conf
alsa-base.conf          blacklist-firewire.conf     blacklist-rare-network.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist-bcm43.conf    blacklist-modem.conf        sound.conf
lupus@lupus-HP-Pavilion-dv4-Notebook-PC:~$ 
```

there you go
blacklist-oss.conf is bold-blue.

;_)

---

### Post by lidex on 2011-09-01
Fire up a terminal and change directory:
```
cd /etc/modprobe.d/
```
Now remove uneeded files:
```
sudo rm alsa-base sound.conf
```
Reload alsa:
```
sudo alsa force-reload
```

---

### Post by gverrilla on 2011-09-02
output was:
```
lupus@lupus-HP-Pavilion-dv4-Notebook-PC:~$ cd /etc/modprobe.d/
lupus@lupus-HP-Pavilion-dv4-Notebook-PC:/etc/modprobe.d$ sudo rm alsa-base sound.conf
[sudo] password for lupus: 
Sorry, try again.
[sudo] password for lupus: 
lupus@lupus-HP-Pavilion-dv4-Notebook-PC:/etc/modprobe.d$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lupus/.gvfs
      Output information may be incomplete.
Terminating processes: 1461lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lupus/.gvfs
      Output information may be incomplete.
 6496lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lupus/.gvfs
      Output information may be incomplete.
 6513lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lupus/.gvfs
      Output information may be incomplete.
 6528lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lupus/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 6543lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lupus/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 6559(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lupus/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 6559(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
lupus@lupus-HP-Pavilion-dv4-Notebook-PC:/etc/modprobe.d$ 


```

brb, booting

---

### Post by gverrilla on 2011-09-02
same :/

---

### Post by lidex on 2011-09-02
> **gverrilla said:**
> same :/

OK. Remove the model line from alsa-base.conf and replace with this block:
```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 enable_msi=1

```
Save. Close. Reboot.

---

### Post by gverrilla on 2011-09-03
not yet mate
I changed, rebooted, and nothing
event tried the force-reload once more,rebooted again, but no success
seems to me hp is just anti-linux, somehow
hope we can find the answer
thanks

---

### Post by lidex on 2011-09-03
Since nothing yet added to alsa-base.conf seems to be working, return it do default by removing your edits. Run the script again for me please.
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by gverrilla on 2011-09-03
I have deleted those last 3 lines, and then runned the command you told me to. Here's the output:
[http://www.alsa-project.org/db/?f=3dff83d65d5e58df127b49ac4a7656004a260bb7](http://www.alsa-project.org/db/?f=3dff83d65d5e58df127b49ac4a7656004a260bb7)

PS: I did not reboot after deleting those lines,if that's ok

---

### Post by lidex on 2011-09-04
> **gverrilla said:**
> I have deleted those last 3 lines, and then runned the command you told me to. Here's the output:
[http://www.alsa-project.org/db/?f=3dff83d65d5e58df127b49ac4a7656004a260bb7](http://www.alsa-project.org/db/?f=3dff83d65d5e58df127b49ac4a7656004a260bb7)

PS: I did not reboot after deleting those lines,if that's ok

No, sorry, you really have to reboot or reload alsa for the changes to take effect. Alsa-info still shows the dell-m4-1 model.

---

### Post by gverrilla on 2011-09-04
:tongue:
sorry, there you go.

reload:
```
lupus@lupus-HP-Pavilion-dv4-Notebook-PC:~$ sudo alsa force-reload[sudo] password for lupus: 
Sorry, try again.
[sudo] password for lupus: 
Sorry, try again.
[sudo] password for lupus: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lupus/.gvfs
      Output information may be incomplete.
Terminating processes: 1446lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lupus/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lupus/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/lupus/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-atihdmi snd-hda-codec-idt snd-seq-midi snd-rawmidi snd-hda-intel snd-seq-midi-event snd-hda-codec snd-hwdep snd-seq snd-pcm snd-seq-device snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-atihdmi snd-hda-codec-idt snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-atihdmi snd-hda-codec-idt snd-seq-midi snd-rawmidi snd-hda-intel snd-seq-midi-event snd-hda-codec snd-hwdep snd-seq snd-pcm snd-seq-device snd-timer snd-page-alloc.
lupus@lupus-HP-Pavilion-dv4-Notebook-PC:~$ 

```


output: [http://www.alsa-project.org/db/?f=6f756d2c321bf7605cfd686816c90506e282c155](http://www.alsa-project.org/db/?f=6f756d2c321bf7605cfd686816c90506e282c155)

---

### Post by gverrilla on 2011-09-09
lid ?

---

### Post by gverrilla on 2011-09-15
may I bump /

---

### Post by lidex on 2011-09-18
> **gverrilla said:**
> may I bump /

Sorry, was out of town. Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=ref" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by gverrilla on 2011-09-19
hi lidex!
sorry for insisting
thanks for returning
but not yet mate: it's still the same :/

---

### Post by gverrilla on 2011-09-24
bumpty

---

### Post by lidex on 2011-09-27
Try changing the ref model to this:
```
hp-dv4-1222nr
```

---

### Post by gverrilla on 2011-09-27
nothing yet :/

```
options snd-hda-intel model=hp-dv4-1222nr
```

---

### Post by lidex on 2011-09-27
OK. Remove that model name and replace with this:
```
enable_msi=1
```

Things we can look at here:
1. bios update
2. alsa upgrade - via the link in my sig

What are these outputs:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by gverrilla on 2011-09-29
heu lidex, it's "-", instead of "_", isn't it ?
these are the last 2 lines from alsa-base.conf right now:
```
options snd-usb-audio index=-2
options snd-hda-intel enable-msi=1
```

---

### Post by gverrilla on 2011-09-30
sorry, had a work emergency yesterday. there you go:

first output: ```
lupus@lupus-HP-Pavilion-dv4-Notebook-PC:~$ sudo dmidecode -t bios
[sudo] password for lupus: 
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Insyde
	Version: F.17
	Release Date: 12/10/2009
	ROM Size: 2048 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		Targeted content distribution is supported
	BIOS Revision: 15.23
	Firmware Revision: 40.35

```

---

### Post by gverrilla on 2011-09-30
second output:

```
lupus@lupus-HP-Pavilion-dv4-Notebook-PC:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
	Manufacturer: Hewlett-Packard
	Product Name: 3642
	Version: 40.23
	Serial Number: BRG008F8NV
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0016, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: Video Graphics Controller

Handle 0x0017, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: Realtek Lan Controller

```

---

### Post by Akilesh on 2011-10-02
Hi 
I have the same problem. I use an acer aspire 4750z. This is what i get
akilesh@Bantu:~$ aplay -l
aplay: device_list:217: no soundcards found...

lspci -v
00:1b.0 Audio device: Intel Corporation Device 1c20 (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 0506
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 90600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: oss_hdaudio

---

### Post by gverrilla on 2011-10-05
bumpalumpa

---

### Post by lidex on 2011-10-11
> **gverrilla said:**
> bumpalumpa

No, actually the module options use the underscore character.
Have you tried the suggestions from my last post?

---

### Post by gverrilla on 2011-10-11
> **lidex said:**
> No, actually the module options use the underscore character.

Did not understand this.


> **lidex said:**
> No, actually the module options use the underscore character.
Have you tried the suggestions from my last post?
Alsa and bios upgrade?
Thought you asked me those outputs in order to guide me through these processes.
As far as I remember, I have already upgraded alsa.
And I have no idea how to proceed to upgrade my bios.
Any help will be appreciated.
Sorry, I'm a lil lost now.

---

### Post by gverrilla on 2011-10-17
bumppa

---

### Post by gverrilla on 2011-10-24
:( :( :(

---

### Post by gverrilla on 2011-10-31
bump

---

### Post by gverrilla on 2011-11-06
I would hate to go back to windows :/

---

### Post by gverrilla on 2011-11-11
bump

---

### Post by gverrilla on 2011-11-16
bumpz

---

### Post by gverrilla on 2011-11-16
an update: I used hdmi cabble to connect to my tv, and there was sound. thanks

---

### Post by gverrilla on 2011-11-18
SOLVED
thanks a lot for the tries lidex, 11.10 xubuntu fixed it ;)

---

