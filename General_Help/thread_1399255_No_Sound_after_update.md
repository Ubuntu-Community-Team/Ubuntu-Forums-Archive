---
title: "No Sound after update"
date: 2010-02-05
forum: General Help
---

### Post by AlexJudoka51 on 2010-02-05
Hello, today, after an update had to reboot (as far I know this only happens when kernel is updated isn't it?) when logged in again, there was no sound, nothing is muted, everything is just as I left it before the update (actually I was listening music in that moment) any way to bring back my sound? (I want my music back :( )

- on karmic -

---

### Post by tom4everitt on 2010-02-05
Well, as you're mentioning it was probably a kernel upgrade that caused the error. When your computer is booting you can hold shift (or press esc if its an older ubuntu) and you will get a menu where you can choose to boot from older kernels (the grub2 menu). Try that and see what happens.

---

### Post by AlexJudoka51 on 2010-02-05
hi, thanks for the answer, I have booted in the second kernel option and no sucess :( no sound... :(



EDIT: after some reboots, the sound came back, dunno why... but I'm on the most recent kernel and it worked.... weird but I can listen to music again :)

---

### Post by tom4everitt on 2010-02-06
Mysterious are the ways of great ubuntu #-o

---

### Post by krippa on 2010-02-09
This same thing happened to me and so far the sound has not returned. I have also tried booting with the old kernel - a no-go.

At one point I got a very very low noise sound out of the speakers so I am unsure if it isn´t working or if the volume is just extremely low (I already checked all the volume controls, switching between ALSA and pulseaudio etc.)

Also sound settings now say I don´t have a microphone anymore!

Any ideas on a next step? 

BTW. I have a Dell Studio XPS 16

---

### Post by dino99 on 2010-02-09
1st step to validate: system --> pref --> sound
        there, check settings

2d step: apps --> sound & video --> pulseaudio volume control

Now if you still have not sound as you like, follow the hard way:

-  remove / purge alsa*, pulse* packages
-  erase hidden files: .pulse & maybe .gstreamer
-  reinstall all the "alsa" & "pulse" packages previously erased

- check again 1st & 2d steps

If you are still in trouble, in console: ubuntu-bug audio

note: there is also the solution to not use pulseaudio at all, only alsa (remove/purge pulseaudio)

Sometimes, cleaning the system can help too ( install the latest "bleachbit" you find on the website)

---

### Post by krippa on 2010-02-09
Thanks for your post. After an even closer look in the sound settings I saw that my an HDMI output device was chosen instead of the analog one. Don't remember what the setting was before since I have never had to mess with it but setting it to analog makes sound work again and thankfully in Karmic, it works really well!

Similarily with input, I had to pick my input device again (even though in this case there was only one which was curiously not selected).

Although ""easy"" to fix, I don't think this is ok behavior for an update, what happened to "just works"!

---

