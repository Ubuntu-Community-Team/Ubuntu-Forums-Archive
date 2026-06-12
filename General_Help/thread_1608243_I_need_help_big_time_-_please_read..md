---
title: "I need help big time - please read."
date: 2010-10-28
forum: General Help
---

### Post by Wayne1987 on 2010-10-28
p { margin-bottom: 0.08in; }  

          Okay hey guys, first off I would like to say thanks for helping me, okay I'm new to Linux Ubuntu.  I used windows, pretty much all my life but I hate how greedy Microsoft has become soo I moved on to linux.  But, I will need help I hope you guys are up for this, again thank you.
 

 

    So I got Linux Ubuntu installed today, everything seemed fine until I tried to install an A/V program or even a Firewall.  Nothing worked, but the command type thing on here is really nice I've been using that to try and install a proper codec or media player.  But, to be disappointed I found their was no sound at all, I was searching and searching the web to try and maybe fix it may self without bugging you guys.  But sorry, couldn't get it done.
 

   My sound comes from 2 places and right now I just mainly use an old stereo that has a usb port so I just take a usb cord and plug it into my stereo and pc usb port.  But, I'm not seeing the pc picking it up , the stereo its self has a PC mode and its set, aswell says its connected correctly but no sound even while being maxed out.
 

   So, what I really need help on is, getting the sound to work, a proper A/V and Firewall that works then a media player with k-lite codec mega pack.   
 

  This is all I need help with, if somebody could help me that would be awesome, thank you.

---

### Post by ivarn on 2010-10-28
Hey and welcome. 
First of all, there's no such thing as virus in linux so scratch the AV.
UFW (ubuntu firewall) is already installed but disabled by default since you will only need a firewall if you run a server. I've never used it so I don't remember how to turn it on / off.
Also, all the codecs for video/audio and flash you need will be installed if you run this code in the terminal:
sudo apt-get install ubuntu-restricted-extras
Also, here's a command for a program that will let you run the terminal from the right-click menu:[FONT=monospace]
[/FONT]sudo apt-get install nautilus-open-terminal

---

### Post by Wayne1987 on 2010-10-28
I have the media player now, but still no sound at all not even a crackle of a sound.

---

### Post by ivarn on 2010-10-28
go to system > admin > system test.
See if that can help you.
If not, please come back and tell us what sound card you have.
Also, see if the audio is just muted in the volume control settings.
Just click the volume button on the panel.

---

### Post by Wayne1987 on 2010-10-28
I got the sound to work now, but the sound in the stereo still doesn't work is this because its set up usb?   

  It worked fine on windows, but it should work on here shouldn't it? 

As well, when I play my video it seems to be a little laggy/ off set.

---

### Post by ivarn on 2010-10-28
Ok so the audio is not in stereo?
Well, if you go to the volume controller settings and the tap that says hardware, you'll see a drop down menu next to where it says profile. These are different sound profiles such as input/output stereo or mono, joint or surround etc.
And what video player did you choose?
VLC should work just fine to almost every video and audio format.

---

### Post by Frogs Hair on 2010-10-28
If you would like a fire wall install Firewall Configuration from the software center and select enable . It will appear on the administrative menu after installed.

---

### Post by Wayne1987 on 2010-10-28
That worked..

Okay, now how can I make my video look smooth less skipping/ laggy.

I've never had an Issue with lag or video skips, I've seen a lot free software Linux gives away for free .. but ... 25% of it doesn't work...

  Okay, I still can't play MKV or M2TS video files, and I can't see to install nero, would their be any software I could use that would allow me to burn cd or dvds for linux that works?

 Oh yeah, I almost forgot...

  Does Linux have anything to hide your IP address or ISP with?

How do I change my theme on the desktop?

Last thing, where can I find software to teach me on scripting .vbs and .bat files

I really would like to learn that, when I had windows thats what I was on.

I really thank you for helping me.

---

### Post by oracle2b on 2010-10-28
For CD/DVD burning **"[Brasero]("http://projects.gnome.org/brasero/")"** should already be installed. I like using two media players VLC and Smplayer.

 To change your theme go to *System->Preferences->Appearance*.

 You can use [Tor]("http://www.torproject.org/download/download.html.en") to obfuscate your internet traffic from your ISP.

Edit: Many people prefer using K3b for burning CD/DVD but you'll end up installing some KDE libraries also.

---

### Post by ivarn on 2010-10-28
TO change your desktop theme, right click > change the background > theme, or you can go to *System->Preferences->Appearance*.
You'll find themes on sites like gnome-look.org.
Also, yes there are add ons for firefox that will let your hide your ip or use proxy.

---

### Post by tripmix on 2010-10-28
Hi, I cant say I know why your usb sound don't work but I can give you some useful noob commands for dealing with hardware in linux. First of to get a list of your usb and pci devices you can run these commands "lsusb" and "lspci", to get a list of all the modules (nix for drivers) you can run "lsmod". Thats useful to find out if everything is connected and detected properly, it usually will be. Most audio hardware in linux use alsa (advanced linux sound architecture), you can run "alsamixer" and press f6 to control separate soundcards (there are lots of gui mixers too if you prefer). Sorry for being all console but I use kde so I don't know so much about gnome.

---

### Post by Wayne1987 on 2010-10-28
sweet guys, thanks.
Everything, worked.

Is their any software to make Java, PUP, VBS  Scripts?

I would like to learn how to write code, that would be the main reason I want linux and that would be to learn and do more then windows could ever do.

But if there isn't anything I guess I'll just get some books or something on it, but thanks for the help guys, it really did help.

^_^

---

### Post by Wayne1987 on 2010-10-28
> **Frogs Hair said:**
> If you would like a fire wall install Firewall Configuration from the software center and select enable . It will appear on the administrative menu after installed.

My Firewall is called

KMyFirewall, This program isn't set up right at all and I don't have any idea how to config it at all, but oh well I guess it doesn't matter too much.

---

### Post by Wayne1987 on 2010-10-28
Okay I have something else I would like to ask.

Is there any software like (ccleaner)

[Adding In]

Where do I find, the add-on for FireFox to hide my IP.

The software that was posted on here, about hiding it didn't work I couldn't even find the .exe file.

---

### Post by CharlesA on 2010-10-28
Linux is not Windows.

Most of the stuff you were required to use in Windows is irrelivent in Linux.

See [here]("http://ubuntuforums.org/showthread.php?t=510812") for info on security.

Just use ufw or gufw to configure the firewall.

As for something like ccleaner - check out bleachbit.

---

### Post by Wayne1987 on 2010-10-28
:edit:
sudo apt-get install bleachbi

I love this! lol
----------------


Thank you!

  Now lol

Is there software to encode an avi file to dvd? 

and 

Software to encode an Mkv to M2TS

Like I said before I'm done, very done with windows, I'm sick of fighting viruses all the time.

Windows=Sickening 

Thank you guys,
You all rock !

---

### Post by themusicalduck on 2010-10-28
To write an avi file to a dvd you could try DeVeDe. It's in the Software Centre or through apt-get. Also if you haven't looked in there yet, there's lots of software you can install through there by searching for it.

I don't know if you've fixed your laggy video problem yet, but just in case, check System > Administration > Additional drivers and you might be able to install a better video driver.

Here's a good guide for new users - [www.ubuntu-manual.org](www.ubuntu-manual.org)

---

### Post by Wayne1987 on 2010-10-28
Rhythmbox Music player, makes my sound stop working :(

I was trying to play a cd I have saved, it starts the mp3 then it goes from 3 mins to 50 secs.  Then no sound works at all until I restart the computer, what would be a good media player for mp3s?

I liked that program because it looked like Itunes...

None of my Mp3 files have any (DRM) in them at all, so I don't see why unless the software is broken?

---

### Post by oracle2b on 2010-10-28
Banshee is a good media player. You can use winff or Tsmuxer to convert your video files to m2ts.

---

### Post by Wayne1987 on 2010-10-28
I need a program like Mkv2vob

Because of the DTS sound doesn't work on the ps3 I would need AC3

My OS is starting to feel unstable when I try and play music, why is this?

:EDIT:
(BUG)
Okay, this OS has a bug and its a sound bug because its doing it to me no matter how I play the music, once the music starts the sound just drops and stops working.

Could anybody, tell me how to fix this, my gut starting to turn on this one.

:EDIT:
Oh yeah, by the way I'm using 
**Ubuntu 10.10**

I hope somebody has the answer here...

---

### Post by ivarn on 2010-10-29
Ok here's the fix
[http://fossplanet.com/f10/sound-problem-ubuntu-10-10-a-65366/](http://fossplanet.com/f10/sound-problem-ubuntu-10-10-a-65366/)

---

### Post by Vigh on 2010-10-29
ubuntu = epic win- cause its about having a good reliable system, hard to set-up initially, once its set up, it is superior for producitivity/work and is "**not**" purely driven by profit

---

### Post by Brandel Valico on 2010-10-29
Here is a nice thread for setting up Multimedia and getting the Restricted extras installed.

[http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback]("http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback")

As for converting .avi to Dvd format I usually suggest 2ManDvd, A bit of a hassle to install at times. But it's a nice simple program with a menu creator. Similar to Nero and Roxio

---

