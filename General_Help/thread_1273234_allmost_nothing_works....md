---
title: "allmost nothing works..."
date: 2009-09-23
forum: General Help
---

### Post by Guitar-maniac on 2009-09-23
I've been trying to study linux ubuntu for couple weeks now but got allmost nowhere and it's pretty frustrating.
I downloaded tuxguitar since i am a guitarist, but no midi wont work, the program crashes once in a while (mostly while you are trying to shut it down it just freezes), i looked into google, found help but it didn't work.
I downloaded and installed gtkpod, but no, it says error to write while trying to add songs to my ipod and it cant decode my mp3 files, says it's some error again.
I have the latest drivers but still this system says video card drivers isn't installed everytime i start my computer again and i can't install since when tried, my computer says they are in there already. and when writing text for example in facebook it's painfully slow, as scrolling up and down internet sites.

Those are the main problems i have, pretty annoying in everyday use.. since i really would need some guitar tablature editor because of my hobby and band. and yeah, i wuold like to put songs in my ipod :D

is the problem in my hardware or what?
I have nvidia GT8600
2 GB ram
Intel dual core 1,86

---

### Post by nothingspecial on 2009-09-23
Hello and welcome :) 

[[COLOR="Magenta"]midi[/COLOR]]("https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo?action=show&redirect=MidiSoftwareSynthesisHowTo")

Is there a nvidia graphics card in system > administration > hardware drivers? I believe NVIDIA 177  is the one you want.

For your iPod try a few different apps Rhythmbox, Banshee, Amarok

---

### Post by bruno9779 on 2009-09-23
For the Ipod I would use Amarok or Banshee, look _[here]("https://help.ubuntu.com/community/PortableDevices/iPod")_

Graphic card: the right package for your card is nvidia-glx-180 _[here]("http://packages.ubuntu.com/jaunty/nvidia-glx-180")_
After installing it you must go to hardware drivers, activate it and reboot

---

### Post by proxess on 2009-09-23
For your iPod I'd recommend gtkpod-aac,It's what I use with my iPod. Install mp3gain and aacgain and search Synaptic for the other converters requested by gtkpod-aac.

For midi, install timidity.

For your GPU, Use what is said above.

---

### Post by Guitar-maniac on 2009-09-23
I have tried Banshee with my ipod since i listen to my music with it, it sees my ipod but the songs inside it/don't let me add anything in it, it just shows it has some data inside it but don't know what.

I have to check into timidity soon thanks about that.

and about the nvidia, i have the 180 version installed that you recommended.

---

### Post by bruno9779 on 2009-09-23
Did you activate the drivers? 
I had the right version of the drivers installed at first boot, but i had to activate them before the graphic card actually worked

---

### Post by Guitar-maniac on 2009-09-23
Timidity didn't work. tuxguitar just tells me that MIDI system unavailable. It's installed on my computer, i did everything the instructions told, it installed just fine.. but don't work. i rebooted after the installation. but still no effect.
I don't what to do anymore with this OS :D it sure isn't as stable and great i was told to :D programs crashing and stuff not working after installation and writing is slow as h*ll. tho i have tried absolutely every intsructions i could get my hands on these past couple weeks.

And since i don't have windows anymore (i believed that i could use this as a primary operating system and deleted Vista since i don't play games much) se i am stuck now with this! :D

---

### Post by nothingspecial on 2009-09-23
Well don`t panic, we`ll get it sorted ......... after sleep tommorow.

---

