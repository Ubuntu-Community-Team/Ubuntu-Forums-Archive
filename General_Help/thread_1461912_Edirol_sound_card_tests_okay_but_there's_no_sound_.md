---
title: "Edirol sound card tests okay but there's no sound when i use applications"
date: 2010-04-24
forum: General Help
---

### Post by TorbenPiechnik on 2010-04-24
Hello,

I am (a) completely new to Linux and (b) a bit thick, so please be patient and reply as clearly as possible.

I've been searching and pulling my hair out all night for help on this topic but I can't find anything specifically relevant to my problem, which is:

A friend has intalled Linux after a load of problems with windows. He very kindly installed my Edirol UA25 soundcard, and when i click 'test' on System-preferences-sound, it indeed plays a sound.

The problem is that when I try to play anything from the internet on firefox, or any sounds in VLC, or any other application, it doesn't work. 

I believe I'm running Ubuntu Studio, version 8.04, but I am not sure. I have an Athlon 64 bit processor if that's relevant.

Can anyone out there please help? I would be very very grateful.

:confused:

---

### Post by TorbenPiechnik on 2010-04-24
> **TorbenPiechnik said:**
> Hello,

I am (a) completely new to Linux and (b) a bit thick, so please be patient and reply as clearly as possible.

I've been searching and pulling my hair out all night for help on this topic but I can't find anything specifically relevant to my problem, which is:

A friend has intalled Linux after a load of problems with windows. He very kindly installed my Edirol UA25 soundcard, and when i click 'test' on System-preferences-sound, it indeed plays a sound.

The problem is that when I try to play anything from the internet on firefox, or any sounds in VLC, or any other application, it doesn't work. 

I believe I'm running Ubuntu Studio, version 8.04, but I am not sure. I have an Athlon 64 bit processor if that's relevant.

Can anyone out there please help? I would be very very grateful.

:confused:

Any ideas???? I've been trying all night and will do so tomorrow too. Thanks

---

### Post by TorbenPiechnik on 2010-04-25
Still no luck :(

---

### Post by themusicalduck on 2010-04-25
To be honest, I would try a newer version than 8.04. Hardware support, particularly for sound is going to be much better in the newer versions.

I would try the 10.04 release candidate. If you could burn a 10.04 iso to a CD and boot your PC from it, then click to try without changing anything (rather than install it) and then you can run it off the CD and see if your card works straight off. (You'll need to click on the volume icon and go to sound preferences to set it as default)

Then you could either install it fresh or try to upgrade using these instructions here - [http://www.ubuntu.com/getubuntu/releasenotes/1004overview](http://www.ubuntu.com/getubuntu/releasenotes/1004overview) you can download an iso from there too.

Make sure you upgrade to 10.04 and not to 8.10. It should tell you how to there.

I don't know if there is an Ubuntu studio 10.04 release available, but you could get 9.10, the release before 10.04. You can't test this before installing though. It generally has the same software anyway, but with some extras added.

Having said all that. What do you want to use Ubuntu for? Recording? In that case you could look into trying out Jack. It'll probably be installed already on your Ubuntustudio install so you could try it out.

I know this is probably a large chunk of daunting information for someone new to Ubuntu. Maybe you could ask your friend to help with it and get things working?

---

### Post by lidex on 2010-04-25
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

