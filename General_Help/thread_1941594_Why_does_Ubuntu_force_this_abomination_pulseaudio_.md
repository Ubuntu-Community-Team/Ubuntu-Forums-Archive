---
title: "Why does Ubuntu force this abomination pulseaudio on us?"
date: 2012-03-15
forum: General Help
---

### Post by Tank Jr on 2012-03-15
Hi all,
Why do we have to put up with this HORRIBLE excuse of a program?
It freezes my computer on waking, and the ONLY way to get sound back is to reboot, which kind of defeats the purpose of hibernating in the first place, doesn't it?

---

### Post by Rodney9 on 2012-03-16
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)

---

### Post by Tank Jr on 2012-03-18
They seem to solve problems with ALSA, or am I missing something?

---

### Post by HiImTye on 2012-03-18
to get sound back, try
```
pulseaudio --start
```
but you might simply be having issues with ALSA (which PulseAudio is a layer on top of)

---

### Post by Tank Jr on 2012-03-20
I did the following:
```

  $killall pulseaudio  
  $pulseaudio --start

```
The output was:
```

  N: [pulseaudio] main.c: User-configured server at  {8af8ac5fed7552b9bb21849c00000017}unix:/home/<My login>/.pulse/8af8ac5fed7552b9bb21849c00000017-runtime/native,which appears to be local. Probing deeper.   

```
Next I try
```

    $pulseaudio -D

```
I get
```

E: [pulseaudio] main.c: Daemon startup failed.

```
No sound. I am forced to reboot.
:mad:

---

### Post by Tank Jr on 2012-03-22
-bump-

---

### Post by idoitprone on 2012-03-22
> **Tank Jr said:**
> Hi all,
Why do we have to put up with this HORRIBLE excuse of a program?
It freezes my computer on waking, and the ONLY way to get sound back is to reboot, which kind of defeats the purpose of hibernating in the first place, doesn't it?

wat up with all the pulseaudio hate?
i still dont get it. All it does it slow down the computer since it huge
the things we should hate is the alsa stack

btw, do you have hdaudio. Then I feel your pain. It breaks often with alsa updates

---

### Post by mastablasta on 2012-03-23
HD audio is a FAIL in linux. Card is supported. updates come, sound doesn't work, new updates sound works again sort of, new updates sound doesn't work normally again.

---

### Post by idoitprone on 2012-03-23
> **Tank Jr said:**
> They seem to solve problems with ALSA, or am I missing something?

yep you are missing something because all your problems is probably not related to the pulseaudio sound system. It alsa

All pulseaudio does it hide structural problems with the alsa api. Unfornately, pulseaudio need access to hardware, but it too high level to do it. So  it calls the alsa stack which is a mess. Basically alsa is used for drivers while pulseaudio does all the fancy things.

If you are having problem with alsa, it mostly likely the alsa driver stack is screwing up

People hate pulseaudio for other reason like latency. Because a sound server is kidda redundant on single user computer. Its extra functionality only add latency.

[QUOTE=mastablasta]          HD audio is a FAIL in linux. Card is supported. updates come, sound  doesn't work, new updates sound works again sort of, new updates sound  doesn't work normally again.     [/QUOTE]
well creator of oss, Hannu actually hated the hdaudio specification. It kidda hard to for developers to write drivers because there is to options and hardware canfiguations that make it a nightmare.

---

### Post by Tank Jr on 2012-03-24
I believe I have HD audio.
```

$lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

```

---

### Post by idoitprone on 2012-03-24
> **Tank Jr said:**
> I believe I have HD audio.
```

$lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

```

i hope this helps [http://ubuntuforums.org/showthread.php?t=1036508](http://ubuntuforums.org/showthread.php?t=1036508)

you might need to provide your laptop model because hd audio is a nightmare since it may differ between vendors and models of the same line

---

### Post by Tank Jr on 2012-03-28
> **idoitprone said:**
> i hope this helps [http://ubuntuforums.org/showthread.php?t=1036508](http://ubuntuforums.org/showthread.php?t=1036508)

you might need to provide your laptop model because hd audio is a nightmare since it may differ between vendors and models of the same line

Nope, did not help.
 My machine is a Dell Inspiron 530 desktop.

---

### Post by MG&amp;TL on 2012-03-28
I helped to wiki-fy [https://help.ubuntu.com/community/SoundTroubleshootingGuide](https://help.ubuntu.com/community/SoundTroubleshootingGuide) recently, I suspect it's the same guide as posted previously, just not owned by google.

---

### Post by idoitprone on 2012-03-28
> **Tank Jr said:**
> Nope, did not help.
 My machine is a Dell Inspiron 530 desktop.

on your alsa.conf in /etc/modprobe.d directory

add 
```
options snd-hda-intel model=6stack-dell
```You need to configure alsa. Here is the documation in this link search Inspiron 530

[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

or run this command

```
sudo bash -c 'echo "options snd-hda-intel model=6stack-dell" >>  /etc/modprobe.d/alsa.conf'
```

hope it works, if not i guess i have to find the alsa parameters again.

post the result of ```
aplay -l
```
as you can see in the docs you kidda need the exact card

Yep, this is because alsa sucks not pulse

---

### Post by Tank Jr on 2012-04-07
Nope, no good still.
I have had this computer for more than 3 years, and did not have this issue with Hardy, Karmic, Lucid, Maverick, and Natty.

---

### Post by idoitprone on 2012-04-07
> **Tank Jr said:**
> Nope, no good still.
I have had this computer for more than 3 years, and did not have this issue with Hardy, Karmic, Lucid, Maverick, and Natty.

then you should remove all the changes i asked you to do before, because this is obviously a regression.

i wonder if this post helps
> Try the simple version first. You can just specify "all" and all the modules will be unloaded. To edit:
    ```
 Code:
     gksu gedit /etc/default/alsa 
```
Add **all** between the quotes in this line:
     Code:
    ```
 force_unload_modules_before_suspend="" 
```
So now it looks like this:
   ```
  Code:
     force_unload_modules_before_suspend="all" 
```
Save the file and close. Now suspend/resume and see if it worked.

BTW alsa-utils is in the default ubuntu install.
[http://ubuntuforums.org/showthread.php?t=1348916&page=3](http://ubuntuforums.org/showthread.php?t=1348916&page=3)

this post might not cover what you need
[http://crunchbanglinux.org/forums/topic/6514/solved-no-sound-after-resumesuspend-ubuntu-karmic-koala-910/](http://crunchbanglinux.org/forums/topic/6514/solved-no-sound-after-resumesuspend-ubuntu-karmic-koala-910/)



it a little frusting and i know it. People had to deal with it. I had an alsa regression on this laptop, which broke my sound.

unless the sound is muted and you can unmute the sound, then it is a entirely different problem[IMG]chrome://dictionarytip/skin/dtipIconHover.png[/IMG]

---

