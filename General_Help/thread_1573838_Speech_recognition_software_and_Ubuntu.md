---
title: "Speech recognition software and Ubuntu"
date: 2010-09-13
forum: General Help
---

### Post by andymorton on 2010-09-13
Hi,

I won't bore you with the details but among other things I'm finding increasingly difficult to type because of neurological problems. I've just had a meeting with someone from university who said they could get me some speech recognition software to write assignments. I was wondering if anyone knows of any which will run on Ubuntu rather than just Windows. (I don't have Windows on either of my computers)

Thanks
andy

---

### Post by Mark Phelps on 2010-09-13
The wiki link below is a good starting place:

[http://en.wikipedia.org/wiki/Speech_recognition_in_Linux]("http://en.wikipedia.org/wiki/Speech_recognition_in_Linux")

---

### Post by |{urse on 2010-09-13
The only progress I've made so far in finding a working speech recognition/text to speech program on linux is running a software called Dragon Naturally Speaking 8 under wine. Its interface was very glitchy but the actual recognition engine seems to work fine and simply outputs whatever you say (correctly for the most part) to the current cursor position (whatever window you have clicked last with your mouse). Sorry I don't have more info on the wine version I was using. Please post back if you find something that actually works well.

---

### Post by |{urse on 2010-09-13
[http://thenerdshow.com/platypus.html](http://thenerdshow.com/platypus.html)

You will need this too.

---

### Post by wojox on 2010-09-13
There's [Gnome Orca]("http://live.gnome.org/Orca") that's the closest thing.

---

### Post by |{urse on 2010-09-13
I tried orca a couple years ago but i think all it did read aloud what is currently on the screen via festival. I think what the OP is looking for is a speech to text program. Like where you can dictate through the mic and the program will output text matching what was said. Maybe I am mistaken?

---

### Post by wojox on 2010-09-13
> **|{urse said:**
> I tried orca a couple years ago but i think all it did read aloud what is currently on the screen via festival. I think what the OP is looking for is a speech to text program. Like where you can dictate through the mic and the program will output text matching what was said. Maybe I am mistaken?

I got it. I thought it could read in a text file like festival or espeak.

---

### Post by DJonsson2008 on 2010-09-16
I'm not sure if perhaps we should change the title here to
"speech-to-text" 
specifically as 
speech -->into--> text which seems to be the frontier.

Text to speech seems to be much easier to find a solution for.

Specifically what I'd like is to be able to open a word processor
and/or text editor and simply talk to write. I can use the mouse
or keyboard to open the the text editor or word processor but
from then on out would like the bulk of entry to be via speech.

Seems feasible but can't find an exact tutorial on this anywhere yet? 

In theory Sphinx2 or Julius should do this but can't find any howto info
on it.

---

### Post by ngrieb on 2010-09-16
Sorry to hear about your troubles, I thought that this would be a nice thing to have as well, and saw one of my friends was using something for this in OpenOffice but I can't remember if it was in Windows or Linux. Either way I found this if you have not given it a try yet: [http://freespeech.sourceforge.net/](http://freespeech.sourceforge.net/) . Hope this helps. I might give it a try later myself.

---

### Post by |{urse on 2010-09-18
It seems to me that since this feature comes standard with windows 7 there should be someone racing quickly behind (usually ahead) in the OSS herd. Speech to text is super BAD-A because i can walk around the house with a wireless mic and dictate emails/documents/a friggin novel while doing whatever else. 

@ the guy who mentioned julius, I almost have that working and will post a howto if anything comes of it.

Please everyone post your findings here if you do manage to find a linux native solution.

---

### Post by DJonsson2008 on 2010-09-19
I spent a few hours checking this out. There seem to be a lot of 
developer tools out there, Sphinx and Julius included. Although
their websites indicated Speech-to-text is a big part of their goal,
I can't find any direct link on how to make this practical with
Ubuntu.

Sphinx-4 which isn't in the Ubuntu 10 repositories but seems to
have basic sample util to demonstration Speech-->to-->Text.
There is also something called PocketSphinx for the portable 
devices like the Android, where much of the GUI attention seems to be going.  

Something called python-pocketsphinx seems to have been part of Karmic but is now not in the repositories.

[http://packages.ubuntu.com/karmic/python-pocketsphinx](http://packages.ubuntu.com/karmic/python-pocketsphinx)

Sphinx-4 reportedly has a related application promisingly called "Dictation" in Java as a tookkit for making a practical app, but again hard find any usable information. Personally I'd prefer a python solution.

ViaVoice by IBM has a few howto's out there but last was supported
on Mandrake circa the year 2000, so intensive rollback and hacking would be needed to even get that to a test level. 

Not to dis the CMU-Sphinx or Julias websites they are buried in crucial
technical issues for their active expert participants. But gaining critical mass likely requires at least a gateway/entry level app that people can use and/or play with.

A year to 2 from now when I buy an Android, a selling point would be Voice-to-SMS-text. Hard to understand why it is so hard to find any solid Ubuntu info on this what seems to be a crucial feature, or at least very feasible these days with multi-core CPUs.

---

### Post by |{urse on 2010-10-11
Sorry for the necro. Still looking for some well deserved joy on this. Anyone?

---

### Post by Reileigh on 2010-10-11
Wonder if Wine 1.2 would run Dragon 10?

You see Dragon 10 is the best out of all dictation programs, but they have patents every which way on their algorithms, so essentially, if you want dictation software that is production-grade, you need Dragon 10, on Windows 7, and really good hardware. It is a resource monster.

My computers barely run version 10 effectively, that's without emulation. Worth a try ubuntu/wine though if you have a copy. I am unsure if activation would work though.

---

### Post by DJonsson2008 on 2010-10-12
What the person above said about Dragon, although momentum is building.

For an intelligent discussion of the problems and current status of full dictation in existing open source solutions the simon/speech2text forum is informative.

[http://sourceforge.net/projects/spee.../topic/3685883](http://sourceforge.net/projects/spee.../topic/3685883)

Simon as well is a slick and impressive GUI, while admittedly limited to the current speech to text resources it seems well poised to advance and also benefit from users feedback. It seems suitable for a limited commands dictionary but not full dictation, but is trainable, according to the author.

For more info check the discussion here.
[http://ubuntuforums.org/showthread.php?t=1575877&highlight=sphinx](http://ubuntuforums.org/showthread.php?t=1575877&highlight=sphinx)

---

### Post by |{urse on 2010-10-13
Yeah Dragon and wine was mentioned earlier in this thread. It works best when ran with platypus. That's what I'm currently using. It's... just okay. Any native solutions? Windows 7 has it standard already.

---

### Post by DJonsson2008 on 2010-10-14
IBM had a Linux native solution years ago, but I don't think
it is supported anymore. 

Presently development in this area with Linux appears to be
fragmented. Although issuing finite commands seem to be 
available full dictation is hard to find.

For full dictation Simon as mentioned above has
brought the issue to a workable and flexible GUI, and from 
what I can tell speculates 1-2 years for better development.

There is chatter about a java/open office solution floating on the net, but like with Sphinx and Julius when you look closer you may find in fact it is a set of development tools only. 

Keep looking though and if you find something else please let me know.

---

