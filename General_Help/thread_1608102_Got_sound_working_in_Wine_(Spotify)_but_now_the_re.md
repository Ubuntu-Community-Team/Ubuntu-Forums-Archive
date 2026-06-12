---
title: "Got sound working in Wine (Spotify) but now the rest of the system is on mute"
date: 2010-10-28
forum: General Help
---

### Post by anonymousrobot on 2010-10-28
So I followed the instructions at [http://www.spotify.com/uk/help/faq/wine/](http://www.spotify.com/uk/help/faq/wine/)
and got Spotify working, problem is now the only sound working is in Spotify.

Any ideas, is this to do with Wine or what?

---

### Post by anonymousrobot on 2010-10-28
Wow I don't know what happened there, just restarted my computer and I'm running XUbuntu...

---

### Post by 3Miro on 2010-10-28
I have seen issues with sound under KDE (Kubuntu), where one application will lock the others out. However, those are very rare under Gnome (Ubuntu).

How much have you played with winecfg and the sound settings. What do have as a setup there.

---

### Post by anonymousrobot on 2010-10-28
Well I changed the sound thing to OSS or something, sorry I can't remember, see the post above yours.

I really have no idea what just happened.

---

### Post by matt_symes on 2010-10-28
Hi

Try changing to Alsa. OSS is legacy.

Kind regards

---

### Post by 3Miro on 2010-10-28
I don't think Ubuntu and Xubuntu are running different sound schemes, so this is not the issue.

The issue is OSS, which a deprecated standard and it is not really supported. The instructions on their web-page are for Ubuntu 9.10 and somewhat older versions of wine. Check on winehq forums for more up-to-date information.

---

### Post by anonymousrobot on 2010-10-28
Okay thanks guys, sound is working now.

Any ideas how to get back to Ubuntu, is there a system restore on Linux?

---

### Post by DirtyPC on 2010-10-28
[IMG]http://i55.tinypic.com/2cscieh.png[/IMG]

---

### Post by 3Miro on 2010-10-28
> **anonymousrobot said:**
> 
Any ideas how to get back to Ubuntu, is there a system restore on Linux?

What do you mean? There is "safe" mode that you can enter from boot if you press and hold shift. What do you mean by going back to Ubuntu.

---

### Post by DirtyPC on 2010-10-28
Try those settings, they work fine for me, seeing as Xubuntu and Ubuntu have the same sound schemes, hope this helps! :-)

---

### Post by DirtyPC on 2010-10-28
> **3Miro said:**
> What do you mean? There is "safe" mode that you can enter from boot if you press and hold shift. What do you mean by going back to Ubuntu.
He means changing his desktop environment from Xubuntu to Ubuntu.. and i'm not sure if thats possible...

---

### Post by matt_symes on 2010-10-28
Hi

sudo apt-get install ubuntu-desktop from the terminal. Then when you login you can select ubuntu

Are you currently running xubuntu or kubuntu?

Kind regards

---

### Post by 3Miro on 2010-10-28
You can install Ubuntu-desktop and switch between XFCE and Gnome. Those are Desktop Environments, there is also KDE and LXDE. You can Google them.

---

### Post by anonymousrobot on 2010-10-28
Right my computer wouldn't even start. I had to boot from the Ubuntu CD, running on that now.

Erm I think I'm gonna try backing up and reinstalling a fresh copy now.

---

### Post by matt_symes on 2010-10-28
Hi

> **anonymousrobot said:**
> Right my computer wouldn't even start. I had to boot from the Ubuntu CD, running on that now.

Erm I think I'm gonna try backing up and reinstalling a fresh copy now.

Eh?? What happened

Kind regards

---

### Post by anonymousrobot on 2010-10-28
> **matt_symes said:**
> Hi



Eh?? What happened

Kind regards

Got this error message...

init: udevtrigger main process (440) terminated with status 1
init: udevtrigger post-stop process (449) terminated with status 1
init: udevtrigger main process (447) killed by TERM signal 

Other people seem to have got this problem, can't find any solutions though.

---

