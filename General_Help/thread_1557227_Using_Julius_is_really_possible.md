---
title: "Using Julius is really possible?"
date: 2010-08-20
forum: General Help
---

### Post by enverhoxha on 2010-08-20
I have installed Julius, the voice recognition software, with Package Manager. Alright, and what do I do now? There's no trace of it in the Applications menu. 
If I go to /usr/bin and click on the Julius executable, nothing happens. (It's not the only software that behaves like this after installation, btw...)
Is there something I miss here? Is there another piece of software I need in order to get Julius work?

---

### Post by Shazaam on 2010-08-20
Open terminal, type in...
```
julius
```
and see if it runs or errors out.
If it runs, you may have to add it manually to the MainMenu. Or you can right-click the desktop and make a launcher.

---

### Post by enverhoxha on 2010-08-20
No run, no errors. Just a message suggesting to use the ”-setting” command to configure the engine, or the ”-help” command. There's no user interface?

---

### Post by QBalls on 2010-08-22
I'm new too. below is the output returned to the terminal command "julius" and help returns an error. What am I missing?

Julius rev.4.1.2 - based on 
JuliusLib rev.4.1.2 (fast)  built for x86_64-unknown-linux-gnu

Copyright (c) 1991-2009 Kawahara Lab., Kyoto University
Copyright (c) 1997-2000 Information-technology Promotion Agency, Japan
Copyright (c) 2000-2005 Shikano Lab., Nara Institute of Science and Technology
Copyright (c) 2005-2009 Julius project team, Nagoya Institute of Technology

Try '-setting' for built-in engine configuration.
Try '-help' for run time options.

---

### Post by suggestions on 2010-09-07
> **QBalls said:**
> I'm new too. below is the output returned to the terminal command "julius" and help returns an error. What am I missing?

Julius rev.4.1.2 - based on 
JuliusLib rev.4.1.2 (fast)  built for x86_64-unknown-linux-gnu

Copyright (c) 1991-2009 Kawahara Lab., Kyoto University
Copyright (c) 1997-2000 Information-technology Promotion Agency, Japan
Copyright (c) 2000-2005 Shikano Lab., Nara Institute of Science and Technology
Copyright (c) 2005-2009 Julius project team, Nagoya Institute of Technology

Try '-setting' for built-in engine configuration.
Try '-help' for run time options.
the same holds for me.. I'm completely unable to use Julius.. I have removed it after just 10 minutes since the installation.. linux has this congenital cancer: a neverending trouble at the user level.. :-(

this doesn't mean that I'm not grateful to the community for offering linux to all of us.. I try to use it as much as possible..

---

### Post by DJonsson2008 on 2010-09-19
I'm trying to get Julius to run as well.

I've discovered that its best to copy a copy of the
Sample.jconf into the directory where you are running
it from. 

ie \home\myhomedir\Sample.jconf

from my home dir then I ran

$ julius -C Sample.jconf

at which point it responded.

ERROR: m_chkparam: you should specify at least one LM to run Julius!

so i opened Sample.jconf and tried uncommenting out the line.

## You should give a unique name.
## -LM (name)

and entered 
-LM lm_1
then saving the Sample.jconf file

I again attempted 

$ julius -C Sample.jconf

I then get the response

ERROR: m_options: wrong argument: "scores"

I've also checked the following resources for clues/hints or insights.
* downloaded the documentation PDF from
  [http://julius.sourceforge.jp/en_index.php](http://julius.sourceforge.jp/en_index.php)

and checked the Julius Ubuntu package page,
* [http://packages.ubuntu.com/lucid/sound/julius](http://packages.ubuntu.com/lucid/sound/julius)
and the man page
[http://manpages.ubuntu.com/manpages/lucid/en/man1/julius.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/julius.1.html)

Both sources lack examples and troubleshooting suggestions.

---

### Post by junapp on 2010-09-19
some decent reading at:
[http://globalbase.dl.sourceforge.jp/julius/47534/Juliusbook-4.1.5.pdf](http://globalbase.dl.sourceforge.jp/julius/47534/Juliusbook-4.1.5.pdf)

according to 
[http://hackaday.com/2010/07/09/get-started-with-speech-recognition/](http://hackaday.com/2010/07/09/get-started-with-speech-recognition/)
Julius is a work in progress still, so perhaps Linux shouldn't labeled as having a cancer. 

There seems to be a growing forum at:
[http://julius.sourceforge.jp/forum/](http://julius.sourceforge.jp/forum/)

Maybe someone there can assist with options and getting you up and running.

Good luck.

---

### Post by DJonsson2008 on 2010-09-19
I appreciate the links above but the Julius resources are not
very helpful, as the in both their forums and documentation their
is little patience or help available for beginners. As well this is a multi-platform project so gaining any insight into how to use with Ubuntu from reading Julius'  PDF, forums or website may require quite a bit of sifting through info for other platforms and in the end prove to a dead end. 

Julius is part of the Ubuntu LTS package, so people are not wrong in thinking that it should work. Likely hundreds more have tried Julius than those who have commented here. Those who have gone to the Julian forums to ask have found the tone in response to beginners condescending. The Ubuntu Julius man link above contains no examples of use.

---

### Post by DJonsson2008 on 2010-09-19
A user friendly GUI for Julian can be found with Simon,

Unlike Julius Simon's forums contain enough detail for 
beginners, and the GUI in and of it self somewhat
explains the various components. 

In any case it takes a bit of time to get it going but
Simon gives major GUI leverage to Julius from what I've
seen so far.

for more info 

[http://ubuntuforums.org/showpost.php?p=9864792&postcount=2](http://ubuntuforums.org/showpost.php?p=9864792&postcount=2)

---

### Post by verdomde on 2011-02-13
From what I understand Julius doesnt have a gui, there are examples of how to use it in /usr/share/doc/julius-voxforge/examples/ with instructions, plus there is an online manual. From what I gather the voice recognition developers seem to be concentrating on building valid, working libraries of speech in order to support front ends. Seems to be a massive task, and requires many hours of speech input. You can donate some of your time to voxforge and help out eh?

---

