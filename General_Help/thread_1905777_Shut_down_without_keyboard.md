---
title: "Shut down without keyboard?"
date: 2012-01-07
forum: General Help
---

### Post by mk5500 on 2012-01-07
Is there any way I can get a clean shutdown on an Ubuntu PC that doesn't have the keyboard connected?

I have a system setup as an MP3 player that starts up and plays when it boots but need a way to shut it down cleanly or the startup sequence can be "iffy".

Someone suggested installing Ubuntu server edition (and I'm still goofing with that) but wonder if there isn't a script that maybe detects a power off button press and takes it from there? or something?

I can't do it based on "the last MP3 played etc" because I want it to be a completely random player. (just now thinking -- there is a possibility I could have it turn off at a weird time, like 3am or something).

---

### Post by galvatron408 on 2012-01-07
if you check your system power settings, there should be some menu there that asks what to do when the power button is pressed... just change that to "shutdown". I did that to my laptop and it works great.

---

### Post by imachavel on 2012-01-07
> **mk5500 said:**
> Is there any way I can get a clean shutdown on an Ubuntu PC that doesn't have the keyboard connected?

I have a system setup as an MP3 player that starts up and plays when it boots but need a way to shut it down cleanly or the startup sequence can be "iffy".

Someone suggested installing Ubuntu server edition (and I'm still goofing with that) but wonder if there isn't a script that maybe detects a power off button press and takes it from there? or something?

I can't do it based on "the last MP3 played etc" because I want it to be a completely random player. (just now thinking -- there is a possibility I could have it turn off at a weird time, like 3am or something).

ubuntu server edition? I thought vi would give you the options to edit dhcp i.p. settings in gedit configure text app. I didn't know you needed a separate edition of ubuntu for server purposes. Is it just an entirely different distro??

---

### Post by imachavel on 2012-01-07
> **mk5500 said:**
> Is there any way I can get a clean shutdown on an Ubuntu PC that doesn't have the keyboard connected?

I have a system setup as an MP3 player that starts up and plays when it boots but need a way to shut it down cleanly or the startup sequence can be "iffy".

Someone suggested installing Ubuntu server edition (and I'm still goofing with that) but wonder if there isn't a script that maybe detects a power off button press and takes it from there? or something?

I can't do it based on "the last MP3 played etc" because I want it to be a completely random player. (just now thinking -- there is a possibility I could have it turn off at a weird time, like 3am or something).

strange. yes without keyboard scroll mouse over to system settings or shutdown icon or menu depending on which distro you are using. From there the shutdown button should work.

Usually people ask the opposite, without a mouse how to shut down, which I believe is:

sudo shutdown now

to reboot:

sudo reboot now

and try and avoid:

sudo halt now

as that sends the kill signal, not giving your pc enough time to stop programs and apps and might cause data loss. Although it rarely ever will, it's still possible. I've just heard to avoid it.

---

### Post by QIII on 2012-01-07
Is it on a network or is it entirely stand-alone?

---

