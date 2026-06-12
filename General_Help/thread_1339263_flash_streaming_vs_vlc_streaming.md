---
title: "flash streaming vs vlc streaming?"
date: 2009-11-27
forum: General Help
---

### Post by skaldyr on 2009-11-27
i have a netbook with ubuntu and flash streaming from youtube is choppy, the sound is fine, but the picture stop and stutters.

vlc streaming mpeg4 is fine.

How could that be?

---

### Post by lovemylady on 2009-11-27
using firefox?, installed the plugins when there were some to install?

otherwise i just guess your pc cant handle it perhaps go processmanager and check when you open a video on youtube if it suddenly needs that much cpu.. 

but is youtube really flash streaming? hm no idea..

installed all the other video plugins etc.. ?
firefox up to date?

otherwise i got no idea

---

### Post by prem1er on 2009-11-27
> **lovemylady said:**
> using firefox?, installed the plugins when there were some to install?

otherwise i just guess your pc cant handle it perhaps go processmanager and check when you open a video on youtube if it suddenly needs that much cpu.. 

but is youtube really flash streaming? hm no idea..

installed all the other video plugins etc.. ?
firefox up to date?

otherwise i got no idea

I'm really not sure what this post is supposed to mean? YouTube is definitely using Flash to play videos. How did you install Flash on your system? And also what version of Ubuntu are you using?

---

### Post by skaldyr on 2009-11-27
its moblin(ubuntu 8.04). I have installed flash as i always do with gdebi.

cpu usage spikes to 91% when playing youtube in firefox.

---

### Post by skaldyr on 2009-11-27
cpu is atom z500 with a gma500 chip

---

### Post by snowpine on 2009-11-27
> **skaldyr said:**
> cpu is atom z500 with a gma500 chip

I am not familiar with Moblin/Ubuntu 8.04, so I'm unable to offer a specific solution.

gma500 may require a special driver; see here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by prem1er on 2009-11-27
> **snowpine said:**
> I am not familiar with Moblin/Ubuntu 8.04, so I'm unable to offer a specific solution.

gma500 may require a special driver; see here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

+1. Also, might want to try playing the video in another browser and check if you have the same issue.

---

### Post by ajgreeny on 2009-11-27
You say you installed flash with gdebi, but do not say which flash package it was.  If it was direct from adobe, then it should be the correct one, as it would be if it was the **adobe-flashplugin** or** flashplugin-installer** from the repos

However, check that you don't have any **swfdec** or **gnash** packages also installed as they can cause conflicts.  If you have either, remove them and try again.

---

### Post by lovemylady on 2009-11-27
> **prem1er said:**
> I'm really not sure what this post is supposed to mean? YouTube is definitely using Flash to play videos. How did you install Flash on your system? And also what version of Ubuntu are you using?

[COLOR=Magenta]I use Ubuntu 9.10 but not 100% lil modifield by friend (dont ask me what i got no idea lol)

Okay well i go to a website like "www.javachat.com" or so lol dunno if this exist and when i for example try to join the java chat on firefox's upper corner you will told that plugins are missing you click isntall blabla and done ^^

To install flashplayer use synapics or simply firefox while it popups and everything should be fine ^^[/COLOR] **kisses* xD*

---

### Post by ajgreeny on 2009-11-27
It isn usually better to install the variours plugins you need by going to Add/Remove or Software Centre, and searchin=g and installing from there, rather than trying to install from the plugin's site itself.

For example for java plugins go to **sun-java6-plugin** and choose install.  All may then be well with your needs.

---

### Post by lovemylady on 2009-11-28
[COLOR=Magenta]For me not, since then i would install plugins i do not need.. so i only install plugins through firefox only if i need them ;p[/COLOR]

---

