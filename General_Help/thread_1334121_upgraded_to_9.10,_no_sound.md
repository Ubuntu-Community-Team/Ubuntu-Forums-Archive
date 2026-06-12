---
title: "upgraded to 9.10, no sound"
date: 2009-11-22
forum: General Help
---

### Post by miggerish on 2009-11-22
Hi,

I upgraded to 9.10 and ever since then my computer does not play any sound from the internet like youtube, etc.. and also it does not play sound from the application called "KAlarm."  I think it is problem with sound card, I have one called "NVidia."  

Here is the dialogue in a screenshot image of when I tested an alarm sound using KAlarm: 
[br]

[[IMG]http://img690.imageshack.us/img690/8759/screenshoteb.th.png[/IMG]](http://img690.imageshack.us/i/screenshoteb.png/)

[[IMG]http://img692.imageshack.us/img692/6613/screenshot1ns.th.png[/IMG]](http://img692.imageshack.us/i/screenshot1ns.png/)

Also, everytime now when I want to watch a youtube video with sound, i wait till the video loads in my browser, then I navigate to "/tmp" and I find the video file and I open it with "Movie Player" and then the sounds works fine in movie player.  But for some reason, after the upgrade to 9.10, sound does not work in internet or KAlarm.

Thanks,  Any help solving this will be appreciated.

---

### Post by camaron1 on 2009-11-22
No it is more likely a Pulseaudio problem. Just a clarification, by your pictures it looks like you might be running Kubuntu....? Could you clarify this please?

---

### Post by miggerish on 2009-11-22
> **camaron1 said:**
> No it is more likely a Pulseaudio problem. Just a clarification, by your pictures it looks like you might be running Kubuntu....? Could you clarify this please?

No it is actually Ubuntu.  At least that's what it says every time I log in in a Big Logo: "ubuntu".

Okay, so i am not very experienced.  What is pulse audio, and how to go about fixing it?  want me to do any terminal commands and show you the results?

thanks

---

### Post by camaron1 on 2009-11-22
> **miggerish said:**
> No it is actually Ubuntu.  At least that's what it says every time I log in in a Big Logo: "ubuntu".

Okay, so i am not very experienced.  What is pulse audio, and how to go about fixing it?  want me to do any terminal commands and show you the results?

thanks
give me a minute

---

### Post by miggerish on 2009-11-22
> **camaron1 said:**
> give me a minute

Okay.  Thanks for taking the time to help me.

---

### Post by cliffbreaker on 2009-11-22
I had some trouble with sound too. Consider removing pulseaudio - it's getting worse and worse with each new version. So do aptitude remove pulseaudio and I hope it fixes your trouble.

---

### Post by camaron1 on 2009-11-22
Right before you do anything I need to insist: the pictures you provided are from KDE applications, that's why I asked about Kubuntu. Did you installed these on your Ubuntu machine or where they there by default? I particularly refere to KDE Control Module, as it is obviously an application to manage multimedia settings...
 
If it is definitely Ubuntu that you have installed the following 3 things have helped many people in getting their sound back in Ubuntu Karmic (myself included). Try them in order.


1-Check on volumen applet on the top right to make sure the volume is not muted (sorry if ti sounds stupid). If it is no muted:

2-Open a terminal and copy and paste this:
[B]
gksudo gedit /etc/pulse/default.pa[/B]

On the text editor go to preferences and choose to display line numbers. On line 45-46 you should probably see:
45 # load-module module-alsa-sink
46 # load-module module-alsa-source device=hw:1,0

Remove the sign **#** from both. Save the document and reboot. 

If this has not worked either:

3- Open synaptic and totally remove Pulseaudio (and a few dependencies that will go too). If it says it will remove Ubuntu-desktop dont worry, you can install that later (It is just a metapackage not the actual desktop)

I you are not totally sure whether you have Ubuntu or Kubuntu (you could have got wrong splash screen) don't follow the above as I've never used Kubuntu

---

### Post by miggerish on 2009-11-22
> **camaron1 said:**
> Right before you do anything I need to insist: the pictures you provided are from KDE applications, that's why I asked about Kubuntu. Did you installed these on your Ubuntu machine or where they there by default? I particularly refere to KDE Control Module, as it is obviously an application to manage multimedia settings...
 
If it is definitely Ubuntu that you have installed the following 3 things have helped many people in getting their sound back in Ubuntu Karmic (myself included). Try them in order.


1-Check on volumen applet on the top right to make sure the volume is not muted (sorry if ti sounds stupid). If it is no muted:

2-Open a terminal and copy and paste this:
[B]
gksudo gedit /etc/pulse/default.pa[/B]

On the text editor go to preferences and choose to display line numbers. On line 45-46 you should probably see:
45 # load-module module-alsa-sink
46 # load-module module-alsa-source device=hw:1,0

Remove the sign **#** from both. Save the document and reboot. 

If this has not worked either:

3- Open synaptic and totally remove Pulseaudio (and a few dependencies that will go too). If it says it will remove Ubuntu-desktop dont worry, you can install that later (It is just a metapackage not the actual desktop)

I you are not totally sure whether you have Ubuntu or Kubuntu (you could have got wrong splash screen) don't follow the above as I've never used Kubuntu

Thanks, I am 100% sure it is Ubuntu.  To answer your Question, it is an application which did not come by default, I manually installed "KAlarm" on my machine.  Does it make sense to you that it doesn't make sound from "KAlarm" application or from internet browsing like youtube, but it still plays sound for other apps like music and such?

---

### Post by camaron1 on 2009-11-22
> Thanks, I am 100% sure it is Ubuntu. To answer your Question, it is an application which did not come by default, I manually installed "KAlarm" on my machine. Does it make sense to you that it doesn't make sound from "KAlarm" application or from internet browsing like youtube, but it still plays sound for other apps like music and such? 

I'm very sorry I think I totally misread your post, I thought you didn't get any sounds at all. So you can play your music on the computer but not from the internet?

---

### Post by miggerish on 2009-11-22
> **camaron1 said:**
> I'm very sorry I think I totally misread your post, I thought you didn't get any sounds at all. So you can play your music on the computer but not from the internet?

Correct.  Some apps work with sound, most don't.  For example, a video being watched on youtube in the firefox browser does not play sound.  However, if I go into the "/tmp" folder, where the temporary youtube video file is located, and I open it using "Movie Player," the sound works fine in that application called "Movie Player."  Same with a few other apps such as banshee media player.  But in the application called "KAlarm," the sound does not work just like in firefox and it even pops up the dialogue about my sound card which I just showed you in the screenshot.

---

### Post by camaron1 on 2009-11-22
OK, there are probably two different issues here. A general sound problem and some issues with KDE applications. In my experience KDE sound applications are not well integrated in Ubuntu.

I still think though that you should try my advise above. Give it a go and see how it works. (Also I'm supposing that you've got flash installed eh, that is the first thing to do really...)

Tell us how it goes

---

