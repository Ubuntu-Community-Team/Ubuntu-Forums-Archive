---
title: "Pulse Audio Problem"
date: 2009-08-23
forum: General Help
---

### Post by Pingpawn on 2009-08-23
Hello ubuntu users,
I am having a problem booting, it is a "Pulse Audio" problem.
After trying to add a NVIDIA card to my Ubuntu system, I went to reboot
and I got the error "PulseAudio configured for person-user sessions" Under that it said:
Saned disabled; edit /etc/default/saned
 
There are about 6 messages that pop up above and below this one, but this doesn't
have an [OKAY] next to it and I can't boot up ubuntu because of it.
 
Help would be greatly appreciated!

---

### Post by Kerubu on 2009-08-23
I recently had the audio on my machine (8.10 installed) messed up by a crashing MeTV installation. The only way I could restore sound was to remove and purge all PulseAudio and ALSA packages and then download and install them.

Be warned, should you decide to do this, removing the pulse audio packages will remove things like gnome-desktop and they will NOT be re-instaleld when you reinstall PulseAudio and ALSA so you'll need to make a note of the additionaly removed packages and manually re-install them,

You can see what pulse and alsa packages you have installed with :

```

aptitude search '~i' | grep pulse

```

and

```

aptitude search '~i' | grep alsa

```

If you decide to do this method just go slowly and make note of what is removed.

---

### Post by CatKiller on 2009-08-23
I suspect you're barking up the wrong tree. You may think that you have a PulseAudio problem, but that's probably just a normal status message that you aren't used to seeing. The same for the SANE message.

Your actual problem appears to be that you aren't getting your graphical login because X isn't starting since you installed your NVidia card. Some more details on that would probably be useful.

---

### Post by markbuntu on 2009-08-23
"PulseAudio configured for person-user sessions"  is a normal boot information message.

What you need to do is reboot and choose the recovery kernel from the grub menu and then choose the fix x option.

---

