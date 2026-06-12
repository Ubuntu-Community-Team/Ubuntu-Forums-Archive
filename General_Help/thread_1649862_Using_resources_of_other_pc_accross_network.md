---
title: "Using resources of other pc accross network"
date: 2010-12-20
forum: General Help
---

### Post by afonteijn on 2010-12-20
I got a fairly powerful media system standing in the living room. Most of the time it is idle, maybe playing some music. At the same time I got a pc in my office that is less resourceful. Sometimes I'll run programs through ssh with the -XC command. This way a program will seemingly run on my office pc, while it is actually running on the media system. However:
- 1 Sound doesn't transfer to the office pc. 
- 2 When using a program I need to constantly be aware where I save my files. Sometimes it is located on the remote computer, sometimes it isn't.

Is there an alternative way to use the resources on the media system? E.g. run a program that is stored on the office pc and process it on the media system?

Both systems run Ubuntu (office 10.04 - media system 10.10). 

I'm interested to hear any creative solutions you might have!

---

### Post by afonteijn on 2011-01-02
I solved part of the problem by following the steps describe at [http://ubuntuforums.org/showthread.php?t=1623908]("http://ubuntuforums.org/showthread.php?t=1623908") Thanks to KeyserSoze93!

Sound can be streamed by using pulseaudio.
Install padevchooser on the client
Statup "PulseAudio Device Chooser" in the "Sound & Video" folder of the start menu.
An icon will appear in the system tray. Left click on it and choose "Configure Local Sound Server", then go to the Network Server tab and tick "Enable Network Access To Local Sound Devices" and "Do Not Require Authentication".

All that is left to do is to go to the "server" which you are logging into through ssh and type the following command in the terminal.

```
export PULSE_SERVER=192.168.X.X
```
Where the ip address is that of your client.

And it worked like a charm.

I'm still trying to find a way to let the applications from the server use the user data from the client. One way would be to set up a NFS network and to mount it in fstab as the /home/user directory on the server. However, this would mean that the client would have to be on all the time, otherwise the connection might be broken.

---

