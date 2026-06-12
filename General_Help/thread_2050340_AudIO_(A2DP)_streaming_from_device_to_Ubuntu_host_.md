---
title: "AudIO (A2DP) streaming from device to Ubuntu host using ALSA"
date: 2012-08-30
forum: General Help
---

### Post by pbarrantes on 2012-08-30
Hi,

I've succeeded streaming audio from my Android device to my Ubuntu 12.04 host PC with the help of Pulseaudio. I needed to do this using command line commands only (i.e. no UI helpers), since the next step is to make this on an embedded system. 

These are the steps I followed in case they are useful:

A) Edit /etc/bluetooth/audio.conf and add 
```

Enable=Source

```
on the General section (read somewhere that if this fails Enable=Socket might work).

B) Pair device using:
```

hcitool dev -> Get your bluetooth device <BT_DEV>
hcitool scan ->Get your device MAC Address
bluez-simple-agent <BT_DEV> XX:XX:XX:XX:XX:XX -> where XX:XX:XX:XX:XX:XX is the device MAC address

```NOTE: The previous steps stopped working after a while (still working on my embedded system), I'm still trying to figure out why. This is the output I get:

```

RequestConfirmation (/org/bluez/955/hci0/dev_XX_XX_XX_XX_XX_XX, 357756)
Confirm passkey (yes/no): yes
Release
Creating device failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```Anyway, after setting up the device with blueman (sudo apt-get install blueman) the next steps still work.

C) Configure the Android device to use your Ubuntu host for media media audio (On an HTC One X go to Settings->Bluetooth->Select your device->Select Use for media audio.

D) Get your bluetooth device object path. You can get this from the output on step B or use:
```

ADAPTER=`dbus-send --print-reply --system --dest=org.bluez / org.bluez.Manager.DefaultAdapter | cut -d'"' -f 2 | grep org`

DEVICE_PATH=`dbus-send --system --dest=org.bluez --print-reply $ADAPTER org.bluez.Adapter.ListDevices | grep path | cut -d'"' -f 2`

```E) Connect your device as an audio source
```

dbus-send --print-reply --system --dest=org.bluez $DEVICE_PATH org.bluez.AudioSource.Connect

```F) Get bluez audio source and ALSA audio sink
```

SOURCE=`pacmd list-sources | grep bluez | grep card | cut -d"<" -f2`
SINK=`pacmd list-sinks | grep alsa | grep card | grep pci | cut -d"<" -f2` (NOTE: This one might not work on your side, use list-sinks and look for yours)

```G) Connect bluez audio source to alsa output
```

ID=`pactl load-module module-loopback source=$SOURCE sink=$SINK`

```H) Play some audio on the mobile device and listen on the speakers

I) Stop playback
```

pactl unload-module $ID

```J) Disconnect from audio source:
```

dbus-send --print-reply --system --dest=org.bluez $DEVICE_PATH org.bluez.AudioSource.Disconnect

```Now, I would like to do this using ALSA only. I tried doing it going through steps A to E and then created/modified file /etc/asound.conf:

```

#/etc/asound.conf
pcm.btheadset {
    type plug
    slave {
        pcm {
            type bluetooth
            device XX:XX:XX:XX:XX:XX
            profile "auto"
        }   
    }   

    hint {
        show on
        description "BT Headset"
    }   
}

ctl.btheadset {
  type bluetooth
}

```but when I do

```

arecord -D btheadset test.wav

```I get:
```

Recording WAVE 'test.wav' : Unsigned 8 bit, Rate 8000 Hz, Mono
ALSA lib pcm_params.c:2162:(snd1_pcm_hw_refine_slave) Slave PCM not usable
arecord: set_params:1059: Broken configuration for this PCM: no configurations available

```I've looked all around but apparently most people want to stream from the host to the device (headset model) and all posts are ~3 years old. Suggestions are very welcome

---

### Post by Lanzecki on 2012-12-09
I am trying to achieve the same result with varying levels of success.

One thing I have noticed is that I think your asound.conf is set up for a bluetooth output, not input. I have yet to find a way of configuring Bluez to output directly to Alsa (which is the holy grail that we are both seeking).

I managed to get a better quality result with PulseAudio using pacat as in this example [http://thelinuxexperiment.com/guinea-pigs/tyler-b/fix-pulseaudio-loopback-delay/ ]("http://thelinuxexperiment.com/guinea-pigs/tyler-b/fix-pulseaudio-loopback-delay/")

but it would be so nice to get rid of PA completely as it adds so much processing overhead to my somewhat underpowered Raspberry Pi.

---

