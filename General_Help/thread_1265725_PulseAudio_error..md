---
title: "PulseAudio error."
date: 2009-09-13
forum: General Help
---

### Post by mcpsm_84 on 2009-09-13
I've got an error for PulseAudio "saned disabled; edit /etc/default/saned". Now I can't get to my desktop.

The last thing I did was install nVidia driver for 8800GTX.

P.S. I'm complete Linux/Ubuntu newb. I just installed Ubuntu 9.0.4 today and this is my first experience with Linux. If anyone can help, it's gonna need to be layman's terms :oops: and very step-by-step, please.

Thanks!

---

### Post by stderr on 2009-09-13
Hi mcpsm_84. It's much more likely to be the new graphics driver causing your login problems. Could you describe what happens when you boot the PC - i.e. what stage does it get to? If it seems to boot but you don't get your graphical login screen, could you try pressing Ctrl+Alt+F2, and see if that takes you to a textual login prompt?

---

### Post by kevdog on 2009-09-13
I'd remove pulse audio if I were you.  Big problems in ubuntu karmic and less.  Supposedly things are better in jaunty however that is speculation.

---

### Post by mcpsm_84 on 2009-09-13
> **stderr said:**
> Could you describe what happens when you boot the PC - i.e. what stage does it get to?

I get a list of "Starting" devices/processes (such as Network Manager, Printing System, etc.). All of these have an "OK" next to them, except PulseAudio, which has an orange asterisk and the message "saned disabled; edit /etc/default/saned". It doesn't get further than that... Doesn't get to desktop or GUI. 

  
> **stderr said:**
> If it seems to boot but you don't get your graphical login screen, could you try pressing Ctrl+Alt+F2, and see if that takes you to a textual login prompt?

I can Ctrl+Alt+F2 to a text login and enter/type in my user name, but not my password (no text comes after PW when I type).

---

### Post by mcpsm_84 on 2009-09-13
> **kevdog said:**
> I'd remove pulse audio if I were you.  Big problems in ubuntu karmic and less.  Supposedly things are better in jaunty however that is speculation.

How can I uninstall it?

---

### Post by stderr on 2009-09-13
The password field is working, it just doesn't display characters as you type. Just type your password and hit enter. 

To remove pulseaudio:
```
sudo apt-get remove pulseaudio
```

I don't think that's the problem, though. I think it has to do with your nvidia  graphics driver. And saned is probably referring to the daemon for sane, a scanner app/library - unrelated, and just an unimportant warning anyway.

if removing pulseaudio doesn't help, you can reinstall it with 

```
sudo apt-get install pulseaudio
```

---

### Post by mcpsm_84 on 2009-09-14
I removed PulseAudio, but still have the same problem (can't get to desktop). 

I installed another Ubuntu 9.0.4 and the same issue occurs after installing any of the 'recommended" nVidia 8800GTX drivers.

Thanks for help and suggestions so far.

---

### Post by CatKiller on 2009-09-14
> **mcpsm_84 said:**
> I've got an error for PulseAudio "saned disabled; edit /etc/default/saned".

That's not a PulseAudio error message. [SANE]("http://en.wikipedia.org/wiki/Scanner_Access_Now_Easy") is completely unrelated to [PulseAudio]("http://en.wikipedia.org/wiki/PulseAudio"), and they are both completely unrelated to the fact that the nVidia driver you installed has meant that X doesn't start.

They are just messages that you aren't used to seeing.

> **kevdog said:**
> I'd remove pulse audio if I were you.

That's not going to achieve anything, since it's not related to anything. While the default PulseAudio configuration in Hardy was bad, removing it from subsequent releases is just pointless.

---

