---
title: "My sound just unexpectedly stopped working"
date: 2006-04-23
forum: General Help
---

### Post by NakedGreekStatue on 2006-04-23
It is really weird because it suddenly happened for no reason that I can tell. The little ubuntu drum-beat that plays when you get to the login screen works fine though. Any help?

---

### Post by jmullagh on 2006-04-23
I had the very same problem. I updated to Dapper and kernels 19 and 20 I had lost my sound. I got it back with a soft re-boot.However, when I would do a hard re-boot...there was no sound. I just updated the system to kernel 21 and now it is working fine...bongos and all. Try updating to the new kernel.....

---

### Post by NakedGreekStatue on 2006-04-24
hmm im using breezy though?

---

### Post by NakedGreekStatue on 2006-04-24
this is my kernel: 2.6.12-10-386

ALso when I go to System>Preferences>Sound there is no soundcard on the list under "Default SOund Card":. How do I get my soundcard back under there? Do I need Ubuntu to redetect and configure it somehow?

---

### Post by NakedGreekStatue on 2006-04-25
*bump* any help?

---

### Post by tc10b on 2006-04-27
Have you tried using the Gnome sound fix in Automatix? I had a similar problem and that seemed to do the trick.

Find it in this thread. [http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix)

---

### Post by chownsb on 2006-05-03
I have the exact same problem.  A day or two ago my sound just quit working.  I think it was shortly after a large batch of updates.  I'm using Dapper right up to date as of today (May 3rd, 11:00 ET).

All checks that I know about (lspci, sound preferences, etc) all show my sound card still.  I've checked an nothing seems to be muted.  I played a sound on the terminal and it thinks it played just fine (but I heard nothing).  My sound card is a SoundBlaster Live Value and has worked fine until now.

Any suggestions?

---

### Post by crichell on 2006-05-04
This may help you guys out.  (For the Breezy folks)

From the terminal try

gst-register-0.8

Reboot and you should have sound back.  Hope it helps.

---

### Post by shendric on 2006-05-04
Hi all,

I just started using Ubuntu (Breezy) and my soundcard also just stopped working.  I've tried all the suggestions here, as well as a couple of others in other places, and none of them worked.

lspci finds the soundcard, and I can run through alsa's configuration and it detects it, no problem, but when I try to run alsamixer, or do something with the volume, I get errors like the following:

alsamixer: function snd_ctrl_open failed for default: No such device

Any help would be appreciated.  The only thing I did prior to this was an update of the system.

Sean

---

### Post by frogstar on 2006-05-10
[QUOTE=shendric]lspci finds the soundcard, and I can run through alsa's configuration and it detects it, no problem, but when I try to run alsamixer, or do something with the volume, I get errors like the following:

alsamixer: function snd_ctrl_open failed for default: No such device

Any help would be appreciated.  The only thing I did prior to this was an update of the system.[/QUOTE]

Ditto.  Anyone out there have any ideas?

---

