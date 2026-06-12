---
title: "KDE in Lucid shortly lost main speakers, left us headphones!"
date: 2010-09-22
forum: General Help
---

### Post by Jonny87 on 2010-09-22
I got my dad onto Ubuntu and he thinks its great. He's adamant that he's not going back to MS Windows.
However recently I got him to install KDE so that he could see a different environment. I think that was my mistake. since then hes lost his sound from his main speaker system. he can however get sound coming through headset. However if he unplugs his headset and plugs it back in, he looses the use of his Mic but still had sound, until this evening when I got him to try installing the Kubuntu desktop packages, lost the sound on the headset. this could be fixed by restarting the system.

We've tried looking through all the settings that we can but can't seem to find anything to help.

---

### Post by robsoles on 2010-09-22
Good show getting your Dad into Linux and helping him find it's worth.

I am not familiar with KDE but I've been pushing these things around for a while now and plenty better than me can be attracted to your thread with more info and catchier title!

Is it 10.04 LTS? Does the PC dualboot Windows?

Does the main speaker system work nicely from LiveCD or Windows?

Is it a certainty to you that KDE caused the loss of main speakers? (Was it immediate? for instance.)

Can you rename this thread? ("KDE in Lucid shortly lost main speakers, left us headphones!" seems good to me.)

---

### Post by Jonny87 on 2010-09-22
how do I rename the thread?
I can do it for this post.

---

### Post by robsoles on 2010-09-22
I just checked under thread tools in a thread I created and found I can't rename it, pity.

> **robsoles said:**
> ...

Is it 10.04 LTS? Does the PC dualboot Windows?

Does the main speaker system work nicely from LiveCD or Windows?

Is it a certainty to you that KDE caused the loss of main speakers? (Was it immediate? for instance.)

...

---

### Post by grahammechanical on 2010-09-22
I might be stating the obvious and as I don't use KDE I might be saying something stupid as well, but, is there not an icon for sound? There is one on the Gnome top panel. A left click gives the option to mute all. Underneath is Sound Preferences. Most of the tabs give an option to mute. May be, somehow, mute has been ticked. May be you have checked this out. If so, then I am sorry.

regards.

---

### Post by Jonny87 on 2010-09-22
Hi all, thanks for your suggestions.

> Is it 10.04 LTS? Does the PC dualboot Windows?
Yes it is the 10.04, and no its not dual booting.

> Does the main speaker system work nicely from LiveCD or Windows? 
He's apparently having trouble getting his computer to boot from CD, so this hasn't been tested yet though I have suggested it to him. With out me being over there to help him in person its kinda hard for me to know some details.

> Is it a certainty to you that KDE caused the loss of main speakers? (Was it immediate? for instance.)
I'd have to ask him how soon it happened but from what he's told me it only started happening since installing KDE. He originally installed the KDE-full package from the synaptic and all the other packages that it want with it. Then last night as another attempt, I told him to try installing the Kubuntu-desktop package etc from synaptic hoping that this may replace some altered file and hopefully fix what ever went wrong.

> is there not an icon for sound?
Yea there is such an icon. We've tried looking through all the setting with the available graphical tools but still no luck.

I was discussing it with a fella on skype who had seen this thread he suggested the following commands.
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
sudo apt-get install linux-backports-modules-alsa-lucid-generic

```

I was planning to try this next time I'm talking to my dad. Hes assured me that they won't make things worse. He referenced the following thread [http://ubuntuforums.org/showthread.php?t=1466096](http://ubuntuforums.org/showthread.php?t=1466096)

Though I'm wondering if the the backports one would be necessary?

---

### Post by SeijiSensei on 2010-09-22
Run "alsamixer" from the Terminal and check the volume settings for all the outputs.  Sometimes a critical one is muted or set to zero.  Then right-click on the speaker icon in the system tray next to the clock and choose "show mixer window".  This is the KDE app "kmix" which can sometimes have wrong or conflicting settings itself.  Your comment suggests your father's computer has multiple audio outputs.  My guess is that kmix is muting the one that connects to the audio system.

---

### Post by lisati on 2010-09-22
> **Jonny87 said:**
> how do I rename the thread?
I can do it for this post.

Done!

---

### Post by robsoles on 2010-09-22
> **lisati said:**
> Done!
Thanks lisati. I considered bringing it to mods attention via the resolution center but the thread attracted attention anyway.

> **Jonny87 said:**
> ...

I was discussing it with a fella on skype who had seen this thread he suggested the following commands.
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
sudo apt-get install linux-backports-modules-alsa-lucid-generic

```

I was planning to try this next time I'm talking to my dad. Hes assured me that they won't make things worse. He referenced the following thread [http://ubuntuforums.org/showthread.php?t=1466096](http://ubuntuforums.org/showthread.php?t=1466096)

Though I'm wondering if the the backports one would be necessary?

I wouldn't do the backports myself but the others may benefit by inclusion of '-f' flag (- actually means 'fix if possible', not 'force' in this command/case) in the apt-get install lines may help.

I would exhaustively try stuff suggested by others such as pressing through dialog boxes relating to sound settings such as muting and volume=0.

---

### Post by Jonny87 on 2010-09-23
> **SeijiSensei said:**
> Run "alsamixer" from the Terminal and check the volume settings for all the outputs.
Thanks, I just tried this on my own system out of curiosity. Never knew that you could that. quite neat I thought.

>  Your comment suggests your father's computer has multiple audio  outputs.  My guess is that kmix is muting the one that connects to the  audio system. 	
Yea I think there is multiple outputs.

> I would exhaustively try stuff suggested by others such as pressing  through dialog boxes relating to sound settings such as muting and  volume=0. 	
We've been doing this for some time now so thats why I started this thread.

---

