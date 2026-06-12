---
title: "External Speakers Not Working on uBuntu 10.10"
date: 2011-04-03
forum: General Help
---

### Post by rohitink on 2011-04-03
I have a Lenovo ideapad z560 and have windows and UBuntu both installed on it.

I have an External speaker which can be connected to the Laptop through the 3.5mm Jack.

The speaker works Flawlessly in Windows System but in Ubnutu They Just Won't Work.

I have Searched Almost Everywhere. But Couldn't Find a Solution.

My Ubnutu Version is 10.10

Reading some other similar post, i have done this. Run this Command in Terminal.

> wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh


here is the output:

> [http://www.alsa-project.org/db/?f=1b68b0aefe94bcedf4d0e286858bd66240db0ae0](http://www.alsa-project.org/db/?f=1b68b0aefe94bcedf4d0e286858bd66240db0ae0)

Any help would be Highly appreciated.
:(:(:(:(:(:(

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

This Thread has been [COLOR="Red"]**Solved**[/COLOR]. I am So happy.

I am writing the solution as many people have this problem over here.

Following Was the procedure i did.


Using Terminal
Open this file for editing:

```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```

Insert this line at the bottom:

```
 options snd-hda-intel model=thinkpad 
```
(This will work if you have an Intel Processor, I Have Intel Core i5)

Save. Close. Reboot. 

Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Thanks to Lidex for His Wonderful Help, which he is providing to The Forum Community.

---

### Post by bingmicrosoft on 2011-04-03
1 more exp, that is very simple ?

---

