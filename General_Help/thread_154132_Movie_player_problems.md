---
title: "Movie player problems"
date: 2006-04-02
forum: General Help
---

### Post by Hoffmann on 2006-04-02
Movie Player
Hello:

I am having problems with both VLC and MPlayer players.

I went to to System tab ---> Preferences ---> Removable Drives and Media, and in the Video DVD Disc write this in the commandline box, I tried the obptions below:

(1) VLC
Code: 
wxvlc dvd:///dev/dvd


(2)Mplayer
Code:
gmplayer dvd://1 -dvd-device /dev/dvd

With the first option, VCL was lounched, but nothing happen. Whereas, in the second option, MPlayer was also lounched, but I got the error:
"Failed to open dvd://1"

Could you guys, please, help me?

Thanks!
Hoffmann

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=Hoffmann]Movie Player
Hello:

I am having problems with both VLC and MPlayer players.

I went to to System tab ---> Preferences ---> Removable Drives and Media, and in the Video DVD Disc write this in the commandline box, I tried the obptions below:

(1) VLC
Code: 
wxvlc dvd:///dev/dvd


(2)Mplayer
Code:
gmplayer dvd://1 -dvd-device /dev/dvd

With the first option, VCL was lounched, but nothing happen. Whereas, in the second option, MPlayer was also lounched, but I got the error:
"Failed to open dvd://1"

Could you guys, please, help me?

Thanks!
Hoffmann[/QUOTE]
Do you have the dvd, audio, and video codecs installed ? :)

---

### Post by lemix on 2006-04-02
I dont know if this helps. :-k 

But to play DVD's in VLC Player off of a fresh install i always open VLC (GUI) and instead of running *Open Disc* From the File Menu i go to *Open Directory...* And open the Video_ts directory from the disc. The audio loads with it.

I also have downloaded and installed every VLC Plugin from Synaptic Package Manager.

---

### Post by Hoffmann on 2006-04-02
[QUOTE=MasterChief1234]Do you have the dvd, audio, and video codecs installed ? :)[/QUOTE]

Well, I can listen to streamradios, and CDs with no problem. How can I check if I have the appropriated programs/libraries installed?
Hoffmann

---

### Post by Hoffmann on 2006-04-02
[QUOTE=lemix]I dont know if this helps. :-k 

But to play DVD's in VLC Player off of a fresh install i always open VLC (GUI) and instead of running *Open Disc* From the File Menu i go to *Open Directory...* And open the Video_ts directory from the disc. The audio loads with it.

I also have downloaded and installed every VLC Plugin from Synaptic Package Manager.[/QUOTE]

I did exactly as you suggested, but. Both the sound and the image is not working well. The sound is missing all the time (every 2 seconds) , and I got no mage quality. Could you tell me about your VLC Player configuration?
Thanks,
Hoffmann

---

### Post by lemix on 2006-04-04
[QUOTE=Hoffmann]I did exactly as you suggested, but. Both the sound and the image is not working well. The sound is missing all the time (every 2 seconds) , and I got no mage quality. Could you tell me about your VLC Player configuration?
Thanks,
Hoffmann[/QUOTE]

Sorry bout long time no reply. My ubuntu took a dump on me when i tried to update. Then i tried to install dapper 6.04 and that took a dump on me. Now i am back in 5.10 and i have the same problem as you do. its taking a dump on me.

---

### Post by Hoffmann on 2006-04-05
[QUOTE=lemix]Sorry bout long time no reply. My ubuntu took a dump on me when i tried to update. Then i tried to install dapper 6.04 and that took a dump on me. Now i am back in 5.10 and i have the same problem as you do. its taking a dump on me.[/QUOTE]

Hi lemix,

No problem!
 What happened during your upgrade to Dapper 6.04? I am also worry about the quality of upgrading the system next June. I don't know if the distro will be good enough during the upgrading process. I mean, I hope, the upgrading don't break the system. But, it seems like that was exactly what heppened with you.
Well, regarding the players, I decided to use my Windows partition to watch DVDs, since it is not working well with my Ubuntu partition.

Hoffmann

---

### Post by JoeMetal on 2006-04-05
As far as I know, you have to have libdvdcss installed to play DVDs since they are encrypted.  I don't think that the Ubuntu repositories have it.  You can search for a script called EasyUbuntu.  It'll install a whole bunch of stuff for you like plugins for web browsers and other things along with libdvdcss.  You can check what you want to install too, so it's not just putting a whole bunch of useless stuff on your comp.

---

### Post by Hoffmann on 2006-04-05
[QUOTE=JoeMetal]As far as I know, you have to have libdvdcss installed to play DVDs since they are encrypted.  I don't think that the Ubuntu repositories have it.  You can search for a script called EasyUbuntu.  It'll install a whole bunch of stuff for you like plugins for web browsers and other things along with libdvdcss.  You can check what you want to install too, so it's not just putting a whole bunch of useless stuff on your comp.[/QUOTE]

I didn't find neither libdvdcss nor EasyUbuntu on Synaptic

---

### Post by r4ik on 2006-04-05
For EasyUbuntu try here,

[http://www.ubuntuforums.org/showthread.php?t=64629](http://www.ubuntuforums.org/showthread.php?t=64629)

Maybe this is a good read,

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

It includes libdvdcss2 somewhere in this section,

[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Codecs](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Codecs)

Good luck !

---

### Post by Hoffmann on 2006-04-05
I will check it out.

Thanks a lot!

---

