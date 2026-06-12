---
title: "How do I reset to Ubuntu's default sound setup and drivers?"
date: 2010-01-30
forum: General Help
---

### Post by Meetze on 2010-01-30
My Karmic box was working great until recently.

I was trying to troubleshoot some software issues and was instructed to run apt-get autoremove. To make a long story short, I messed up my sound settings to the extent that the driver doesn't even show up under the hardware settings.

When I boot from the Ubuntu live CD, the sound works fine.

So, is there any way I can reset to Ubuntu's default sound setup without having to reinstall the OS?

Thanks.

---

### Post by Compintuit on 2010-01-30
I've also messed up my sound before. I fixed it by removing ~/.pulse. If that doesn't work, if you log in as another user, and sound still doesn't work, you probably uninstalled something you shouldn't have. In synaptic there is a log; see what you removed, and reinstall it. Good luck!

---

### Post by dcstar on 2010-01-30
> **Meetze said:**
> My Karmic box was working great until recently.

I was trying to troubleshoot some software issues and was instructed to run apt-get autoremove. To make a long story short, I messed up my sound settings to the extent that the driver doesn't even show up under the hardware settings.

When I boot from the Ubuntu live CD, the sound works fine.

So, is there any way I can reset to Ubuntu's default sound setup without having to reinstall the OS?

Thanks.

Reinstall the ubuntu-desktop package.

---

### Post by Meetze on 2010-01-30
> **dcstar said:**
> Reinstall the ubuntu-desktop package.

That was it.  You saved me quite a bit of work. Thanks.

---

### Post by Meetze on 2010-01-31
I ran alsamixer and instantly lost my sound again.  No amount of running sudo apt-get install --reinstall ubuntu-desktop is bringing it back either. LOL

---

### Post by NightwishFan on 2010-01-31
Try this just in case:
```
sudo apt-get install ubuntu-desktop && sudo apt-get -f install
```

If it asks you to remove many packages, hit "no" when prompted, and post the output here. If everything is in order, try the steps listed here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Meetze on 2010-01-31
> **NightwishFan said:**
> If everything is in order, try the steps listed here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I didn't actually have to re-configure anything.  Per the instructions on the link you gave me, just running sudo alsa force-reload from the terminal fixed the issue.  In fact, I'm having to run it everytime I boot up in order for the sound device to show up in the preferences menu. System -> Sound -> Hardware

It's like Ubuntu doesn't remember the sound settings when I shut down or reboot the computer.

---

### Post by NightwishFan on 2010-01-31
Are your mixer settings right? Run this command to view them:
```
alsamixer -c0
```

---

### Post by Meetze on 2010-01-31
> **NightwishFan said:**
> Are your mixer settings right? Run this command to view them:
```
alsamixer -c0
```

I don't see anything out of the ordinary in alsamixer.  It is reset every time I run the sudo alsa force-reload command anyway.

---

### Post by floris83 on 2010-02-19
> **dcstar said:**
> Reinstall the ubuntu-desktop package.

Hello, 

I'm new to Linux and Ubuntu. If anyone could help me out?

I have the same problem with my sound. So how do I re-install the ubuntu-desktop package?

hope you can explain.

regards

ps. I'm using Ubuntu 9.10 64-bit

---

