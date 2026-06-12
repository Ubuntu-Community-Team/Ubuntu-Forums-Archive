---
title: "VESA Driver install - 9.10"
date: 2009-11-02
forum: General Help
---

### Post by nixed242 on 2009-11-02
Currently my system boots using the nvidia driver. If I were to use "**rmmod nvidia**" to remove it, using "**modprobe vesafb**" should install the vesa driver for good right? I wouldn't need to compile anything special to get it to work?

---

### Post by nikgare on 2009-11-02
Why do you need to use the vesa driver?

I have a headless system where I created xorg.conf and put this in it so that the vesa driver would be used:
```

Section "Device"
        Identifier      "Configured Device"
        Driver  "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31-61  
        VertRefresh 50-75
        Modeline "1024x768" 25.20 640 688 784 800 350 410 412 449
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Device"
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

```

---

### Post by nixed242 on 2009-11-02
Thanks for the reply.

When I boot the Kernel with the NVIDIA driver, it crashes my system. I either need to load the VESA or the VGA driver on boot to possibly keep this from happening. X works fine with its NVIDIA driver. I just need the Kernel to stop loading the NVIDIA Module at boot.

---

### Post by nikgare on 2009-11-02
Do you mean that you computer crashes straight away, just after the grub screen, or does it crash when staring X?

If your computer crashes straignt after the boot screen, then something like this might help:
sudo aptitude remove nvidia-glx-173

If it's the second, then something like what I posted above should work (make sure that the modelines are correct for your monitor!)
You could also try looking in the xorg logs to see if any erros are given.

---

### Post by nixed242 on 2009-11-02
It freezes after the desktop is loaded. I'll try your suggestion above. 

The only thing that confuses me about this is that the NVIDIA drivers work fine when I run gdm from the Revovery Mode's command line prompt. I'm even able to use compiz, but the system crashes when it boots normally. I'm suspecting that the kernel loads something (the NVIDIA driver) at boot which makes it crash.

---

### Post by anoland on 2009-11-03
Nvidia released a new driver last week. I had problems until I upgraded mine.

[http://www.sizzledcore.com/2009/11/02/nvidia-graphics-drivers-19042-for-ubuntu-910/](http://www.sizzledcore.com/2009/11/02/nvidia-graphics-drivers-19042-for-ubuntu-910/)

---

### Post by nixed242 on 2009-11-03
Hi, Thanks for the replies. I filed a Bug Report regarding this issue since a lot of people are having it. I think it runs deeper than the NVIDIA drivers. I think the real issue maybe when "Init" is called. I think it's running something that's causing a crash, or something wasn't set up right on my system. Last night I was able to replicate the freeze from the command prompt without going into X. I ran "telinit 5" and after 20 seconds, I was frozen at the command line. 

I'm determined to fix this issue, and I'll share the resolution if I can reach one.

---

### Post by buckyaustin on 2010-03-23
I just copied and pasted your xorg.conf and it worked out of the box for my computer which is the notorious SIS graphics chip. My xorg was blank. Thank you, you will get more praise around the world if you spread this as the solution to the SIS graphics problem. All graphics features for me work now :)

---

