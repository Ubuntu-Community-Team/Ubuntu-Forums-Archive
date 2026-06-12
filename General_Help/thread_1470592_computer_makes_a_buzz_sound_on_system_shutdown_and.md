---
title: "computer makes a buzz sound on system shutdown and restart"
date: 2010-05-03
forum: General Help
---

### Post by bolenjx1 on 2010-05-03
For some time now, my laptop makes a quick but loud buzz sound when I shutdown or restart it. Muting my sounds doesn't fix it. Before, it didn't do this. It just started one day and got worse till it happened everytime I shutdown or restart.

Going to preferences > sounds > changing sound theme to no sounds helped a bit and after doing this, it doesn't happen all the time anymore. This is quite disturbing especially when I'm in libraries. What worries me the most though is that it might affect my speaker.

I'm using Karmic btw. Thanks for the help.

---

### Post by QIII on 2010-05-03
Does the buzz occur at startup before or after the OS loads?

At shut down before or after the OS shuts down?

---

### Post by bolenjx1 on 2010-05-03
No, it doesn't occur at startup. I don't know if it's related but the login sound (right after you enter you password successfully) doesn't play. This used to work before. The system ready sound though just before you're shown the login box plays ok.

Immediately after I press shutdown or restart it buzzes. My wallpaper is still there but no more taskbar or icons. It's like nautilus has already unloaded before it buzzes. 

Could it be alsa or pulse shutting down that's causing that sound?

---

### Post by bolenjx1 on 2010-05-04
Anyone know how to deal with this? It's really disturbing..

---

### Post by bolenjx1 on 2010-05-11
Anyone? I'm really afraid that this might damage my speakers.

---

### Post by i.m.raziel on 2010-05-13
I have Ubuntu 10.04 which was running all right until I updated it. Now it has the same problem (*of farting*) whenever the laptop is restarted or shutdown. The problem does not occur in logging off. Also the problem persists even if the speakers are muted through alsamixer. I've tried whatever I could find on the net. This problem seems persistent as it developed after update in Ubuntu 9.10 too. Let's hope the developers overcome it.

---

### Post by bolenjx1 on 2010-05-22
Mine was actually fixed after updating to lucid. Didn't have to do anything.

---

### Post by margitajemrtva on 2010-09-27
having same problem with dell inspiron 1545.
not really a solution:** if I log out first, and then shutdown, there is no loud buzz sound**.

one more thing: when I use 'shutdown' command from the terminal (e.g. to schedule a shutdown in, say, 120 mins), there is this f* buzz again!

---

### Post by margitajemrtva on 2010-10-14
problem gone with an update do 10.10

---

### Post by joculi on 2011-04-01
I ran into this problem when I upgraded the ALSA drivers on 10.04 (trying to get my built in mic to work).  I was able to get rid of the buzz at shutdown by installing gnome-alsa-mixer and using it to set the system beep to mute.

---

