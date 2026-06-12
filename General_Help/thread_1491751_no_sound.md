---
title: "no sound"
date: 2010-05-24
forum: General Help
---

### Post by waspinator on 2010-05-24
Hi,

I'm using 10.04. I had sound this morning, and after a reboot ... no sound. When I click on the speaker in the panel and choose "Sound Preferences..." and then choose "Hardware" it's blank. In the "output" tab all I have is "Dummy Output" (it's stereo at least). I don't remember updating Ubuntu since the morning, but I might have. If I type in "pulseaudio" into terminal I get this:

```
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

When I try to start pulseaudio I get this

```
~$ /etc/init.d/pulseaudio start
 * PulseAudio configured for per-user sessions
```

lspci shows this for my audio device

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

How do I get sound back? Do I have to reinstall Ubuntu, or should I wait for 10.10?

Thanks,

Waspinator

EDIT: Also, it's late so I was going to turn off my computer and go to sleep for the night, but using the power menu and clicking "Shut Down..." only logs me off. Looks like I'll have to try ```
sudo shutdown -h now
``` and get this computer to turn off. If you don't hear from me, it's because it worked.

---

### Post by waspinator on 2010-05-24
Huh, nevermind. Booted up this morning and sound is working again. I tried rebooting a few times last night and it didn't help. Strange but true.

---

### Post by Ozor Mox on 2010-06-01
Interestingly I've been having an *identical* problem. Sound was working ok, then it stopped. I noticed the hardware tab was empty and it said "dummy output" in the output tab. Then I noticed I couldn't shut down or restart, it would just log me out instead and if I was logged out already it would do nothing. I also resorted to a sudo shutdown -h now.

It's all working again now for some reason, just thought you might like to know you aren't the only one!

---

### Post by captainpotato on 2010-08-18
Ozor Mox and Waspinator, did you ever actually solve this problem? I'm also having this issue, and [there are others as well](http://ubuntuforums.org/showthread.php?t=1526440).

---

