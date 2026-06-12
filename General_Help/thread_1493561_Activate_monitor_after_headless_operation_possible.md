---
title: "Activate monitor after headless operation possible?"
date: 2010-05-26
forum: General Help
---

### Post by CharlesA on 2010-05-26
Hi,

I had a problem with my server (which is running headless, no keyboard, monitor). I hooked up a monitor, but it wouldn't output any video from either port on the video card. It's using a GeForce 9400 GT, if that matters, no GUI installed.

Is it possible to "wake up" the video card from a terminal?

As of now, if I have problems that need me to be able to see the screen, I need to login blindly and do a sudo reboot to get the video to display.

Any help is appreciated. :)

Thanks.

EDIT: I am running Lucid x64 server on the machine.

---

### Post by CharlesA on 2010-05-27
Any ideas?

---

### Post by akakingess on 2010-05-27
Not sure about waking up the card, but since it is a headless server, usually piping in via TTY or SSH should be an option of some sort (I don't do that myself, so sorry if no help whatsoever, just trying to help through some ideas out there). Good luck and let us know if that won't work for you, and I will investigate the 'waking the card' option.

---

### Post by Snow986 on 2010-05-27
If port 22 is open on it, get on the same network and find its IP.  Then you can ssh in by 
```

ssh -X username@IP

```

then restart X to see if it will come up
```

sudo /etc/init.d/gdm restart

```

If that doesn't work, then try a reboot.

---

### Post by CharlesA on 2010-05-27
The problem was that I totally locked it down, so I couldn't even get in with SSH. It's not running an X server, so I don't have GDM installed.

The only thing related to X is  x11-common.

I've hooked it up to a monitor and just unplugged the keyboard for the time being. If I plug in a keyboard, the display comes up fine.

I would have thought that if a monitor was plugged into a certain port on the video card, removed and then plugged back in to the same port, any keyboard activity would "wake" it up.

---

### Post by Snow986 on 2010-05-27
Ahh, I now see you don't have gui installed!  Glad you got it working.  You should think about editing openSSH config file so port 22 is open (but make sure its secure) so you can ssh if there's any issues since its headless.

---

### Post by CharlesA on 2010-05-27
Well, the SSH port was open, but I screwed up my firewall rules and ended up causing all network traffic to be dropped. SSH doesn't work very well when it won't connect. :p

---

