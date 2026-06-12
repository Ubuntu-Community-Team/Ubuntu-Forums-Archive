---
title: "vlc sound and video out of sync"
date: 2011-07-06
forum: General Help
---

### Post by knoproxy on 2011-07-06
my vlc player suddenly decided to start de-syncing my sound and video. Switching vlc to asla output corrects this, but also makes the player go mute whenever you pause and resume a video. Totem is still working fine, but I really like vlc. If anyone knows how to fix this issue I would appreciate it.

---

### Post by litmus on 2011-07-06
same problem here. no solution found yet. anyone?

---

### Post by flipper T on 2011-07-06
go to tools / synchronization

fiddle with controls as you are playing video

i have found that restarting vlc often fixes the problem

---

### Post by fede82 on 2011-07-06
> **flipper T said:**
> go to tools / synchronization

fiddle with controls as you are playing video

i have found that restarting vlc often fixes the problem

You could do the same thing with hotkeys J and K (or K and L?), a little bit easier.
Anyway it`s just a workaround, not a real solution :(

---

### Post by Olivrwendl on 2011-07-06
same problem here. consistently -300 off.

---

### Post by de_vries on 2011-07-07
same problem here...

I found this on The VideoLAN Forums: "PulseAudio output is broken beyond repair in VLC 1.1.x. I wouldn't expect any fix until VLC 1.2."

I chanced the VLC seting under Audio --> output to "Alsa audio output" and I've got my sync back.

---

### Post by litmus on 2011-07-07
Selecting alsa gives me the same problems mentioned above (audio goes when video is paused and then resumed). The best workaround i could find is to downgrade to version 1.9.1-1ubuntu1.1 from the natty-security repo. That works fine for me. Hope they fix it soon, vlc is by far the best player around.

---

### Post by Digital_Man on 2011-07-07
> **de_vries said:**
> I chanced the VLC seting under Audio --> output to "Alsa audio output" and I've got my sync back.

That worked for me - many thanks!

---

### Post by dmp1ce on 2011-07-31
> **litmus said:**
> Selecting alsa gives me the same problems mentioned above (audio goes when video is paused and then resumed). The best workaround i could find is to downgrade to version 1.9.1-1ubuntu1.1 from the natty-security repo. That works fine for me. Hope they fix it soon, vlc is by far the best player around.
Yep, this is the same problem I have with changing to alsa.  The audio seems to be in sync but when I pause the video and resume then the audio is gone.  Looking forward to a fix.  VLC is my favorite player.

---

### Post by fbanguiano on 2011-08-01
Check this out, it worked for me:
VLC and audio lag issues are perhaps more common than they really should be. Under Linux, pulse-audio seems to be a common thread.

However there doesnt appear to be a magic "fix" to cure all.

So here are a few things you could try:

Check that you haven't changed the Audio synchronisation: Tools - Track Synchronisation should be set to zero
Check that other preferences havent affected audio tracking: Tools > Preferences and click the Reset Preferences button
Use Alsa instead of Pulse-Audio for output: From the VLC menu, choose Tools > Preferences > Audio. Change the Output from Default to Alsa
If using Natty - revert to using interrupt driven mode instead of time-scheduled mode

modify the following line in /etc/pulse/default.pa

load-module module-udev-detect

with :

load-module module-udev-detect tsched=0

source: [http://askubuntu.com/questions/53652/sound-in-vlc-is-out-of-sync](http://askubuntu.com/questions/53652/sound-in-vlc-is-out-of-sync)

---

### Post by scottbomb on 2011-10-08
That did it! Thanks!!

---

### Post by scottbomb on 2011-10-08
Well, nevermind. It fixed it for a few minutes and now the audio is completely gone. Even after a reboot.

---

### Post by scottbomb on 2011-10-11
> **litmus said:**
> The best workaround i could find is to downgrade to version 1.9.1-1ubuntu1.1 from the natty-security repo. That works fine for me. 

Please forgive the noob question here but how exactly do I go about getting that version? Do I need to add a software source that doesn't already come with Natty? If so, what exactly is the source so I can put it in there? You say "natty-security repo" but (like I said, I'm a noob) I can't seem to find the exact URL to put into Software Center to get access to it.

---

### Post by scottbomb on 2011-10-14
FWIW, I uninstalled and re-installed and it works fine now. Strange.

Edit: Until a few days later. Sound stops about 28 min. into an hour-long video (.avi). 

Sure wish I knew how to find that version 1.9.1-1ubuntu1.1 ......

---

