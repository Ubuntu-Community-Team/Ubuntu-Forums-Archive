---
title: "music editing"
date: 2006-03-22
forum: General Help
---

### Post by gos1 on 2006-03-22
does anyone know the best music editing software (like cakewalk , protools etc) for ubuntu ? I couldnt find one.

---

### Post by OffHand on 2006-03-22
Audacity for editing. Dunno about quantisizers.

---

### Post by gos1 on 2006-03-22
can I compose music with that software  ?

---

### Post by OffHand on 2006-03-22
[QUOTE=gos1]can I compose music with that software  ?[/QUOTE]Check out their website to see what it is capable of: [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/) I know quite a lot of musicians but they all use either xp or mac os x. Linux isn't the best yet for some serious producing imho.

---

### Post by gos1 on 2006-03-22
I want to use a midi keyboard and a firewire sound card with a suitable software under linux. I cannot trust windows at stage and saw some one using a realy good software under linux. Just searching for that now. Thank you for your help. take care.

---

### Post by IYY on 2006-03-22
Audacity is not for composition. You use it to record, mix and edit audio. I actually heard that audio production is one of Linux's weaker points today.

---

### Post by Matt Yun on 2006-03-23
[QUOTE=gos1]does anyone know the best music editing software (like cakewalk , protools etc) for ubuntu ? I couldnt find one.[/QUOTE]

I don't have a lot of experience with these, but you might want to check out the software mentioned at these sites:

[Debian Multimedia List]("http://debianlinux.net/multimedia.html")
[Wired]("http://wired.sourceforge.net/") -- the multitrack app, not the magazine (reviewed on [Slashdot]("http://slashdot.org/article.pl?sid=04/11/13/0423234&tid=141&tid=185&tid=1"))
[Studio-To-Go]("http://www.studio-to-go.com/index.php?option=com_smf&Itemid=78") -- commercial Linux LiveCD for audio studio apps
[Linux-Sound.org]("http://www.linux-sound.org/") -- lists of audio apps
[FST]("http://joebutton.co.uk/fst/") -- enable VST plugins under Linux

---

### Post by Gustav on 2006-03-23
There is a special project called Ubuntu Studio that is for ubuntu musicians: [http://ubuntustudio.com](http://ubuntustudio.com)

I think they should have all the information you're looking for

---

### Post by bionnaki on 2006-03-23
I cant wait until audio apps are better developed in linux. until then I'm thinking of creating a windows partition solely for ableton live 5.

---

### Post by damu on 2006-03-23
You basically want a sound studio running on Linux   :) 
That's not a prob, sound design is part of my job and I know** you can have a complete sound studio running on Linux**.

- Rosegarden is the best sequencer so far in the linux world.

- Ardour is the best multitrack audio recorder, with full automation for the mix

- Hydrogen is a perfect drum machine

This 3 masterpieces can run in sync thanks to jack sync


- Fluidsynth wil allow you to use all your favorite sound fonts (best way to use sampled instrument in linux so far for me).

-Equivalent to VST (which for most of them can also run on linux sound studio), a good 200 alsa plug-ins  will help you get "the sound!" (compression, dynamic, reverb, delay, chorus, phaser and so on)  

- You will find some synths and other loads of other cool softwares running under linux for music creation.

- For mastering, you will  use Jamin, a very very professionnal tool including 30-band and 1023-band equalisers, a spectrum analyser, a three-band peak compressor and a look-ahead brick-wall limiter...

- The audio is routed through a master piece in Linux, Jack.

**The main difficulty is to get a low latency kernel**. It's hard core job. 
Installing all this softwares and make them running all together is another hard job.

I **don't know yet any solution which support firewire soundcards**...that could be your biggest problem to switch to Linux for audio production. My RME Multiface works perfectly...

If you will really want to run everything with Ubuntu, then check [ubuntustudio]("http://ubuntustudio.com")

If you don't feel confident enough to go through all the steps needed, I would strongly suggest to g**et a specific linux distribution for audio production, and a live cd one** is definitely the best approach. It will take a bit longer to open an apllication from a live cd, but once it's running you won't nootice much difference in the speed of processing

- The best distribution so far on Linux world is not free (50£ - 70€ ) is [studio to go]("http://studio-to-go.com/") . That's the one I use. I didn't know much about Linux before, and it has been the perfect distro for me. Boot on the cd and start doing music...it just works!  It comes with native support of most VST, including in the sequencer Rosegarden. Check on their website the list of compatible hardware. The studiotogo team is very active , so if you have any question, just post on their forum

- a good free alternative to Studiotogo is [musix]("http://www.musix.org.ar/en/index.html")
You will probably not have native support for VST. My RME will be mounted, but with no sound...the RME mixer is missing. But with a few tweaks, it can be a very interesting distro. It includes all the softwares yu need , and more!

Agnula has been a  leading project in the linux world for audio production, even though it is not founded anymore...worth having a look

---

### Post by voldemar on 2006-03-23
Actually i am not a professional in music, but i've found some links:
[http://ubuntustudio.com/wiki/index.php/Links](http://ubuntustudio.com/wiki/index.php/Links) - list of music software
[http://lmms.sourceforge.net/](http://lmms.sourceforge.net/) - a good tool for making music (if trust the screenshots). Sample files are also avaliable.

---

### Post by gos1 on 2006-03-24
I checked that link before typing this quote but editing kernel is not something &#305; want does anyboy know. If I edit kernel again for audio works does it effects other applications performance  ?. I just dd not do that for ths reason.

---

### Post by voldemar on 2006-03-24
You about LMMS? Why you should edit your kernel?:confused:

---

