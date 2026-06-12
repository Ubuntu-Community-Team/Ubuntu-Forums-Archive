---
title: "Changing Midi to MP3 (Using timidity.. or anything!)"
date: 2010-03-14
forum: General Help
---

### Post by RabbitWho on 2010-03-14
Been searching around about this for ages, got a .mid exported from rosegarden (which is an awesome program). 
Need to make it an MP3 or OGG or any kind of standard audio file.
[U]
With Timidity:[/U]

I'm using version 2.13.2

Found this advice: 
[http://ocmnet.com/saxguru/TimiditySetup.html#Midi2Wav](http://ocmnet.com/saxguru/TimiditySetup.html#Midi2Wav)

Isn't it awesome and clear and well put together? 
If your wondering yes the file will play for me from Timidity and I can hear it fine.
Problem is there's no "Config" on my version. Closest thing is when i click file and save config. Normal click doesn't open the menu, gotta click and hold, which i do, then drag the cursor down to where i want it and release, nothing happened. It also said meta + S would open it, that's super/windows key + S, right? No luck. 

Anyone know a comandline way of doing it? 
I found a list of commands for it here but it's probably grossly out of date: [http://sca.uwaterloo.ca/www.cgs.fi/tt/timidity/timidity.txt](http://sca.uwaterloo.ca/www.cgs.fi/tt/timidity/timidity.txt) and i couldn't find anything about saving. 
[U]
With Audacity: [/U]

Apparently you can use Audacity to record the output of the sound card directly. 
However I can't seem to figure out how to set this. It says in the into there's a preferences drop down next to the mixer thingy, maybe i'm blind but I can't find it anywhere. 


Any help very much appreciated and awarded with beautiful pictures of chickens to midi music. 



(Audacity and Timidity are the names of programs and not necessarily emotional states I am going through as you might think)

---

### Post by RabbitWho on 2010-03-14
Bump :)

---

### Post by RabbitWho on 2010-03-14
Bump

---

### Post by RabbitWho on 2010-03-14
In the end I just played the song in timidity and recorded it on my microphone, not the quality I would have liked: 

[http://www.youtube.com/watch?v=1olXK9nxHO0](http://www.youtube.com/watch?v=1olXK9nxHO0) 

But better than nothing, the whole point of this was to see if I could make songs, that tune just started with me messing around (i just hit the stave randomly for the first few seconds of it as you can hear) and then developing something out of that. At least I know how to do it now. 

And I'm reasonably happy with the result!

---

### Post by RabbitWho on 2010-03-14
Gonna try one more bump! It would be so cool if i could somehow get something that would capture an MP3 directly from the sound card as the midi was playing, instead of having to record it with the microphone. Quality and all.

---

### Post by RabbitWho on 2010-03-15
Okay okay seriously, just gonna try ONE MORE TIME just in case.

---

### Post by Trebawa on 2010-03-15
I'm here to help!  According to [this post]("http://ubuntuforums.org/showpost.php?p=5817175&postcount=2"), you can add a loopback virtual sound card by running this command:
```
sudo modprobe snd-aloop
```
Then go to your sound settings and set the loopback card as the input source.  Finally, play the file with the soundfont of your choice and record it using Sound Recorder or a similar application.

---

### Post by blueridgedog on 2010-03-15
Take a look:

[http://www.ehow.com/how_5114457_convert-midi-mp-ubuntu.html](http://www.ehow.com/how_5114457_convert-midi-mp-ubuntu.html)

---

### Post by RabbitWho on 2010-03-16
Awesome! Hurraaaaaaaaaaaaaaaaaaaaaaaaah! thank you so much! 

(marking thread as solved)

---

### Post by derhannes on 2010-11-23
Just in case above link becomes broken:

MIDI to WAV using "timidity":
```
timidity -Ow myMidiFile.mid
```

Other formats are available as well:
```
timidity --help
```

---

