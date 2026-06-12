---
title: "No sound from tuxGuitar?"
date: 2009-09-12
forum: General Help
---

### Post by The-ITu on 2009-09-12
hello
I downloaded tuxguitar and it does not seam to be giving any sound once I play any song.
its kinda wired. if any1 could help me that would be appreciated. thanks.
The-ITu

---

### Post by khelben1979 on 2009-09-12
Source of the download?

---

### Post by The-ITu on 2009-09-12
synaptic package manager.

---

### Post by khelben1979 on 2009-09-12
I see. You can always try the version [from their homepage]("http://tuxguitar.herac.com.ar/") to see if it works better.

---

### Post by Exodist on 2009-09-12
> **khelben1979 said:**
> Source of the download?

Its in the repos.

None of the MIDI based software is working and Jack server is no where to be found also. So this effect Rosegarden and other programs like Frets of Fire the same.

---

### Post by The-ITu on 2009-09-12
> **khelben1979 said:**
> I see. You can always try the version [from their homepage]("http://tuxguitar.herac.com.ar/") to see if it works better.
i tryed that. i uninstalled my last version and download a .run file from site.
after installing it and opening it, when i play the song i get an "MIDI system is unavalable" error.
:S

---

### Post by The-ITu on 2009-09-14
**bump**

---

### Post by stephen.robin on 2009-09-14
HI

There is problem is sound, you have to check your system and also check your speaker is working  proper or not. There may be problem in download. :guitar:

---

### Post by danwood76 on 2009-09-14
You probably need to install Timidity and use that as the midi output from tuxguitar (set in tuxguitar prefs).
This is due to not having a hardware midi output device so the timidity software converts the midi to audio for you!

---

### Post by JonMoss on 2009-10-07
> **danwood76 said:**
> You probably need to install Timidity and use that as the midi output from tuxguitar (set in tuxguitar prefs).
This is due to not having a hardware midi output device so the timidity software converts the midi to audio for you!

I had some trouble with the sound in the 64-bit version of Kubuntu Jaunty.  Is Timidity compatible with Alsa?  

Thanks, 

Jon Moss
Lansing, Kansas

---

### Post by danwood76 on 2009-10-07
Yes fully compatible with Alsa.
You have to make sure you set tux to use the timidity driver as it defaults to the non working midi.

---

### Post by ZaHACKieL on 2009-10-07
I'll tell you what I did to make it work.

First I downloaded the package sun-java6-jre and after that, the soundbank deluxe from [http://java.sun.com/products/java-media/sound/soundbanks.html](http://java.sun.com/products/java-media/sound/soundbanks.html)

I downloaded the TuxGuitar 1.1 from the official site. There is a .run and a .deb package. I tried both and the two worked but I think its easier to use the .deb file.

So, those things did the trick for me. Try it and let me know if it works!

ZL

---

### Post by danwood76 on 2009-10-08
If you were to have installed timidity that would also work.
It would also be easier as its all from the repos.

---

### Post by Arkold Thos on 2009-10-19
Not working since I upgraded to Karmic, Timidity installed and doesn't appear in tuxguitar settings. Worked on Jaunty, and Edgy.

Edit, worked, thanks!
> **ZaHACKieL said:**
> I'll tell you what I did to make it work.

First I downloaded the package sun-java6-jre and after that, the soundbank deluxe from [http://java.sun.com/products/java-media/sound/soundbanks.html](http://java.sun.com/products/java-media/sound/soundbanks.html)

I downloaded the TuxGuitar 1.1 from the official site. There is a .run and a .deb package. I tried both and the two worked but I think its easier to use the .deb file.

So, those things did the trick for me. Try it and let me know if it works!

ZL

done a fast and easy [guide]("http://arkold.com/811-java-sound-synthesizer-and-tuxguitar-on-karmic") for doing it. 

AGAIN THANKS!

---

### Post by rsmitty on 2009-10-20
Just had the same problem with no sound. I'm using Hardy.

Installed tuxguitar using the .deb from the website. It's version 1.1 (1.0 is in the repos).
Solved it by getting Timidity.

In Terminal:
sudo apt-get install timidity

Then In tuxguitar:
Tools>Settings>Sound> Set MIDI port to TiMidity port 0.

Hope that helps.

---

### Post by gotgenes on 2009-10-23
You don't need to mess around with Timidity. See [http://ubuntuforums.org/showthread.php?t=1125054&highlight=tuxguitar&page=2#15](http://ubuntuforums.org/showthread.php?t=1125054&highlight=tuxguitar&page=2#15)

---

### Post by Predatorian on 2009-10-27
thank you for the reference to the other thread, restarting timidity did it for me, cause i installed all those other plug-ins and it worked fine a for a few days, but then it stopped working today, and restarting timidity did it. thank you *buntuers.

---

