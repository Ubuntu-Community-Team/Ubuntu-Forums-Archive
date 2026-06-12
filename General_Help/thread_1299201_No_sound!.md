---
title: "No sound!"
date: 2009-10-23
forum: General Help
---

### Post by Cephi on 2009-10-23
I installed hardy to make the machine in our grad lab a dual boot.  No sound at all.  I upgraded to jaunty, no change.  Windows sound still works.  

When I use mplayer, I get a mess of errors in the text output.  I've included that in the attached txt.

Those messages include that I lack needed permissions, so I've tried "sudo mplayer track.mp3" and then the only error message I get is:

```

E: core-util.c: Home directory /home/cephi not ours.
AO: [pulse] Failed to connect to server: Connection refused
E: core-util.c: Home directory /home/cephi not ours.

```

(I don't know whether this is related, but xfce won't let me access Users and Groups.  It tells me "You are not allowed to access the system configuration."  It tells me the same thing whichever user acct I log in under (there are only two).  I haven't tried it as root because I don't know how to log in as root, I only know how to su on the command line.)

---

### Post by jbrown96 on 2009-10-23
You may want to switch to ALSA playback. System-->preferences-->sound. Switch all the options to ALSA. Reboot. Try playing your audio file, and while that is playing make sure none of the channels are muted Open a terminal (apps-->accessories) ```
alsamixer
``` only unmute the necessary ones, which are usually pcm, master, front, headphone, speaker.

Have you installed a mp3 decoder? You can also test basic sound playback in the sound preferences; there is a test button. If that works, but mplayer still won't. Install ```
sudo apt-get install ubuntu-restricted-extras
``` Try mplayer's settings and make sure that alsa is the playback option and not pulseaudio. If that's still not working, post the output of ```
lspci | grep Audio
```

---

### Post by Cephi on 2009-10-24
I'm using xubuntu, and I can find nothing corresponding to the sound preferences you tried to direct me to.  When I try "alsamixer" on the command line, I get this error:

> 
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused


The problem is not just mplayer, or just mp3s; I've tried several applications and formats.

When I use 'lspci | grep Audio', I get:

> 
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)


Any help greatly appreciated!  I was hoping I could introduce tons of people to linux by putting xubuntu on the lab computer... but I think people are getting a bad first impression!

---

### Post by Cephi on 2009-10-24
Well, I seem to have fixed it... I tried to run users-admin from the command line, which led me to discover that my /var/lib/dbus/machine-id file was empty... so, based on what was said here: [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/288596](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/288596), I deleted the machine-id file and then used "dbus-uuidgen --ensure" to generate a new one, then I rebooted... and suddenly there was sound (after I fiddled with alsa a bit)

---

