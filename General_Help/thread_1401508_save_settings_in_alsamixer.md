---
title: "save settings in alsamixer"
date: 2010-02-08
forum: General Help
---

### Post by gabrielcik on 2010-02-08
Hello,

I was finally able to make the internal mic of my Vaio w12 work properly both sound recorder and in skype...

I added this line in alsa-base.conf
```
 options snd-hda-intel model=auto 
```The problem is that everytime i restart the netbook the "Input so" switch automatically to "Front mic" instead to keep the setting "Int mic".

I tried to use sudo alsa ctl store but nothing change...

Maybe there is another way for to set "input so" to "Int mic" by default.

Im using Ubuntu 9.10 desktop 32 bit.

Thank you:)

---

### Post by crichard on 2010-02-08
no space between alsa & ctl.
Your command should be like this 
> [SIZE=2]sudo alsactl store 0[/SIZE]

FYI, the last part of above mentioned code is Number zero. If you are  having 2 sound cards you need to change it as 1 i.e. Number of sound  cards-1

---

### Post by gabrielcik on 2010-02-08
Yes i know, i tried already sudo alsactl store and sudo alsactl store 0 but nothing....

is there any other way to set int mic by default by modifying some other file?

Thank you!

---

### Post by gabrielcik on 2010-02-08
I notice that inside the file:

/var/lib/alsa/asound.state

under "input Source" there is really "Int Mic" even after rebooting but alsamixer doesn't load this parameter and take instead "Front mic"

I have to use alsactl restore for to push alsamixer to use int mic.

What to do?

---

### Post by crichard on 2010-02-08
install gnome-alsamixer from Synaptic Package Manager, & try various options.

> [SIZE=2]sudo alsactl store 0[/SIZE]
It helped me once.

---

### Post by gabrielcik on 2010-02-08
I still didn't try to install gnome-alsamixer...

anyway i was able to fix it in another way:

i placed alsaclt restore inside startup Applications and finally it works now!

Thank you:)

---

