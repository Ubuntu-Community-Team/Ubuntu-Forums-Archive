---
title: "Error when connecting iPod Touch 4G"
date: 2010-12-28
forum: General Help
---

### Post by brettansley on 2010-12-28
Hi

I just installed Ubuntu 10.10 but when I pug in my iPod Touch 4G I get the following error message:

Unable to Mount Brett's iPod
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

Can anyone help me get get this working please?

Thanks

---

### Post by tredegar on 2010-12-28
Do you have the following installed?
[B]libgpod4
libgpod-common
usbmuxd
libusbmuxd1
libmobiledevice0
rhythmbox-plugins
libplist1
rhythmbox[/B]

My itouch works fine with 10.04.

---

### Post by brettansley on 2010-12-28
All of the above were already installed as part of 10.10 - I've tried apt-get install for each of them but have already got the latest versions.

---

### Post by Spyderkid on 2010-12-28
ubuntu restricted extras might be worth downloading...

it might enable file types which you don't have, which you need to charge your ipod 4g

I have the iPod 2g and it works fine with it.

---

### Post by tredegar on 2010-12-28
And there's a long thread [here]("http://ubuntuforums.org/showthread.php?t=1628529") about itouch problems and solutions.

Mine is running version 1.1.5 (4B1). It hasn't been connected to itunes for a couple of years I'd guess. So maybe it is so out of date it can't fail to work?

---

### Post by brettansley on 2010-12-28
Hi

Thanks for the link - lots of great stuff. 

I can now successfully mount my iPod G4 on 10.10 Linux 2.6.35-24-generic

But I still cannot get RhythmBox to recognise the device - I can see it in PCMan but not in Rhythmbox.

Any other ideas?

Thanks

---

### Post by tredegar on 2010-12-28
> I can now successfully mount my iPod G4 on 10.10 Linux 2.6.35-24-generic

Good progress. Congratulations.

But it would be helpful to others reading this thread if you posted here, what worked for you, and even reasons for your understanding of *why* it worked for you.
> But I still cannot get RhythmBox to recognise the device - I can see it in PCMan but not in Rhythmbox.

I don't know what PCMan is, but when my itouch is plugged in there's an icon on my desktop, and both rhythmbox and clementine can see and use the device.

Perhaps the difference is that you are on 10.10, while I am running 10.04[COLOR="Red"]LTS[/COLOR]
and my itouch hasn't been "updated" (perhaps read as "re-broken") by apple for *years*, but yours is "current".

"Bleeding edge" or "Stable"? "*You pays your money and you takes your choice.*" [*1846 Punch X. 16*]

To be honest, I never use my itouch. It was given to me several years ago as a well-intentioned gift. It has proved itself to be a source of continual (minor) annoyance, because I run only linux, and when I am bored, I wonder "Does that itouch thing work yet?", and then I play with it. Right now it is working, but in the light of my experiences with it, I will never buy an apple product. Ever. 

There are many (cheaper) itouch equivalents out there that work very happily with linux. If I needed one, I'd go and buy one.

Apart from the obvious (make more searches) I cannot offer you any further advice at the moment. Sorry.

Hope you get your problem(s) fixed. Please post a follow-up when you make progress.

Good luck.

---

### Post by brettansley on 2010-12-29
Finally everything is working correctly!!

What worked:

QUOTE=migmruiz;10208430]Step-by-step workaround

Add the ppa to your repos
```

sudo add-apt-repository ppa:pmcenery/ppa

```
then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```

That worked for some people, 
if it DIDN'T for you, install libimobiledevice-utils
```

sudo apt-get install libimobiledevice-utils

```
and then run from the command-line
```

idevicepair unpair
idevicepair pair
idevicepair validate
```[/QUOTE]

Then:

```
gksudo gedit /etc/fuse.conf
```
Change

#user_allow_other
to

user_allow_other
Save and exit.

Then open Rhythmbox go to Plugins and enable the iPod plugin. Restart Ubuntu and everything works great!

Thanks for the help all

Brett

---

### Post by donmatas on 2010-12-31
Thanks bro

I did this:
```

sudo add-apt-repository ppa:pmcenery/ppa

```
then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```

Then I reboot and plugged in the Ipod. The Ipod icon appeared in the desktop. I double clicked it and a window showing the Ipod's content has opened. I press the Rhythmbox botton on the bar of the window and Rhythmbox ran. I tried to put some songs on the Ipod and it looks that it was working, but after unmounting the Ipod I could not be able to find the songs on it. 

Do you have any idea about what happened?

thanks for your help and have a happy new year

DM

---

### Post by prettymess on 2011-01-05
> **donmatas said:**
> Thanks bro

I did this:
```

sudo add-apt-repository ppa:pmcenery/ppa

```
then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```

Then I reboot and plugged in the Ipod. The Ipod icon appeared in the desktop. I double clicked it and a window showing the Ipod's content has opened. I press the Rhythmbox botton on the bar of the window and Rhythmbox ran. I tried to put some songs on the Ipod and it looks that it was working, but after unmounting the Ipod I could not be able to find the songs on it. 

Do you have any idea about what happened?

thanks for your help and have a happy new year

DM
Having the same problem, anyone have any suggestions?

---

### Post by donmatas on 2011-01-05
come on dudes!
I am sure that there are a lot of ubuntu users that are running their Ipod 4g without any problem... please help!

---

### Post by En1alessej on 2011-01-15
Thanks, Brett! The first solution you posed allowed me to finally mount my ipod touch running Ubuntu 10.10. Appreciate these steers in the right direction as a nubie.

Here's what you suggested that I used successfully:
Add the ppa to your repos
 	Code:
 	sudo add-apt-repository ppa:pmcenery/ppa 
then update and upgrade your packages
 	Code:
 	sudo apt-get update
sudo apt-get upgrade

---

### Post by donmatas on 2011-01-18
> **En1alessej said:**
> Thanks, Brett! The first solution you posed allowed me to finally mount my ipod touch running Ubuntu 10.10. Appreciate these steers in the right direction as a nubie.

Here's what you suggested that I used successfully:
Add the ppa to your repos
 	Code:
 	sudo add-apt-repository ppa:pmcenery/ppa 
then update and upgrade your packages
 	Code:
 	sudo apt-get update
sudo apt-get upgrade

I will try it with Maverik and then I will inform

NEW REPORT: same problem

---

### Post by ions on 2011-01-30
Same problem here. I hate Apple and the world in which they're actually the best choice. It's insane.

---

### Post by donmatas on 2011-02-01
> **ions said:**
> Same problem here. I hate Apple and the world in which they're actually the best choice. It's insane.

Ions: I am 100% agree with you.

salud
DM

---

