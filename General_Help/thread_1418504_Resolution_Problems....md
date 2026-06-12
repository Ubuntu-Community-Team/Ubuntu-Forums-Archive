---
title: "Resolution Problems..."
date: 2010-02-28
forum: General Help
---

### Post by srChubs on 2010-02-28
I just installed 9.10 and the only options for resolutions is 800x600 and lower on my Samsung 22". I would like to have the resolution at 1600x900. My graphics card is NVIDIA 6150. Anyone help??

---

### Post by srChubs on 2010-02-28
here is a link to the message that i get in the NVIDIA settings..... 

[http://i469.photobucket.com/albums/rr53/anth0ny_92/Screenshot.png?t=1267394316](http://i469.photobucket.com/albums/rr53/anth0ny_92/Screenshot.png?t=1267394316)

help, please and thank you

---

### Post by themusicalduck on 2010-02-28
Have you installed the Nvidia drivers from System > Administration > Hardware Drivers?

It should be configured automatically after that but if it isn't you need to use nvidia-settings

Run it as root by pressing alt+f2 and typing in ```
gksudo nvidia-settings
``` and setup the resolution you want under X Server Display Configuration.

Once finished, click on Save to X Configuration File and then reboot.

EDIT: guess I posted just after you made your last post..

In that case, just open a terminal (Applications > Accessories > Terminal) and run ```
sudo nvidia-xconfig
```

---

### Post by srChubs on 2010-02-28
ok, when i try to activate the driver it gives me this... 

[http://i469.photobucket.com/albums/rr53/anth0ny_92/Screenshot-2.png?t=1267394898](http://i469.photobucket.com/albums/rr53/anth0ny_92/Screenshot-2.png?t=1267394898)

oh then i tried to type "sudo nvidia-xconfig" and it said command not found?

---

### Post by themusicalduck on 2010-02-28
Normally that message comes up if you have something else open that manages packages, like synaptic or the software centre or update manager. If you do then close it and try again.

But looking in the screenshot, it doesn't look like anything is open.. perhaps try restarting and then try it again.

---

### Post by srChubs on 2010-02-28
i restarted and it still says "command not found"
when i typed in "sudo nvidia-xconfig"

---

### Post by themusicalduck on 2010-02-28
Have you tried to activate the drivers again in the hardware drivers dialog? That's the error I meant. The nvidia-xconfig command won't work unless the driver is installed properly first.

---

### Post by srChubs on 2010-02-28
thank you, it works fine now.

---

