---
title: "Joining channels to make multichannel (PLEASE DON'T IGNORE ME)"
date: 2009-11-27
forum: General Help
---

### Post by Dancefloor Innovators on 2009-11-27
I have a sound card with two separate mono channels that I want to merge into a single stereo channel. I found this article online:
[http://alsa.opensrc.org/index.php/.asoundrc#Joining_devices_to_make_multichannel](http://alsa.opensrc.org/index.php/.asoundrc#Joining_devices_to_make_multichannel)
...but it just left me even more confused. Someone please lend me a hand here. :(

```
**devices**
  2:        : timer
  3: [ 0- 0]: raw midi
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0]   : control
  7:        : sequencer

``````
**cards**
 0 [M1010LT        ]: ICE1712 - M Audio Delta 1010LT
                      M Audio Delta 1010LT at 0x1040, irq 21

``````
**modules**
 0 snd_ice1712

``````
**pcm**
00-00: ICE1712 multi : ICE1712 multi : playback 1 : capture 1

``````
**timers**
G0: system timer : 1000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
  Client application 22231 : running
P0-0-1: PCM capture 0-0-1 : SLAVE

``````
**version**
Advanced Linux Sound Architecture Driver Version 1.0.20.

``````
**ice1712**
M Audio Delta 1010LT at 0x1040, irq 21

EEPROM:
  Subvendor        : 0x12143bd6
  Size             : 29 bytes
  Version          : 1
  Codec            : 0x1f
  ACLink           : 0x80
  I2S ID           : 0x72
  S/PDIF           : 0x3
  GPIO mask        : 0x4
  GPIO state       : 0x7e
  GPIO direction   : 0xfb
  AC'97 main       : 0x0
  AC'97 pcm        : 0x0
  AC'97 record     : 0x0
  AC'97 record src : 0x44
  DAC ID #0        : 0x3
  DAC ID #1        : 0x3
  DAC ID #2        : 0x3
  DAC ID #3        : 0x3
  ADC ID #0        : 0x3
  ADC ID #1        : 0x3
  ADC ID #2        : 0x3
  ADC ID #3        : 0x3
  Extra #28        : 0x0

Registers:
  PSDOUT03         : 0x0000
  CAPTURE          : 0x00000000
  SPDOUT           : 0x0000
  RATE             : 0x00
  GPIO_DATA        : 0x5a
  GPIO_WRITE_MASK  : 0x04
  GPIO_DIRECTION   : 0xfb

``````
**id**
M1010LT

``````
**midi0**
M Audio Delta 1010LT MIDI

Output 0
  Tx bytes     : 0
Input 0
  Rx bytes     : 0


``````
**oss_mixer**
VOLUME "" 0
BASS "" 0
TREBLE "" 0
SYNTH "" 0
PCM "" 0
SPEAKER "" 0
LINE "" 0
MIC "" 0
CD "" 0
IMIX "" 0
ALTPCM "" 0
RECLEV "" 0
IGAIN "" 0
OGAIN "" 0
LINE1 "" 0
LINE2 "" 0
LINE3 "" 0
DIGITAL1 "IEC958" 0
DIGITAL2 "" 0
DIGITAL3 "" 0
PHONEIN "" 0
PHONEOUT "" 0
VIDEO "" 0
RADIO "" 0
MONITOR "" 0


```

---

### Post by HermanAB on 2009-11-27
Uhhhmmm, a stereo channel is simply two mono channels.

Maybe you should play with Sound Exchange (sox) on the command line to get a better grasp of things.  Google for sox:
[http://www.google.com/linux?hl=en&q=sox&btnG=Search](http://www.google.com/linux?hl=en&q=sox&btnG=Search)

---

### Post by Dancefloor Innovators on 2009-12-02
> **HermanAB said:**
> Uhhhmmm, a stereo channel is simply two mono channels.
I know that. The only problem is that ALSA is treating both left and right channels as two separate mono channels, NOT as one stereo channel like it should.

---

### Post by Dancefloor Innovators on 2009-12-03
Someone help me...

---

### Post by Dancefloor Innovators on 2009-12-05
```
**.asoundrc**
pcm.multi_capture {
	type multi
	slaves.a.pcm hw:0 
	slaves.a.channels 12
	slaves.b.pcm hw:1
	slaves.b.channels 12

# First 8 channels of first soundcard (capture)
 	bindings.0.slave a
 	bindings.0.channel 0
 	bindings.1.slave a
 	bindings.1.channel 1
 	bindings.2.slave a
 	bindings.2.channel 2
 	bindings.3.slave a
 	bindings.3.channel 3
 	bindings.4.slave a
 	bindings.4.channel 4
 	bindings.5.slave a
 	bindings.5.channel 5
 	bindings.6.slave a
 	bindings.6.channel 6
 	bindings.7.slave a
 	bindings.7.channel 7

# S/PDIF section. Uncomment bindings if required.

# S/PDIF first soundcard (capture)
 	#bindings.16.slave a
 	#bindings.16.channel 8
 	#bindings.17.slave a
 	#bindings.17.channel 9
}

ctl.multi_capture {
	type hw
	card 0
}

pcm.multi_playback {
	type multi
	slaves.a.pcm hw:0
	slaves.a.channels 10

# First 8 channels of first soundcard (playback)
 	bindings.0.slave a
 	bindings.0.channel 0
 	bindings.1.slave a
 	bindings.1.channel 1
 	bindings.2.slave a
 	bindings.2.channel 2
 	bindings.3.slave a
 	bindings.3.channel 3
 	bindings.4.slave a
 	bindings.4.channel 4
 	bindings.5.slave a
 	bindings.5.channel 5
 	bindings.6.slave a
 	bindings.6.channel 6
 	bindings.7.slave a
 	bindings.7.channel 7

# S/PDIF section. Uncomment bindings if required.

# S/PDIF first soundcard (playback)
 	#bindings.16.slave a
 	#bindings.16.channel 8
 	#bindings.17.slave a
 	#bindings.17.channel 9
}

ctl.multi_playback {
	type hw
	card 0
}
```
```

jackd 0.116.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... multi_playback|multi_capture|1024|2|48000|0|0|nomon|swmeter|-|32bit
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: no playback configurations available (Invalid argument)
ALSA: cannot configure capture channel
cannot load driver module alsa

```

What's wrong???

---

