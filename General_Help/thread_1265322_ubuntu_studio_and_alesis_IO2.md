---
title: "ubuntu studio and alesis IO2"
date: 2009-09-13
forum: General Help
---

### Post by metalmaniac248 on 2009-09-13
im just getting into recording my own music at home, and am looking to get a pair of microphones, and something like the alesis IO2 to interface the microphones with my computer,

has anyone had any experiences or knows anything about ubuntu (or linux in general) and the alesis IO2 (or similar)

thanks

---

### Post by pumatheman on 2009-12-04
I would like to buy one!!! anyone has any news? does it works on 9.04? and on 9.10??
HELP !!!

---

### Post by maghoxfr on 2010-03-10
In this [website]("http://www.linuxstudiopro.com/") you can see all the audio hardware that's supposed to run on ubuntu, the io2 is not there. I was planning to buy one too but I really don't want to struggle to make it work. I'm sure it can be done but I don't know how. Here's the link

---

### Post by jinnan_tonnix on 2010-03-11
It works fine on the latest Ubuntu Studio (you need to configure it through jack, of course). I used it to record some electric guitar (amp output -> Alesis input) and was impressed by the very low latency (Jack > Ardour)

BUT....... for the life of me I cannot get the MIDI to work with my old-style MIDI keyboard (5-pin round plug). I'm going to have another shot then give up and buy a USB keyboard.

---

### Post by maghoxfr on 2010-05-20
> **jinnan_tonnix said:**
> It works fine on the latest Ubuntu Studio (you need to configure it through jack, of course). I used it to record some electric guitar (amp output -> Alesis input) and was impressed by the very low latency (Jack > Ardour)

BUT....... for the life of me I cannot get the MIDI to work with my old-style MIDI keyboard (5-pin round plug). I'm going to have another shot then give up and buy a USB keyboard.
I need an interface desperately, there's not many available in my country and the ones that are available are not supported by linux. For example I'm reading the best reviews about the Saffire 6 USB but it hasn't linux drivers.

Do you have the Alesis io2 running with no problems at all? I mean latency, xruns, weird malfunctioning problems...

Because I'm willing to take your testimony as holy and go out and buy it LOL. I want to record so bad.

PS: I have an USB midi controller keyboard so the midi port is not my priority.

---

### Post by twcook on 2010-09-20
Using the iO2 Express all I have available in JACK is:
Output Ports:  20:io|2                       
                  0:io|2 MIDI 1

Input Ports:  20:io|2 
                  0:io|2 MIDI 1                                 

So the left or right channels for guitar/mic do not show up.

Any ideas?

If I use it with ALSA into Audacity I get the static issues that others have reported.  

I am using Ubuntu 10.04 with Ubuntu Studion installed with the preempt kernel.  I am new to this audio recording stuff but not new to Linux.

Thanks,
Tim

---

