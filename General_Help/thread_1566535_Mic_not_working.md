---
title: "Mic not working"
date: 2010-09-02
forum: General Help
---

### Post by Tinya_Fair on 2010-09-02
Hello, i have Ubuntu lucid lynx and I cannot get my mic to work. I have done many things like installed pulse and gnome volume control, i have also upgraded my audio drivers.
The audio card i have is a realtec. This is bugging me because i was able to get my fiancee`s mic working, but still having trouble with mine.

Only ubuntu iso works on my laptop, so i am unable to try another one.

---

### Post by akoskm on 2010-09-02
> **Tinya_Fair said:**
> Hello, i have Ubuntu lucid lynx and I cannot get my mic to work. I have done many things like installed pulse and gnome volume control, i have also upgraded my audio drivers.
The audio card i have is a realtec. This is bugging me because i was able to get my fiancee`s mic working, but still having trouble with mine.

Only ubuntu iso works on my laptop, so i am unable to try another one.

Try to test it with
```

arecord -d 5 somefile

```, then
```

aplay somefile

```.

---

### Post by Tinya_Fair on 2010-09-02
It will not play back, i am very confused as to why. 
Could it be that my mic does not work?

---

### Post by akoskm on 2010-09-02
> **Tinya_Fair said:**
> It will not play back, i am very confused as to why. 
Could it be that my mic does not work?

If there was no sound while you played the *somefile*, there is definitely no recording.
Have checked your mic settings in *System > Preferences > Sound, Input* tab. Since it is a laptop you have one or more Connector available, please check them one by one.
Which hardware is selected in the *Hardware* tab?

---

### Post by Tinya_Fair on 2010-09-02
In the Input there is only one called internal audio analog stereo, and that is unmuted.
In the hardware tab it says internal audio 1 output/ 1 input Analog Stereo Duplex

---

### Post by akoskm on 2010-09-02
> **Tinya_Fair said:**
> In the Input there is only one called internal audio analog stereo, and that is unmuted.
In the hardware tab it says internal audio 1 output/ 1 input Analog Stereo Duplex

Internal Audio Analog Stereo as input, now that's gonna be interesting! :D

---

### Post by Tinya_Fair on 2010-09-02
it is

---

### Post by akoskm on 2010-09-02
> **Tinya_Fair said:**
> it is

Is your output working?
What is the output of
```

lspci | grep Audio

```?
What is your sound server?

---

### Post by coolman98 on 2010-09-02
alsamixer should work.

---

### Post by gypsumwolf on 2010-09-02
**->** What I did to get mine to work is quite simple, look at this thread: [http://ubuntuforums.org/showthread.php?t=1566070]("http://ubuntuforums.org/showthread.php?t=1566070")

**Note: **You may just need to install the *_xfce4-mixer_* and set the "*_In-Gain_*" there if you want to keep Ubuntu-Desktop.

**->** Actually I will quote myself here:
> 
**Solved!:**

**1)** Installed "*_Xubuntu 10.04_*" instead of "*_Ubuntu 10.04_*".

**2)** Installed "*_Sound Recorder_*" for testing purposes.

**3)** Clicked on speaker icon next to the clock in upper XFCE panel to bring up "*_Mixer_*", with Sound Card: "*_VIA VT1708 8-Ch (OSS Mixer)_*" selected, click "*_Select Controls..._*" and check "*_In-gain_*".

**4)** I turned the *_In-gain_* all the way up, tested it with "*_Sound Recorder_*"and it works perfectly!

---

### Post by akoskm on 2010-09-02
Sure! Check your Capture channels in alsamixer.
After starting it, hit F4 to see the capturing channels.

---

### Post by Tinya_Fair on 2010-09-02
xubuntu doesn`t work on my laptop

the sound is this 00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

il try F4 right now

---

### Post by NoNameWill on 2010-09-02
I had to turn down the input volume to get my mic to work. Seems by default it was set to high and cutting out the mic.

---

### Post by Tinya_Fair on 2010-09-02
The input level for the mic does not move, its like theres nothing there.

---

### Post by akoskm on 2010-09-02
Here is a screenshot about my alsamixer:
[http://imagebin.org/112445]("http://imagebin.org/112445").
If the input level isn't moving try to move the Input level over the Unamplified mark, and in alsamixer too.

---

### Post by Tinya_Fair on 2010-09-03
My gnome alsa mixer looks a lot different than the one you are using.

---

### Post by akoskm on 2010-09-03
> **Tinya_Fair said:**
> My gnome alsa mixer looks a lot different than the one you are using.

It isn't the gnome-alsamixer, this is the default one. Open a Terminal window and start it with:
```

alsamixer

```.

---

### Post by Tinya_Fair on 2010-09-03
Alsamixer cannot be found in my terminal.

---

### Post by akoskm on 2010-09-03
> **Tinya_Fair said:**
> Alsamixer cannot be found in my terminal.
```

sudo aptitude install alsa-utils

```

---

### Post by Tinya_Fair on 2010-09-03
I got one bar to start moving on the input in sound preferences; however i dont see input in alsa

---

