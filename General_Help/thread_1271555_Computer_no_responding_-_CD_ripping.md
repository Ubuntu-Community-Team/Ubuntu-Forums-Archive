---
title: "Computer no responding - CD ripping"
date: 2009-09-21
forum: General Help
---

### Post by ozzyprv on 2009-09-21
Not sure what to do.
I am trying to rip a music CD. Right after I click start (Sound-Juicer) or press enter (ABCDE) the computer does not respond anymore. Nothing, no mouse pad, no keyboard, nothing. I have to hard-reboot. 
As I mentioned, I thought it could be Sound-Juicer, so I installed and tried ABCDE. Same, computer froze right after pressing enter to start ripping.

I am not sure what to do. What log should I be looking at?

For reference: this is happening on my Dell XPS 1340 laptop.

Please help.

Thanks.

---

### Post by ozzyprv on 2009-09-22
*bump*

Update:
~Booted to Window$, tried ripping the same CD using W-media player and it worked.

Please help.

---

### Post by ozzyprv on 2009-10-04
*bump*

No advance yet. I searched and searched a lot but I couldn't find anything about this. Not even suggestions as to how to diagnose the issue I have.

I am afraid of keep trying things because every time I try I have to do a hard reboot. I feel like I am going to corrupt my HD. 

The crash is so bad that not even the Alt+(Fn+PrnScr)/SysRq + RSEIUB method works. The systems freezes and there is no way to regain control of the mouse/keyboard.

I have a hard time believing nobody out there is able to help me. A peripheral (CD-ROM) crashing Ubuntu like that?

Anyone?

---

### Post by StuartN on 2009-10-04
I can't solve your problem, but it would give some useful information if you open a terminal and **sudo lshw -class disk** to see what disk hardware is recognized and to open preferences in Sound Juicer to see which disk device is selected there.

What happens if you try to play an audio CD? Can you mount and browse a data CD?

---

### Post by ozzyprv on 2009-10-04
THANK YOU StuartN, I do not want people solving my problems. What I need is help/guidance/suggestions.

VLC plays the audio CD, Rhythmbox too.

The output **sudo lshw -class disk** matches the device (CD drive) Sound Juicer would use. The problem starts when I click "Extract". 
Everything appears to start okay, but then system crashes.

I tried some other CLI based ripping tool with the same result.

Let me know if showing the actual output of lshw would help.

---

### Post by StuartN on 2009-10-04
[QUOTE=ozzyprv;8052661]The problem starts when I click "Extract"./QUOTE]

It sounds like your hardware is recognised and the disk mounts okay, otherwise you could not play. The next point for failure could be the track lookup or the encoding settings. Does it retrieve a sensible track listing? If you go to the Sound Juicer preferences, Edit profiles and Edit the profile that you are using, does it look sensible?

(my "CD Quality, MP3" is "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux")

If that all looks okay, then it is possible that your command line level tools are not functioning.

I see this example from man gst-launch:

  gst-launch cdda://5 !  lame  vbr=new  vbr-quality=6  !  filesink location=track5.mp3

---

### Post by ozzyprv on 2009-10-04
This is my GStreamer pipeline: "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux"

I am not sure what you mean by that example.

Thanks again!

---

### Post by StuartN on 2009-10-05
> **ozzyprv said:**
> I am not sure what you mean by that example.

If you open a terminal an run gst-launch <pipeline> then you can test the settings used in Sound Juicer. The reason for doing this is to be able to see any error messages that the GUI is hiding at the moment that encryption starts and messes up your system. At least that is the theory, but when I try it, all I get is:

```
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
```

Presumably the CD has already been assigned to and locked by another process.

Someone wiser than me might be able to help.

---

### Post by ozzyprv on 2009-10-13
> **StuartN said:**
> 

Someone wiser than me might be able to help.

...still waiting...

---

### Post by ozzyprv on 2009-10-30
**bumped again...**

---

