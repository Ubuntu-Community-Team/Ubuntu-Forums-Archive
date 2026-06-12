---
title: "Sound Surround 5.1 Problem"
date: 2010-11-23
forum: General Help
---

### Post by Einstein86 on 2010-11-23
[I][COLOR=DarkSlateGray]I please very much admin just to move this topic in a right group if it's inappropriate here. Appreciate [/COLOR]

[/I][SIZE=2]People, I am user of Ubuntu 10.04 and I have problem with my 5.1 surround output sound. When I run any song I can hear it on all speakers but it's just something like you reduce up and down volume button. It comes feel same as you use some mixer. Know what I mean? But when I load some radio programme in mp3 format downloaded on hdd, where is only talk without songs, sound is heard perfectly.  
Do you have any idea what that can be? [/SIZE]

---

### Post by papibe on 2010-11-23
Could you post the result of these commands:
```
$ sudo aplay -l
$ sudo aplay -L
```
Regards.

---

### Post by Einstein86 on 2010-11-24
here it is

---

### Post by papibe on 2010-11-24
It is possible that some of the speakers are muted. Try:
```
$ alsamixer
```
to check both the mute status and the volume of each output. That is a text mode(curses) application. User the keyboard's arrows to move arround. 

After that you could try:
```
$ speaker-test -Dsurround51 -c6 -twav
```
or
```
$ speaker-test -Dplug:surround51 -c6 -twav
```
to test each speaker individually.

Good luck!

---

### Post by Einstein86 on 2010-11-26
please can you look on my alsamixer, i couldn't find anything unusual?

and when i try test, all speakers are heard very good :(

this might be crazy question, but can problem be connected with my 64 cpu that works on 1.6GHz also RAM on 512MB?

---

### Post by papibe on 2010-11-27
Your alsamixer looks OK. Check your Sound Settings, and make sure that you have selected all channels (5.1) as output instead of the the default (stereo).

Then it would depend on the audio file and the player you use. Try mplayer as a player because is well known, and it can handle 5.1. If you run it from the command line you can see detail information about the media and the devices are being used to play the file.

Regards.

---

### Post by Einstein86 on 2010-11-30
it's much better, but I still can sense little problem in sound. However I am really thankfull for your help and time you set aside for me.

all best

---

