---
title: "Replacing Ubuntu with Windows"
date: 2011-05-24
forum: General Help
---

### Post by benwalburn on 2011-05-24
I'm sorry if this has already been asked a million times, but I want to get the facts straight before screwing anything up.

I am getting fed up with my windows vista and so am considering installing Ubuntu on my laptop. 

I need to know the best way to install, how much memory it takes (for when I download it) and any major technical issues I might come across. (Such as loss of the ability to connect to the internet)

I am running a dell laptop, on vista. I don't know the specs.

Thank you

---

### Post by linuxinstalledfromhdd on 2011-05-24
Try it with 10.10 first. 

Here is a nice walkthrough, and if you get stuck let us know..

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

This is identical to mine.  You should be relatively ok. :guitar:

---

### Post by dFlyer on 2011-05-24
First what version of Ubuntu do you want to run?

My guess is if your running vista you have plenty of memory to run Ubuntu, but how much memory do you have?

So you have a Dell Laptop - What model? Is it 32 or 64 bit processor?

Are you planning on dual booting or completely replacing windows vista?

Have you used linux before?

Have you downloaded a Live Desktop CD and tried it?

---

### Post by airspoon on 2011-05-24
You should download Ubuntu (I have 11.04) on to a CD or USB thumb-drive, then boot up from that CD or thumb-drive to see if you like it. If you do, the install is a snap and you can do it from that same CD or thumb-drive. I just did it last week and I couldn't be happier. In fact, I haven't once gone back to Windows yet (except for work, where I use Adobe software on both Mac and Windows).

If you have enough RAM for Vista, then you should have enough RAM for Ubuntu.


--airspoon

---

### Post by linuxinstalledfromhdd on 2011-05-24
And if you get really hard-up for Windows again after installing Ubuntu, you can always use your original Windows disc to install it in Virtualbox 4.  That's what I did.

---

### Post by benwalburn on 2011-05-24
You are all being very helpful, and prompt lol.

I'm running 32 bit, for whoever asked.
I want to completely rid myself of Windows. Trying out Ubuntu first sounds good, but I doubt my computer can take it. (CPU maxes out a few minutes in to booting,) If it's possible, I would like to try it out somehow. And I don't have the windows disk

My big question now is what size cd/flash drive do I require?

---

### Post by ryan! on 2011-05-24
the iso is 700 mb so a cd-r or a 1 gb flash drive would work

---

### Post by linuxinstalledfromhdd on 2011-05-24
Let's try the other end of the spectrum..

Try Crunchbang 9.04.. Google it.. Download it.. Burn it.. Boot from it. 

Let us know the results. :) 

Cheers.

---

### Post by airspoon on 2011-05-24
I believe you need a 2gig thumb-drive. If you go to [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) , it should have some very clear and easy to follow instructions on how to try Ubuntu 11.04 from a CD or thumb-drive before installing it. Or, just head over to Ubuntu.com and click on 'downloads' for an earlier version.

Windows Vista uses a lot of resources (RAM etc...) so if your computer handled Vista, it should do just fine with Ubuntu. With that being said, I'm far from an expert. I was however in your shoes a week ago. Ubuntu has been great for me and I'm glad I made the jump.


--airspoon

---

### Post by benwalburn on 2011-05-24
Ok, I'm going to hope a 1gig is enough, my 4gig is missing.

I'm going to try v10.10 (the first link posted) from the directory, do I download all the files to the root of my sd card, or what?

---

### Post by linuxinstalledfromhdd on 2011-05-24
It sounds like their system is ancient, perhaps..  Let them try a couple lite versions and see if they can at least boot into something that we can work with.

---

### Post by benwalburn on 2011-05-25
Ok, I managed to get Ubuntu v11.4 on my 1gig flash drive. For the sake of the people who use my computer, I'm not going to replace Windows Vista yet.

I noticed that Ubuntu works fine on my computer, but when I tried on another, I encountered severe graphics issues. Is there any way I can fix this, or is Ubuntu incompatible with that computer?

Also, I could not connect to the internet with my Verizon MI-FI. Can anyone tell me how to configure it?

---

### Post by jim_deadlock on 2011-05-25
Graphics and wireless are the two most common issues with new installs. I've found that as long as I have a wired connection during install, all the necessary drivers are automatically downloaded during all the updates you have to do immediately after the install, after that everything is usually fine.

---

### Post by airspoon on 2011-05-25
I too had graphics problems on my computer with 11.04 and deduced that it is a problem with the third party driver, particularly Nvidia. That computer doesn't happen to have an Nvidia graphics card, does it? Even still, there is a quick and simple work around. 

For me (and many others), the solution is to login to Gnome Classic. After clicking on my name in the login screen, an option becomes available at the bottom of the screen to choose environments.

As far as I know, that is the only work around at the moment, though due to the large number of people with this issue, I'm sure it will be resolved fairly quickly.

Just after installing Ubuntu and running into that problem, I started a thread about it and got back some pretty informative replies. It might help you to read some of those replies and follow the subsequent links. The thread is here: [http://ubuntuforums.org/showthread.php?t=1759635](http://ubuntuforums.org/showthread.php?t=1759635)

Good luck!

---

### Post by yangli on 2011-05-25
Try a live CD first to see if there are any issues.

---

### Post by LordNeo on 2011-05-25
Ok, Straight forward.

1. Get Ubuntu 11.04 into a Pendrive following the instructions here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
(In Step2, select "USB stick" and then click "Show me how")

While doing it, select at least some MB for a persistence file, so you can "save changes" into the pendrive

2. Boot from that pendrive while you are connected wired to internet, go to the dash (or press "Win" key) and search "Drivers" it should show you the application for aditional drivers (sorry, i'm using it in spanish, so i don't know the actual name in english) where you will find if you need to download and install graphic and wireless drivers.

PD: Those will be saved in the pendrive so it will persist after reboot

3. Once installed, reboot the computer and boot again from the pendrive and you should be able to use graphics and wireless easily.

Best regards

---

### Post by airspoon on 2011-05-25
Before installing, I tried a "live-thumbdrive" and Unity worked perfectly. It wasn't until I actually installed it on my HDD, that I found the driver conflict. So, at least from my own experience, a live-CD won't do any help for resolving that particular graphics issue (if it's the same issue that I -and may others- have).

---

### Post by benwalburn on 2011-05-25
I'll do that as soon as I can make the internet work. I have to play with the settings because it seems that Ubuntu does not have a wi-fi scan. Or does it?

---

### Post by benwalburn on 2011-05-25
Now I'm trying to boot it again from the computer it worked on. It loaded fine, but my cord got unplugged and I lost power. Now I can't get Ubuntu to load. It gets as far as the purple Ubuntu screen, then it goes black and nothing happens. Hoe do I fix this?

My Windows had a problem similar to this. It would freeze on the Welcome screen and I would have to use ctrl alt delete to get past it.

---

