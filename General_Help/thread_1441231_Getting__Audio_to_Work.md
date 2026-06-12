---
title: "Getting  Audio to Work"
date: 2010-03-28
forum: General Help
---

### Post by joemost on 2010-03-28
Hi,

I am a musician who just switched over to ubuntu studio. I was looking for some good software and what really caught my eye was ardour.

So I created a dual boot with Windows Vista and Ubuntu studio.... But anyway 

I have been having trouble getting audio to work. I cant seem to figure out, I tried every output system in the volume menu. I have a headset (which i know works) plugged in to my dell machine through the audio jack (you know the green one). So what should I change the sound as for the audio to come out of my headphones.

Thanks for the help,

Joe

Sorry Please Pardon my noobness :)

---

### Post by mac666 on 2010-03-28
Check this out: 
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by cchhrriiss121212 on 2010-03-28
I don't think you need to get involved in upgrading alsa just yet. Are you having trouble with just Ardour or everything on the OS? Pulse is the default audio controller, but it is not very good so download alsa mixer instead.

Audio production with Linux/Ubuntu Studio means you will be using jack most of the time, a sound server that allows you to connect every audio program to each other and to your audio inputs and outputs (Ardour for example will not function without jack). Unfortunately jack is very frustrating for new users as it does not work out of the box on any machine. You can find it in the applications>sound menu.  
Put this in a terminal to get jack to run when you press start:
 ```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
```

---

### Post by joemost on 2010-03-29
Ok so I should open up Jack to deal with input and output devices? Does that include USB? Also, my Dell Inspiron (what I am running ubuntu studio on) does not have a built in wifi, I have a Usb card that picks up the wifi..... But it does not come up in the Internet connection, like it would in ubuntu ( I used to use ubunu)

---

### Post by cchhrriiss121212 on 2010-03-29
You need to install network manager, studio doesn't have it as wireless connections will interfere with your audio processing. Keep that in mind if you plan to use wireless all the time.

Jack can handle usb midi devices, is that what you mean? Or do you have a usb recording interface you want to use? You can check the alsa database for compatable interfaces.

---

### Post by joemost on 2010-03-29
I am gonna have to use WiFi for network, thats my only way
 
My mic is a fairly simple Logitech USB Microphone,

---

### Post by joemost on 2010-03-29
Can I have a link to the two applications u recomended I download, I I'll have to download them on my pc then move them into the other hardrive

---

### Post by joemost on 2010-03-29
How do I download Ubuntu Network Manager for Ubuntu.

---

### Post by cchhrriiss121212 on 2010-03-29
You will need to get access to a wired internet connection and then download network manager from synaptic.

Your mic may be recognised by jack but it might not, you will have to plug it in and check the connections window. Not all hardware is supported on ubuntu.

---

### Post by joemost on 2010-03-29
I have some pretty big usb drives, anyway I have some big portable file storage, is there anyway I could bring it in that way. Download it on my computer that has connection, and bring it in through USB

---

### Post by cchhrriiss121212 on 2010-03-29
Yes, but you would have to download the source files and compile it yourself, which you might not find easy if you don't use much terminal commands. If you want to have a go at that then look up the gnome network manager website. I don't recommend this.

Or. if you have a live cd of a regular ubuntu release you could just put that in the drive and load it as a software source from synaptic, and install network manager from there. Network manager may even be on the studio dvd somewhere, so give it a try first.

---

### Post by gordintoronto on 2010-03-29
> **cchhrriiss121212 said:**
> Yes, but you would have to download the source files and compile it yourself....

This is not true.

[http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/)

---

### Post by joemost on 2010-03-29
Lucky for me I do have Ubuntu on a live cd so I will
do that.

---

### Post by joemost on 2010-03-30
I did what I said and searched For network manager on the ubuntu live cd, it came up with a package called libnm-glib0 , I clicked on it and it said mark for reiinstallation, installation was faded, does this mean I already have network manager?

---

### Post by cchhrriiss121212 on 2010-03-30
That is not it, you need to install two packages: 'gnome network manager' and 'network manager'.
You need to reload the sources once you have added the cd as a source.

---

### Post by joemost on 2010-03-30
Oh..... I did not do that,
 
Thanks 
 
Also, how I am supposed to Get Jack to Work?

---

### Post by cchhrriiss121212 on 2010-03-30
> Network manager may even be on the studio dvd somewhere, so give it a try first.

I just checked this out and you can find this on the studio dvd under pools/main/n/.

Regarding jack, I gave you a good start with it in the 3rd post of this thread. Have you tried starting jack up yet?

Post any errors you are getting.

---

### Post by joemost on 2010-03-30
It says I already have network manager installed, but there is nothing in my menu called network manager

---

### Post by cchhrriiss121212 on 2010-03-30
OK but what about gnome network manager? This will be GUI that will show up as an icon on the right of your taskbar. You can also add network manager to your startup applications in the preferences menu.

---

### Post by joemost on 2010-03-30
I searched for gnome network manager..... Nothing, it says I have network
network managger installed, i have the package u told me to get o. The cd installed, network manager comes upmas network manager in the menu right, Also.... Where do
I go to edit the startup program?I
looked in the preference memu but couldn't find it

---

### Post by cchhrriiss121212 on 2010-03-30
It should be Preferences>Startup Applications.

I take it you have a Studio dvd somewhere? If so put it in the drive. Following on from my earlier post here is the exact location of gnome network manager on the dvd:
/media/cdrom0/pool/main/n/network-manager-applet
Just click on the debian package and it will install. Then you can change startup applications.

---

### Post by joemost on 2010-03-30
> **cchhrriiss121212 said:**
> It should be Preferences>Startup Applications.

I take it you have a Studio dvd somewhere? If so put it in the drive. Following on from my earlier post here is the exact location of gnome network manager on the dvd:
/media/cdrom0/pool/main/n/network-manager-applet
Just click on the debian package and it will install. Then you can change startup applications.


I am in the "n" folder..... There is a folder called network manager but does not have the applet as part of the name... I clicked the folder and inside was like this thing called:

libnm-glib0 (then a bunch of numbers) I clicked on it and the status says it's already been istalled

also I looked in preferences and there is no startup programs

---

### Post by cchhrriiss121212 on 2010-03-30
OK lets get some basic info here.
What OS do you have installed? Karmic? 
Did you download the studio image or did you upgrade from a regular ubuntu?
What is the name of the dvd you looked on for network manager?

---

### Post by joemost on 2010-03-30
> **cchhrriiss121212 said:**
> OK lets get some basic info here.
What OS do you have installed? Karmic? 
Did you download the studio image or did you upgrade from a regular ubuntu?
What is the name of the dvd you looked on for network manager?

the os is ubuntu studio? Right? I downloaded the ubuntu studio image, so whatever comes wiu that image is what I have.

---

### Post by cchhrriiss121212 on 2010-03-30
I don't know what version you are using and I don't know where you downloaded it, you can check by opening system monitor from the system>administration and looking under the system tab.

I'm asking you this because I definitely have a startup applications entry in preferences. I also have a 9.10 (thats karmic) studio image with gnome network manager on it. Do you know whether it is a 32 or 64 bit image? You could check restricted as well as main in the pools folder on the dvd.

Is there a way you could get this machine to a wired internet connection?

---

### Post by carlosgs91 on 2010-03-30
.

---

### Post by joemost on 2010-03-30
Yeah maybe I will just switch to ubuntu, everything seems to work when I use it.... But it will
not let me install Ardour, is that because I don't have Jack already?

---

### Post by joemost on 2010-03-31
It will not allow me to download Ardour in Ubunutu..... Is this because I do not have jack already installed?

---

### Post by cchhrriiss121212 on 2010-03-31
You will definitely need jack to run ardour, and if you use synaptic they can both be pulled in at once.
If you get an error like this in the future try to post what the error actually says otherwise it is hard to help you fix it.

---

### Post by joemost on 2010-03-31
Hi,

Okay I am in Regular Ubuntu in the add software program, I have internet, as a matter of fact i am writing this from ubuntu, but I am having a problem, when ever i click jack to add it (or any other program,) a message comes up that says ; Click on 'Reload' to load it. To reload the list you need a working internet connection. 

So I click reload (and have a working internet connection) but it gives me that same message. What do I do?

---

### Post by cchhrriiss121212 on 2010-03-31
Like I said earlier, just use synaptic. You will find it in system>administration>synaptic package manager. The add software program is OK but it will not satisfy any dependencies.

---

### Post by joemost on 2010-03-31
Okay thanks..... I have another question, when I use ubuntu for somereason it slides a little bit of the desktop( well actually everything) to the left, leaving this black space on the right of the screen, my moniters reseloution is 1440 by 900, how do I get the desktop
to slide over ( Note: I have Linux on 1440 by 900 reseloution allready)

---

### Post by cchhrriiss121212 on 2010-03-31
Not sure about that, it sounds like an xorg configuration thing. Best start a new thread in hardware or general help.

---

