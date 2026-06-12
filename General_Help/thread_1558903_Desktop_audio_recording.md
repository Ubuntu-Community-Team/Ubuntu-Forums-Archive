---
title: "Desktop audio recording"
date: 2010-08-22
forum: General Help
---

### Post by chips24 on 2010-08-22
Where could i find an application that only records sounds in the computer.
my microphone has very poor quality and i would like to record audio on my desktop in its best quality.
speaking of poor quality, how come my avatar is so small? Can it not get any larger?

thanks.

---

### Post by jroa on 2010-08-22
If I understand the question correctly, you are asking for software that will record .mp3 or something else that is playing on the computer, but not from the microphone?  If this is what you are asking, then any recorder should work for you, you just have to either turn off/unplug the microphone or adjust the configuration of the recorder so that it does not pick up the mic.  You may need to configure the recorder to so that it will pick up directly from the computer as well.

---

### Post by chips24 on 2010-08-22
You are understanding my question correctly. I am using Audacity. How do i configure it to record Audio from the computer without Stereo mix?

---

### Post by jroa on 2010-08-22
I am not real familiar with Audacity, and I am on my XP computer right now, but the linux version should look something like the picture.  I suppose you could try the different inputs until you figure out which one will let you record directly from the computer.[IMG]http://i739.photobucket.com/albums/xx38/jorroa5990/Aud-1.gif[/IMG]

---

### Post by chips24 on 2010-08-22
hmm... I thought I made it clear that I am not trying to record with my microphone. I said I am trying to record any audio sources from my computer, not input (which includes microphone, Line in, etc.)
for some reason I could not find that on the linux verson, my stereo mix card is inactive and unrecognizable to linux for some reason. I was trying to find an alternative.

---

### Post by chips24 on 2010-08-22
As you can see, for some reason I do not have that drop-box.

---

### Post by jroa on 2010-08-23
chips24, I know you do not want to record with the mic. I was just showing you where you select the input. For what you want to do, you probably want to select Stereo Mix, but like I said, I am not really familiar with Audacity, so it might be CD Player or Aux or one of the other settings that will do what you want.  You may also have to go to Edit->Preferences->Audio I/O to change the recording device.
 
As far as being able to see this pull down menu, you can not see it right away in Windows either. I had to select View->Float Meter Toolbar. Then I could see it.

---

### Post by Bonster on 2010-08-23
Use PulseAudio Device Chooser and select the speaker stream and record

---

### Post by chips24 on 2010-09-02
All I needed to do was mute the input stream... 
LOL

---

### Post by inameiname on 2010-09-02
This will record all audio that goes to your speakers:

[http://www.omgubuntu.co.uk/2010/07/q...output-in.html]("http://www.omgubuntu.co.uk/2010/07/quickly-record-soundcard-output-in.html")

---

