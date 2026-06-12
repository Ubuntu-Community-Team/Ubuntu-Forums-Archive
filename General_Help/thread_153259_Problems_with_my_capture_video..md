---
title: "Problems with my capture video."
date: 2006-03-31
forum: General Help
---

### Post by Akli on 2006-03-31
I have no idea of what this means:

akli@akli:~$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/akli/.tvtime/tvtime.xml"
I/O error : Permission denied
Cannot change owner of /home/akli/.tvtime/tvtime.xml: Permission denied.
videoinput: Can't get tuner info: Invalid argument

    Your capture card driver: zoran [DC30plus[0]/PCI:0000:00:10.0/2309]
    does not support studio-quality colour images required by tvtime.
    This is a hardware limitation of some cards including many
    low-quality webcams.  Please select a different video device to use
    with the command line option --device.

    Message from the card was: Invalid argument

---

### Post by andrewsawyer on 2006-03-31
Which tuner card are you using?  Also have you tried running tvtime in sudo?

---

### Post by Akli on 2006-03-31
Running it with sudo gives the same message, apparently it is incompatible with my capture video card.

I can say that my problem is solved sice it works with xawtv.

Mirovideo dc30

[http://www.livingroomlinux.com/v4lwiki/index.php/Zoran_devices](http://www.livingroomlinux.com/v4lwiki/index.php/Zoran_devices)

---

### Post by Akli on 2006-03-31
In order to have a full screen display, I have to change my screen resolution to 640*480.

Conclusion: My capture video card sucks (ancient).

---

