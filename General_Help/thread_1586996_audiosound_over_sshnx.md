---
title: "audio/sound over ssh/nx"
date: 2010-10-02
forum: General Help
---

### Post by lespedeza on 2010-10-02
Not sure if this is the correct place to post, please move thread if there is a more appropriate location.

This has been questioned before, but nobody has provided a viable solution.  When logging in remotely via ssh or via nx (which is via ssh), no access to sound cards via regular user.  This is quite frustrating.  I have an htpc which is hooked up to home stereo.  I work at home on the laptop and would like to connect to htpc via nx or ssh and control music on the htpc.  So, I do not want to stream audio over ssh.  I want to control audio on the server.

I've tried the recommendations in the following links

[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/483130]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/483130")

and 

[https://bugs.launchpad.net/ubuntu/+bug/221363]("https://bugs.launchpad.net/ubuntu/+bug/221363")

but they don't solve the problem.

Something curious is that sound is available to root user via the nx or ssh session.  For example, via the regular user, it tells me no sound cards are present.

```
:~$ aplay -l
aplay: device_list:223: no soundcards found...

```

But if I issue same command with root, another story...
```

:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I can also play as root using aplay without any problems.

```
:~$sudo aplay /home/xxxxx/Downloads/vivaldi.wav 
Playing WAVE '/home/xxxxx/Downloads/vivaldi.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

```

versus 
```

:~$ aplay /home/xxxxxxx/Downloads/vivaldi.wav      ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.iec958
aplay: main:608: audio open error: No such file or directory

```

So, if anyone has a solution to this problem it would be greatly appreciated.  It seems there is something in /etc/X11/Xsession.d or in gnome-session that does not get executed correctly when you login in via ssh/nx.

Thanks for your help.

---

### Post by lespedeza on 2010-10-03
I solved the problem by adding user nx and my regular user to the audio group.  I thought I had already done this with my troubleshooting yesterday, but realized this morning that nx was never added to audio group even though I recall typing that command in.  Anyways problem solved.

---

### Post by hasi42 on 2010-10-15
Thank you. Your solution helped me too.

My problem was that arecord didn't work when it was started by a cronjob while I wasn't logged in.

---

