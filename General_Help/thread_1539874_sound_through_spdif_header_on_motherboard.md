---
title: "sound through s/pdif header on motherboard"
date: 2010-07-27
forum: General Help
---

### Post by e64462 on 2010-07-27
Specs
**Motherboard** - Intel DX58sO 
> [http://www.intel.com/products/desktop/motherboards/DX58SO/DX58SO-overview.htm](http://www.intel.com/products/desktop/motherboards/DX58SO/DX58SO-overview.htm)
**Graphics Card** - nVIDIA gtx 280 
> [http://www.nvidia.com/object/product_geforce_gtx_280_us.html](http://www.nvidia.com/object/product_geforce_gtx_280_us.html)

I'm trying to get audio through the speakers on my monitor. The monitor is connected to the DVI port of my graphics card through a DVI-HDMI adapter. As you can see, both of the products I've linked suggest that audio over hdmi is possible. I have the appropriate cable running from the header on my motherboard to the pins on my graphics card, but I need help telling Ubuntu to send audio to the speakers on my monitor.

I believe I've found the relevant output device using the "aplay" command. That output is:

> nick@desktop:~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
[B]iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889 Digital
    IEC958 (S/PDIF) Digital Audio Output[/B]

I don't know if it's relevant, but more aplay output:
> nick@desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So I proceeded to:
> Applications->Preferences->Sound->Hardware Tab
and tried each option containing "IEC958". There are several, so I'll list them here:
> Digital Stereo (IEC958) Input
Digital Stereo Duplex (IEC958)
Digital Stereo (IEC958) Output + Digital Stereo (IEC958) Input
Digital Stereo (IEC958) Output + Analog Stereo Input
I have no idea why there are so many devices listed. I've also verified that the "S/PDIF" and "S/PDIF Default PCM" channels in alsamixer are not muted. But none of this resulted in sound through my monitor's speakers. Please help?

Other relevant output
> nick@desktop:~$ uname -r
2.6.32-24-generic
> nick@desktop:~$ lsb_release -r
Release:	10.04
> nick@desktop:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Jul 29 2010 for kernel 2.6.32-24-generic (SMP).
> nick@desktop:~$ nvidia-settings -t -q NvidiaDriverVersion
256.35

---

### Post by e64462 on 2010-07-27
I just booted in to windows and verified that all cables and headers are configured appropriately. It wasn't much easier to get things working in Windows, but after some tinkering I got audio to come through the monitor's speakers. 

Windows was insanely buggy though. Windows has "test" buttons built in to the guis, which play sounds. When I would test certain settings, like the supported formats, audio would completely break. To get it working again I had to use the test button with a specific format (which didn't work, i don't recall it's name), and then test Dolby Digital (which did work), and afterwards sound would function normally again. But if I went and tested certain settings again I'd have to repeat the whole process. 

I doubt it's relevant to the Ubuntu issues, but it did make me wonder.

also, bump.

---

### Post by e64462 on 2010-07-27
I installed "paman" to see if it offered any more configuration utilities. I don't know how to interpret this, but the "Output Devices" tab indicates that audio is being played. The indicator bar lights up whenever a song is played, but still no audio through the monitor's speakers. I've attached a screenshot.

---

### Post by rubylaser on 2010-07-27
You probably need to umute your S/PDIF in alsmixer. Open a terminal and type
```
alsamixer
```
Unmute all iec and spdif (Hit **m** so they turn green)

[IMG]http://img191.imageshack.us/img191/5182/alsanew.jpg[/IMG]
This is not my image, so excuse the Windows Putty window :)

Hope that helps.

---

### Post by e64462 on 2010-07-27
Thanks for the reply, but I've already confirmed that both the "S/PDIF" and "S/PDIF Default PCM" channels are not muted in alsamixer. The screenshot is of my alsamixer. 

Do you have any other suggestions?

---

### Post by e64462 on 2010-07-27
bump

---

### Post by e64462 on 2010-07-27
bump

---

### Post by Moixer on 2010-07-27
i'm experiencing similar problems with my Intel HDA realtek ALC889 spdif don't work i already ran the upgrade script from alsa everything is the same problem, alsamixer unmuted bars on paman move, the only sound output i get is from my mic output its very strange

---

### Post by e64462 on 2010-07-27
I haven't yet manually updated alsa, I was waiting to see if anybody thought it would help. Digital audio output through S/PDIF did work on previous versions of Ubuntu, I want to say 9.04 (but I'm not sure). I don't think pulseaudio was completely integrated in that release though; so I was thinking about disabling pulse.

---

### Post by e64462 on 2010-07-28
bump

---

### Post by e64462 on 2010-07-28
bump

Somebody out there has to know how to debug alsa / pulseaudio.

---

### Post by e64462 on 2010-07-28
bump

---

### Post by e64462 on 2010-07-29
bump

---

### Post by e64462 on 2010-07-29
I've now tried everything. I updated the nVIDIA drivers. I've completely removed pulseaudio. I've upgraded alsa using the alsa upgrade script. I've tried half a dozen different config hacks/patches/what-have-you. I've restarted an untold number of times. I've done it  all without any music to soothe my savage rage; and I still don't even get a crack or a pop out of the speakers when I test them. Is there literally no one with even the smallest of suggestions?

---

### Post by rubylaser on 2010-07-29
You could try to see if you could get it to work for you like this.
Open ~/.asoundrc in a text editor (create the file if it doesn't exist) and add the following:

**note: make sure to use the correct card/device id and replace 'pcm "hw:0,1"' with it. You can find the id's by typing 'aplay -l' in a terminal.**
```
pcm.dmixer {
    type dmix
    ipc_key 1024
    slave {
        pcm [COLOR="Red"]"hw:0,1"[/COLOR]
        period_time 0
        period_size 1024
        buffer_size 8192
        #periods 128
        #rate 44100
        rate 48000
     }
     bindings {
        0 0
        1 1
     }
}
```

I'd don't if that will help, but you asked for ideas, so you got one :)

Also, is your user a member of the audio group?
```
$ groups
adm dialout cdrom [COLOR="Red"]audio[/COLOR] video plugdev mythtv lpadmin
```

If not, you'll need to add yourself, or you'll never hear a peep.
```
sudo usermod -a -G audio your_user_name
```

---

### Post by e64462 on 2010-07-29
Thanks again for the reply!

First, the output of "aplay -l"
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR="Red"]card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/COLOR]

Then I created ~/.asoundrc. Its contents are:
> pcm.dmixer {
    type dmix
    ipc_key 1024
    slave {
        pcm "[COLOR="Red"]hw:0,1[/COLOR]"
        period_time 0
        period_size 1024
        buffer_size 8192
        #periods 128
        #rate 44100
        rate 48000
     }
     bindings {
        0 0
        1 1
     }
}

Do I leave "hw:0,1" like that, or do I replace "hw" with "iec958" so that it reads "iec958:0,1"?

If the problem were solved by something as simple as my user not being a member of the "audio" group, I would have literally kicked myself in the face. As it turns out, my user was not a member. So I added it, and logged back in... but nothing changed. Why would I need to add my user to the audio group if I got output through the analog device?

---

### Post by e64462 on 2010-07-30
bump

---

### Post by rubylaser on 2010-07-30
In your case, since it's Subdevice #0: subdevice #0, it would be 
```
pcm "hw:0,0"
```

---

### Post by e64462 on 2010-07-30
well, it's added.. but i'm not sure how to utilize the changes.

---

### Post by e64462 on 2010-08-03
bump

---

### Post by e64462 on 2010-08-12
bump

---

### Post by e64462 on 2010-08-18
bump

---

### Post by xubuntu84 on 2010-12-28
> **e64462 said:**
> Thanks again for the reply!

First, the output of "aplay -l"


Then I created ~/.asoundrc. Its contents are:


Do I leave "hw:0,1" like that, or do I replace "hw" with "iec958" so that it reads "iec958:0,1"?

If the problem were solved by something as simple as my user not being a member of the "audio" group, I would have literally kicked myself in the face. As it turns out, my user was not a member. So I added it, and logged back in... but nothing changed. Why would I need to add my user to the audio group if I got output through the analog device?

Did you ever get this to work?  I'm having the same issue... anybody out there alsa smart enough to help out? My "media center" ubuntu computer will turn into a windows 7 media center in about a week if I can't figure this thing out.  It's really frustrating because I love using Linux, just never have had to mess with trying to get sound to work over spdif.

---

### Post by e64462 on 2010-12-31
> **benmctee said:**
> Did you ever get this to work?  I'm having the same issue... anybody out there alsa smart enough to help out? My "media center" ubuntu computer will turn into a windows 7 media center in about a week if I can't figure this thing out.  It's really frustrating because I love using Linux, just never have had to mess with trying to get sound to work over spdif.

Apologies friend, I exhausted every avenue of support, and not a whisper or a fart from anyone.

I did file a bug report, which received no attention; maybe if you reported similar issues we could get someone to at least acknowledge the problem. Here's the link. Best of luck.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/611521](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/611521)

---

### Post by xubuntu84 on 2011-01-01
Subscribed and reported that it affects me as well.

Although, after reading through it I realized that you are trying to get audio out via your HDMI cable.  I guess I missed that from you forum post.  I'm attempting to get it over TOSLINK (sp?), the fiber cable.

I've attempted to install a sound card (Soundblaster xFI) that also has optical out with same results.  It seems my .asoundrc settings need to be changed, but I'm not sure to what.

---

### Post by e64462 on 2011-01-01
> **benmctee said:**
> Subscribed and reported that it affects me as well.

Although, after reading though it I realized that you are trying to get audio out view your HDMI cable.  I guess I missed that from you forum post.  I'm attempting to get it over TOSLINK (sp?), the fiber cable.

I've attempted to install a sound card (Soundblaster xFI) that also has optical out with same results.  It seems my .asoundrc settings need to be changed, but I'm not sure to what.
Yeah, unfortunately I can't help you much with that either. I plan to upgrade to 10.10 tonight or tomorrow, if anything changes for me I'll report it here. Needless to say that at this point I'm not holding my breath; this doesn't seem to be a priority for anyone of particular note.

---

