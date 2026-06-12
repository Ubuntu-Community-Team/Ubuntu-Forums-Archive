---
title: "warning: show-stopper NVidia bug in 10.04"
date: 2010-04-29
forum: General Help
---

### Post by Locke2053 on 2010-04-29
If you have an NVidia [edit] 9500 GT graphics card, do not upgrade to 10.04!

I just did a fresh install of the 64 bit version. 9.10 had previously work fine on this same system. But after enabling NVidia drivers and rebooting, my system loads to a black screen. No errors, no anything. Just black.

So, if you use the NVidia drivers and want to upgrade to Lucid, I suggest you wait until this problem is fixed.

And while I'm on the topic: is there a way to tell 10.04 to load with basic graphics drivers? I would really like to use my system without reinstalling everything...

---

### Post by kelvin spratt on 2010-04-29
no such problem with my nvidia card installed x64bt  today.

---

### Post by renkinjutsu on 2010-04-29
i think Ubuntu's implementation of Nouveau doesn't support your card. You can try to install nouveau from source yourself or install the Nvidia binary package

---

### Post by oldfred on 2010-04-29
With the RC I had to add nomodeset for both the install and the initial boot. My Card is GeForce 9600GT. Once I got nvidia's driver installed It worked just fine. In the release notes they mention the nomodeset for some video cards.

---

### Post by Locke2053 on 2010-04-29
Fred, what do you mean by "add nomodeset"? How could I do this? Why isn't it done automatically?

---

### Post by Calash on 2010-04-29
No problems on my 9600.  

Can you pick Recovery Mode from GRUB?

---

### Post by KinKiac on 2010-04-29
Is this bug with the drivers in repos or the Nvidia drivers from their website?

---

### Post by cariboo on 2010-04-29
I've been using the restricted drivers for a 8400GS, 9400GT and GT210 in Lucid since the start of testing, the only problem I've run into is my crt isn't being detected properly through my kvm.

To the op, start in recovery mode and at the prompt type:

```
nvidia-xconfig
```

The above command will create an /etc/X11/xorg.conf then reboot

---

### Post by sgage on 2010-04-29
No problem here with nvidia drivers and 8500 GT.

---

### Post by schmolch on 2010-04-29
there is a confirmed bug where multi-gpu nvidia setups will freeze before the gui comes up.

---

### Post by oldfred on 2010-04-29
On my machine it did not freeze up but turned the monitor off. I boot from a USB key and its light was still flashing so I knew the install was still running. 

Since I used a USB key booting multiple ISOs with grub2 I edited my grub kernel boot line and then after the install edited the boot menu to add the nomodeset to the kernel line. Immediately installed nvidia & it worked.

I have an older monitor and the DVI cable/connector only has terminals for single link even though the 9600 supports dual link. I see in the log a switch from one to two and wonder if that is the problem??

---

### Post by Locke2053 on 2010-04-30
> **renkinjutsu said:**
> i think Ubuntu's implementation of Nouveau doesn't support your card. You can try to install nouveau from source yourself or install the Nvidia binary package

I don't know what nouveau is, and I don't care. Ubuntu's "Hardware Drivers" application recommended that I install "NVIDIA accelerated graphics driver." I did. Now my computer is a brick. If this driver won't work on my hardware, it should not recommend that I install it.

Major, show-stopper bug. Very frustrating (as 9.10 worked fine).

lspci says I have an nVidia GeForce 9500 GT rev a1. This is hardly an ancient piece of hardware.

---

### Post by Locke2053 on 2010-04-30
> **Calash said:**
> No problems on my 9600.  

Can you pick Recovery Mode from GRUB?

Sorry, my card is a 9500 GT, actually. 

And I don't see an option for Recovery Mode. I tried holding down ESC while booting, and that did nothing.

---

### Post by williamdabastrd on 2010-04-30
> **Locke2053 said:**
> I don't know what nouveau is, and I don't care. Ubuntu's "Hardware Drivers" application recommended that I install "NVIDIA accelerated graphics driver." I did. Now my computer is a brick. If this driver won't work on my hardware, it should not recommend that I install it.
 
Major, show-stopper bug. Very frustrating (as 9.10 worked fine).
 
lspci says I have an nVidia GeForce 9500 GT rev a1. This is hardly an ancient piece of hardware.
 
If you installed it from the hardware drivers, it's a NVIDIA driver issue, not an ubuntu one. The hardware drivers installs drivers provided by NVIDIA, and NVIDIA should fix it. Secondly, I find it inappropriate to be so rude to someone trying to help you. See here for what Nouveau is: [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)
 
When your PC boots up, assuming you have GRUB2 installed, press ESC to reach the config settings. Edit the 'Ubuntu' and add 'nomodeset' to the end. After you type that, press enter. Note that you must press ESC BEFORE the Ubuntu logo shows up. Try pressing repeatedly after your BIOS screen.

---

### Post by kill4killin on 2010-04-30
> **Locke2053 said:**
> Fred, what do you mean by "add nomodeset"? How could I do this? Why isn't it done automatically?

I believe he is referring to the kernel option for "nomodeset"

You would edit fstab and in the boot line for the kernel you are using you would add in "nomodeset" to the end of the Kernel line, it should look something like this:

```
LABEL=/         /               ext3         defaults,nomodeset                1 1
```

It won't look exactly the same but you put in the nomodeset as I have above (If I'm not mistaken, it's been a while since I've done any modifications to the fstab)

---

### Post by dino99 on 2010-04-30
> **Locke2053 said:**
> Sorry, my card is a 9500 GT, actually. 

And I don't see an option for Recovery Mode. I tried holding down ESC while booting, and that did nothing.

which nvidia driver is installed: nvidia-current from official lucid repo, from ppa, from nvidia ?

i'll suggest to remove/purge ALL the nvidia packages installed, check your repo only have legacy repo, update the repo, then install nvidia-current, nvidia-current-modaliases and nvidia-common.

reboot

---

### Post by oldfred on 2010-04-30
The nomodeset is a parameter in the grub commands (not fstab as kill4killin posted).

kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=f9b2a783-78ba-4437-9bc5-9d8cfa86ff0c ro [COLOR=Blue]splash quiet[/COLOR] [COLOR=Red]nomodeset[/COLOR]

Since I knew I was installing nvidia I did not permanently change this in  /etc/default/grub but just edited it one time on first boot. I removed [COLOR=Blue]splash [/COLOR]& [COLOR=Blue]quiet[/COLOR] & added [COLOR=Red]nomodeset[/COLOR]. I think on the install CD version you can do the same thing with f6, but I booted from a USB and just added it to my grub entry there & it worked.

---

### Post by mobius777 on 2010-05-12
Hi, I am having this exact problem as well. I also have a GeForce 9500 GT (Zotec brand). The problem only exists for the proprietary drivers. Running with the "nv" driver set in xorg.conf (instead of nvidia), allows me to work perfectly fine... except no 3d and thus no Compiz. But with the proprietary driver's installed, I get the black screen at boot up. That is, after GRUB, and after it shows the "ubuntu" boot screen, the screen just goes black when it should show the login screen. The system is not frozen. I can get to the terminal with cntl-alt-f2, which allows me to edit config files and issue a reboot, which is a good thing. I guess the problem is either with nVidia's drivers, or with the video card itself, not really with Ubuntu. Oh, and I'm running 10.04, and I did upgrade from 9.10 where I did not have this issue.

---

### Post by mobius777 on 2010-05-12
Update: My video card (9500 GT from Zotec) actual has 2 DVI outs. I switched to the other one and the results are sort of better. Now I can use the proprietary drivers, and about half of the time the system will boot and I'll see the login screen, I can login, and everything is fine for that session. When I get the black screen, hitting cnt-alt-f1 to get to terminal, and then cntl-alt-f7 to go back to desktop, I can see the login screen and can proceed. Also when the screen powers off, I sometimes will have to do the cntl-alt-f1 / cntl-alt-f7 trick to get back. That's annoying, but it works.

I am going to say its a problem with the video card itself. That is to say, the card is a bit flaky. I might get a new video card from a major brand and see if that's any better.

---

