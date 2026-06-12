---
title: "update manager just stopped"
date: 2010-06-21
forum: General Help
---

### Post by Zanven on 2010-06-21
I ran the update manager and during the updating process (it was updating grub and boot image) it stopped and is sitting on that. I know shutting down or forcing it to stop could be disastrous.

I am not very expierienced so I don't know what information I need to get help so if you can suggest action or request more information that can help I'd appreciate it.

The urgency lies in that the computer is in my room and makes sleep hard but I won't shut it down until this is solved.

It is late so I am going to try to sleep. Hope I can get this figured out. Thanks in advance

---

### Post by Zanven on 2010-06-21
Ok, I went ahead and stopped the process against my instinct thinking if something goes wrong I could backup and start over but everything seemed fine and I ran dpkg --config -a and reboot and ran the package repair in safe mode and grub update

Now at grub after updating there is now three kernels (that is what the version numbers are right?) and the oldest one only going to command line and no graphical interface. The middle one runs fine and the newest one has no cursor. Like I move the mouse and buttons highlight so it is there but it is invisible.
any clues on fixing that?
Also after fixing that is it necessary to have all three listed or can you remove 2 of them?

Not a problem but something to note is the start-up splash before grub took a long time to go to grub the first few times (like 2 minutes) but now is fine. I thought that only had to do with the mother board not any bootable partition on a hard drive so that confuses me. any clue?
Like I said I'm sure its not a problem but maybe its a potential one?

Any information I can give that can help me? like and package, log info or what my grub looks like?

---

### Post by Zanven on 2010-06-24
Bumping. Sorry if this is solved somewhere else. if it is can someone link me? I tried searching for the solution

---

### Post by el consul on 2010-06-24
Did you try filling bug reporting -
[http://ubuntuforums.org/showthread.php?t=1011078&highlight=package+manager](http://ubuntuforums.org/showthread.php?t=1011078&highlight=package+manager)
    (copy & paste)
I don't know if you have to open an account
[https://launchpad.net/](https://launchpad.net/)        

there is a way to make the system auto report the problem issue I think on terminal write 
sudo su       or maybe      gksu gedit etc/default/apport         this last one you have to change number 0 to 1
but the one I like the most is           apt-get     this one kind like describe like a how to restore problem  check it out

---

