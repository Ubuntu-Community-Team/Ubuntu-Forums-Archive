---
title: "Skype 2.1 MIC"
date: 2009-10-28
forum: General Help
---

### Post by pantera10 on 2009-10-28
ok im running 9.04 on a hp laptop..recently i installed skype it works fine...except tht it first of all refuses to acknowledge the internal mic of my laptop...and then when i buy an external one it jsut gives out too much static...i use the mic thru sound recorder and it worked fine there :S ..

---

### Post by Giblet5 on 2009-10-28
I had the same problem using a Plantronics B510 bluetooth headset.

Worked great on Windows, completely unusable on 2.1 under Linux.

I found that the 1.4.0.47 release worked fine, although it lacks the later features. I logged a support case with Skype but they don't respond because it's Linux.

[Here's a link]("https://developer.skype.com/Download/OldVersionsCopy#head-7c4e795cc1b9fb9c9cf168eff27098d80432e0eb") to older versions. Try the 1.4.0.47 release.


Download it, then open a terminal window and 'cd' to where you saved the .deb file. Then enter ```
sudo apt-get remove skype
sudo dpkg -i skype-1.4.0.74.deb
```

Post back with the result and, if that fixed it, mark this thread (SOLVED).

---

### Post by pantera10 on 2009-10-29
thanks for the reply...

however your solution provided me with the same results as i was getting with skype 2.1. Although 1.74 was giving me more options in sound devices as compared to pulse in 2.1...its still the same loud static mumbo jumbo whenever i speak into the mic..works fine normally though... :S 

i also tried using the windows version of skype on wine...but i was unable to configure tht cause it would freeze and give error OS failed

---

### Post by Giblet5 on 2009-10-29
> **pantera10 said:**
> thanks for the reply...

however your solution provided me with the same results as i was getting with skype 2.1. Although 1.74 was giving me more options in sound devices as compared to pulse in 2.1...its still the same loud static mumbo jumbo whenever i speak into the mic..works fine normally though... :S 

i also tried using the windows version of skype on wine...but i was unable to configure tht cause it would freeze and give error OS failed

Yeah... Skype won't work in Wine.

Any app that uses low level hardware calls won't work in Wine (there are exceptions but...)

This may be a pulseaudio problem.

Take a look through [this article about microphones and skype on 9.04]("http://blog.mageprojects.com/2009/03/24/get-your-microphone-working-in-ubuntu-904-and-skype-x64/"). I never tried it but it can't hurt anything.

---

### Post by cipicip on 2009-10-29
Have you tried using instead of pulse, alsa? In my case, in skype I have several options in its sound section. The default option in the combos is "Default Device". I selected "Intel Hw:0" (or something like this - I don't have the linux machine here with me). Then in the console, play with the alsamixer and its amplifiers (lower the amplifier level for that mic).

---

### Post by pantera10 on 2009-10-30
i already tried tht article giblet5 

cipcip : skype 2.1 only gives me 1 option of pulseaudio...however it gave me the options u speak of in 1.74...i tried all of themm..believe me i did..and it was same the problem...

:S

---

### Post by Primefalcon on 2009-10-30
Do what I did and go here

[http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

and download skype and skype common

go into synaptic and uninstall 2.1 

install the common and then the other... go back into synaptic and lock them so they don't get updates

---

### Post by pantera10 on 2009-11-03
Thanks alot PrimeFalcon....it works perfectly now ...one more thing id like  to know is that if this will work on 9.10, cause i have not updated yet

---

