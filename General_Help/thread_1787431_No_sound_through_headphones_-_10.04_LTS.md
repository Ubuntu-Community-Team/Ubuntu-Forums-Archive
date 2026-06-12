---
title: "No sound through headphones - 10.04 LTS"
date: 2011-06-21
forum: General Help
---

### Post by Bucky Ball on 2011-06-21
Hi all,

I have done a bit of a search for this and would normally do more but as I am on holiday and have just upgraded my mother in law's machine to 10.04 and only here tomorrow then back home (750Kms away) I am hoping the community can speed things up a little.

Open Pulse Volume Control and headset mic working because input meter shows it, plays audio cause output meter shows it, but the analogue headset headphones give me no sound. 

Please ask for any info. All seems to be working fine but just not getting through to headphones. This is with all apps (Skype, Totem).

Any ideas??? ;)

---

### Post by Bucky Ball on 2011-06-21
ps: I don't have speakers attached but there is analogue audio in and out mini-jacks on the front of this machine so that's where I would plug 'em if I did. So, this thread should really be titled, 'No sound through analogue audio out mini-jack socket'.

---

### Post by mastablasta on 2011-06-21
have you checked the sound levels in alsamixer?
 
alsamixer 
 
in terminal
 
also check that correct sound card is set for output. and check if any speakers work.

---

### Post by Bucky Ball on 2011-06-21
Checked all that. As I say, speakers would be plugged into same mini-jack output that the headphones are. All shows up in Pulse Volume Control, just nothing coming through headphones (although the meter is playing it faultlessly). 

Strange though as lspci gives me:

```
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
```... while I get this result from this command:

```
jo@GreenMachine:~$ cat /proc/asound/card*/codec#* | grep Codec
Codec: VIA VT1708B 8-Ch
```Wrong codec? Not sure how to approach this ... remove that VIA codec could be a start??? As I say, the meters tell me all is working fine 'out of the box' but I'm just not actually hearing anything. Can make a Skype call with no errors but just don't hear anything.

---

### Post by Bucky Ball on 2011-06-21
The plot thickens:

```
jo@GreenMachine:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Perhaps I need to add a line to '/etc/modprobe.d/alsa-base.conf' but not sure what. I'll keep furiously digging ...

---

