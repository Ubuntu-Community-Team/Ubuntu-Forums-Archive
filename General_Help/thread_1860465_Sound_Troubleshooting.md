---
title: "Sound Troubleshooting"
date: 2011-10-14
forum: General Help
---

### Post by fleamour on 2011-10-14
I ran the 10.04 LTS script at this site:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Thing is I am running Xubuntu.  It installed loads of Gnome apps.  System Monitor now reports that I'm running Gnome, even though I'm running XFCE.  Kinda like the new layout, but seriously.  Can the script be adjusted for the Xubuntu desktop?  Any expert know how?

I can restore from backup image, but sound does not work after suspend, which is a regression.  I ran script to solve, which it has.  But the results are a messy hybrid of Gnome & XFCE.

Please advise.

---

### Post by ankspo71 on 2011-10-15
Hi,
The answer would depend on what actually fixed the problem, because the script did 2 things: 

A. The script installed "ubuntu-desktop" and then reinstalled it again. 
It seems to me that the author of the script probably did this to make sure all of the default audio related packages were not previously removed by the user, but that presents a problem for the Xubuntu, Kubuntu, and Lubuntu users. 

B. The script also installed new or updated audio related packages, including packages from 2 different PPA repositories.

Using a slightly modified version of the script for use with Xubuntu might work as just as good, but this would depend on which of the above actually fixed the audio problem for you, so there is no guarantee this will work.

But first, you will need to remove Ubuntu and all of Ubuntu's default applications. You can do one of two things:

A. Use your full backup and restore your system to the way it was,
OR
B. Try using the script on the following page to remove Ubuntu and reinstall Xubuntu with a single command: [http://www.psychocats.net/ubuntu/purexfcelucid](http://www.psychocats.net/ubuntu/purexfcelucid)

Using your backup will probably be safer, because the script in the above link can sometimes fail and/or cause you to reinstall some applications.

Once you are restored to a pure Xubuntu desktop, you can then use the script at [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) again, but replace the words "ubuntu-desktop" with "xubuntu-desktop" (at each occurance) inside the script.

Here's sample modified version of the script:
> If you are using Ubuntu 10.04 (Lucid), then execute this command and reboot:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo add-apt-repository ppa:team-iquik/alsa; sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm xubuntu-desktop linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r) libasound2; sudo apt-get --reinstall install linux-sound-base alsa-base alsa-utils gdm xubuntu-desktop linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r)  libasound2; killall pulseaudio; rm -r ~/.pulse*

Hope this helps

---

### Post by fleamour on 2011-10-15
Thanks for your concise response.  I was gonna just add the ALSA dev channels if encountered sound problems again, but you outline how to execute the whole script.

Funny thing:  Everything seems faster & more responsive?!?  But may be disabling CPU SpeedStep in BIOS. 

Will chalk it down to experience.

Cheerz!

---

### Post by fleamour on 2011-10-15
Ran the psychocats script.  Is it normal for System Monitor to report itself as Ubuntu with Gnome, when it is in fact Xubuntu.  Can anyone check their system tab?

---

