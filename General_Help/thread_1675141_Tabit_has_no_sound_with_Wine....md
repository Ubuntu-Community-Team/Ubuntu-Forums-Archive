---
title: "Tabit has no sound with Wine..."
date: 2011-01-25
forum: General Help
---

### Post by poodoopealeoaph on 2011-01-25
I have installed Tabit in my ubuntu 10.10 installation with wine (fully updated and configured) and i can not get any sound to output. I have FL9 installed with the same wine installation and I have no issues getting sound to output... Weird enough, I installed tabit in my unconfigured wine installation when ubuntu 10.10 first came out and it worked perfectly but now that I've formatted and reinstalled Ubuntu 10.10, I get no sound.

I would just like to add that I would just go to tuxguitar but my band members all use and are very comfortable with tabit so, if I can't get tabit to work, nothing else will work for me. Don't worry though, I love ubuntu and I'll stick with it on my laptop at all costs. I would just like the convenience of being able to use tabit and fl studio 9 while out of my room as to not wake up the wife and kid...

---

### Post by poodoopealeoaph on 2011-02-02
I've had this post up for a while now with no response.... surely there has to be someone out there that can figure out how to get sound to work with tabit in wine... if I can't find a fix for this then a few of my friends may be done with ubuntu. help!!

---

### Post by poodoopealeoaph on 2011-02-02
bump

---

### Post by poodoopealeoaph on 2011-04-02
In the case that anyone checks this out and needs to get Tabit to work on their Ubuntu system. I figured it out! Just go to synaptic manager and search for timidity. After installing timidity you can open tabit and go to Tools>Options>Play and change the midi output device to which ever timidity port you want to use.

---

### Post by strafe_sawdoffe on 2011-04-02
> **poodoopealeoaph said:**
> In the case that anyone checks this out and needs to get Tabit to work on their Ubuntu system. I figured it out! Just go to synaptic manager and search for timidity. After installing timidity you can open tabit and go to Tools>Options>Play and change the midi output device to which ever timidity port you want to use.

I wish I had found this post a few months ago; sorry no one responded. I use (love!) Tabit as well.

One little trick I stumbled across--I got sick of having to start the Timidity server after every reboot, so I added it as a startup process, like so:

System->Preferences->Startup Applications-> add: "timidity -iA"

Works beautifully with the occasional (minor) bug.

---

