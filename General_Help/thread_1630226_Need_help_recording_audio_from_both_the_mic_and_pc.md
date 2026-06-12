---
title: "Need help recording audio from both the mic and pc at the same time."
date: 2010-11-24
forum: General Help
---

### Post by ivarn on 2010-11-24
Hello. I want to record conversations and stuff from skype.
Now, I want the sound to be as good as possible, so what settings do I choose, what do I mute and all the other volume combinations and settings do I configure etc...
To get the best record possible, I need to record from both pc and mic at the same time, but how? As my settings are now I can only record through the mic.
So, what do I do? 
Also, if you could give me a few tips on how I can filter useless background noise.
That would be great.
Thanks a lot in advance :)

---

### Post by ivarn on 2010-11-26
Bump

---

### Post by ivarn on 2010-11-28
bUUUUUUUMP

---

### Post by ivarn on 2010-11-29
Burp

---

### Post by matt_symes on 2010-11-29
Hi

Nice burp errr bump... :)

Does this help as a start? Using audacity.

[http://skypetips.internetvisitation.org/articles/record_skype_calls.html](http://skypetips.internetvisitation.org/articles/record_skype_calls.html)

[http://wiki.audacityteam.org/index.php?title=Noise_Removal](http://wiki.audacityteam.org/index.php?title=Noise_Removal)

[http://manual.audacityteam.org/index.php?title=Noise_Removal](http://manual.audacityteam.org/index.php?title=Noise_Removal)

[http://forum.audacityteam.org/viewtopic.php?f=28&t=442](http://forum.audacityteam.org/viewtopic.php?f=28&t=442)

Kind regards

---

### Post by ivarn on 2010-11-30
thanks a lot. the noise removal links were pretty helpful but the other two links for recording and input/output volume settings were for windows and mac.
Also I know how to record the calls but I will have the input/output and volume settings as good as possible to record both via pc and mic (input and output).

EDIT: Ok so to get both in and output I have to use Analogue Duples. But when I record from the moc using duples I only get the mic sound and not audio I play from the speakers.
So, how do I fix this?

---

### Post by ivarn on 2010-12-02
[FONT=Arial Black][SIZE=7]**_Bump!_**[/SIZE][/FONT]

---

### Post by Habitual on 2010-12-02
1. sudo apt-get install -y sox
2. Create this script:
```

#!/bin/bash
# Copyright 2008-2009, Kees Cook <kees@outflux.net>
#
# Records the PulseAudio monitor channel.
# http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/
#
#This script require sox
#sudo apt-get install sox

if [ -n "$1" ]; then
    OUTFILE="$1"
else
    TIME=$(date +%d-%b-%y_%H%M-%Z)
    OUTFILE="recording_$TIME.wav"
fi

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$OUTFILE"

# End of sound_cap.sh

```
3. chmod 700 script_name.sh
4. I used audacity to test this. I suggest you do the same.
5. open terminal
6. run "script_name.sh mic_check.wav" and in Audacity hit record and SPEAK INTO THE MIC.
7. Stop recording in Audacity.
8. In terminal press Ctrl+C to stop.
9. Play resulting wave file. (mic_check.wav)

This will record ANYTHING/EVERYTHING that comes out of your Speakers.

HTH.

---

### Post by ivarn on 2010-12-02
Ok it worked, but the saved wav file only records from the speakers.
And audacity still only records from the mic.
So how do I fix this problem?
As I said, I want to record input and output at the same time WITH THE SAME PROGRAM.

---

### Post by Habitual on 2010-12-03
Dude, IDK.

The script recorded my voice coming out of the speakers.
but it doesn't work with the headphones plugged in.
I have a headset (earphones and boom mic), I plugged in only the mic and the test worked for me.

Sorry.

---

### Post by ivarn on 2010-12-03
But you don't understand.
I want to use audacity to record both mic and music or skype at the same time.
I can't record skype calls now. I have to choose between input or output sound.

---

### Post by ivarn on 2010-12-05
Bump

---

### Post by Penguin=) on 2010-12-05
Download Skype Call Recorder (type it up on google and put: skype call recorder FOR linux) when downloaded it will take you to your ubuntu software center, then download it.

Wait about 5-10 mins, then log out, check your Accessories, and find skype call recorder!!!

---

### Post by Habitual on 2010-12-05
It's [here...]("http://atdot.ch/scr/files/0.8/skype-call-recorder-ubuntu_0.8_i386.deb")

---

### Post by Habitual on 2010-12-05
> **Penguin=) said:**
> Download Skype Call Recorder (type it up on google and put: skype call recorder FOR linux) when downloaded it will take you to your ubuntu software center, then download it.

Wait about 5-10 mins, then log out, check your Accessories, and find skype call recorder!!!

Uh, I gave him a perfectly good audio script to use, but he insists he wants something "more".

I suspect this post to be flame-bait.

---

### Post by ivarn on 2010-12-06
> **Habitual said:**
> Uh, I gave him a perfectly good audio script to use, but he insists he wants something "more".

I suspect this post to be flame-bait.
No, I mean thanks for the script. But I want a solution that works on my recording programs such as audacity. I need to know how I can be able to record both in and output at the same time as I can with windows.
The problem with that script is, I can't hear the mic in my speakers so therefor I can not use it to record both voice and music.
And I can't edit while recording using that script, which is a huge downside.

EDIT:
Also, Skype Call Recorder works like a charm. Thanks :)
But I still want to know this. Not just for me but as a tutorial or guide for others.

---

### Post by ivarn on 2010-12-07
Bump

---

### Post by Habitual on 2010-12-08
The script I gave you works in Audcacity. That is where I tested it. You have to run the script in terminal (and leave term+script running) while using audacity's Record button.

Once finished in Audacity, Ctrl+c the script in terminal and you'll have a wav file of the recording session.

---

### Post by ivarn on 2010-12-09
> **Habitual said:**
> The script I gave you works in Audcacity. That is where I tested it. You have to run the script in terminal (and leave term+script running) while using audacity's Record button.

Once finished in Audacity, Ctrl+c the script in terminal and you'll have a wav file of the recording session.
ok so maybe my audio settings are wrong then?
I mean since I can't make it work in audacity.
The script records a wav file with the output (only) when audacity still records the mic (only).
Ok so how is your audio input/output settings?
Mine is set to analog duples since I need both aoutput and input recorded.
Also, why do the script record a wav file anyway? it's so frustrating that I have to record from 2 places at the same time instead of just using my sound recorder program.

---

### Post by ivarn on 2010-12-11
Bump

---

### Post by ivarn on 2010-12-23
**bump**

---

### Post by Habitual on 2010-12-23
[http://ubuntuforums.org/showpost.php?p=10202952&postcount=13](http://ubuntuforums.org/showpost.php?p=10202952&postcount=13)

Welcome to my ignore file.

---

### Post by ivarn on 2010-12-27
Does anyone know how to fix this?
Skype recorder will do just fine for skype calls but other things I need in/output recording for won't work.
I thought this would be an easy thing to fix since it's so easy with windows.

---

### Post by ivarn on 2011-01-20
BUMB

Oh for gods sake. Is it really that hard to record both pc and mic audio in linux?
The  most logic thing would be analog stereo duple, but that only records  from mic. So, apparently the settings for the analog stereo duple and  input are the same.
Btw, I'm on ubuntu 10.04.
How hard is this to fix?
It's very important for me to get this solved, for things such as podcast recording and Cam recording.
The  only program I Have seen so far that will record both parts is the  skype recorder, but that only works within skype obviously.

This is a piece of cake process in window. So please help me solve this. THanks

---

### Post by ktat on 2012-08-18
Great script - just cut and paste, worked first time.

Thanks heaps,

:)

---

