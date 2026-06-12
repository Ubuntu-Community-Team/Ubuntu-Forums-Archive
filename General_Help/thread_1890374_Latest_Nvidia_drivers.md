---
title: "Latest Nvidia drivers"
date: 2011-12-03
forum: General Help
---

### Post by Ruffman on 2011-12-03
Hi,
I want to install the latest nvidia drivers. I read a lot of solutions but none of them work for me. I Have an Asus N55SF with an Nvidia GT555m and the latest Xubuntu (11.10). 
after I tried this [http://www.multimediaboom.com/install-nvidia-driver-ubuntu-1-04-11-10-ppa/](http://www.multimediaboom.com/install-nvidia-driver-ubuntu-1-04-11-10-ppa/)  they are installed but not in use. As soon as I run nvidia-xconfig  to generate /etx/X11/xorg.conf my X-server refuses to restart. I can only restart it if i delete this file. Same if I download them on nvidia's homepage and install them. xorg.conf refuses to work. 
how can I install them properly?

---

### Post by BC59 on 2011-12-03
Sometimes is better not to insist to change the recommended from Ubuntu drivers, because you are having problems later. For example your computer after a kernel update, will not recognize the manually installed drivers.
There is a way to do it just check here but I would not recommend the manual installation.

[http://www.gpugrid.net/forum_thread.php?id=266](http://www.gpugrid.net/forum_thread.php?id=266)

---

### Post by Ruffman on 2011-12-03
I tried that already without any success. Envy didn't work anymore, too.
I want to install them, because I see no other way to get my second monitor up in xfce

---

### Post by BC59 on 2011-12-03
I don't now if you tried:

Download the drivers from the NVIDIA website into Home.

Press ctrl-alt-F1 to appear the text login screen.

login as root 

Run ```
sudo /etc/init.d/gdm stop
``` to stop the X server

Run ```
sudo sh THE NAME OF THE PACKAGE OF THE DRIVER
``` to install the driver.

Follow the instructions for the installation.

Run ```
sudo /etc/init.d/gdm start
``` to start the X Server again

Run ```
sudo reboot
```

---

### Post by Ruffman on 2011-12-03
Yes this is what I mean with "they are installed"... 
It execudes nividia-xconfig which inserts xorg.conf to /etc/X11/ which then refuses to boot up my X again.
it has already a failure on gdm start. I have to remove my xorg.conf to get it running again!
Note: I have added blacklist.nouveau=1 to my grub2 kernel line

---

### Post by stinkeye on 2011-12-03
There used to be a bug where jockey told you 
"The driver is activated but not in use".

Jockey is telling me this on 11.10, but ...
```
glen@Oneiric:~$ **lspci -k | grep -A3 VGA**
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
	Subsystem: nVidia Corporation Device 066d
	**Kernel driver in use: nvidia**
	Kernel modules: nvidia_current, nouveau, nvidiafb
```
```
glen@Oneiric:~$ nvidia-settings -q NvidiaDriverVersion -t
**290.10**
```

Updated from x-swat/x-updates ppa.
I do not have an xorg.conf file.

---

### Post by Ruffman on 2011-12-03
i've checked the same commands from your post. I only get empty output on the second command (nvidia-settings), while the rest is similar. I have the same output in additional-drivers, too.
I assume to "use" the driver you have to run nvidia-xconfig which prevents my X from working...
Any solution?

---

### Post by stinkeye on 2011-12-03
Can you open nvidia-settings?
Synaptic shows me nvidia-settings and nvidia-current are both the same version.

All I did to get the latest driver was, when I first installed 11.10
I downloaded and  installed nvidia-current in jockey and then later on
added the ubuntu-x-swat/x-updates ppa which upgraded 
**nvidia-current** and **nvidia-settings**.

Didn't run **sudo nvidia-xconfig** or save any config file.
I do not have an /etc/X11/xorg.conf file.

---

### Post by Ruffman on 2011-12-03
hmm after rebooting, it shows me, that they are working (but they doesn't seem so) .
the current state of mine is in the attachment...
really weird

---

### Post by BicyclerBoy on 2011-12-03
Asus N55 uses optimus..

Have a look/study of
Bumblebee
Ironhide

---

### Post by Ruffman on 2011-12-03
as far as I understand "Nvidia Optimus"  is an option, not a requirement. But thanks for that hint, I'll investigate it further...
if I want to install bumblebee it points me to ironhide... which is the right one, and can someone find a working solution if I have already installed nvidia drivers?

---

### Post by BicyclerBoy on 2011-12-03
Requirement ?? you only have an requirement if you choose to buy an optimus graphics device.

Optimus concept exists in AMD & nVidia graphics h/w. 
It is used in docking stations & DIY external video card docks.

Optimus is not optional for most current h/w using it. It is designed/built for windows.

There are a couple of optimus h/w variations.
This depends on the design around framebuffer/mux & BIOS settings. It is cheaper to not have the mux shared framebuffer. So this h/w has to use iCPU/GPU only or ironhide.

---

### Post by Ruffman on 2011-12-03
and that was what I want, as I read in archWiki that optimus isn't supported. A clean Nvidia driver installation and disable the intel one. That was what I meant with "requirement". I thought I can run the nvidia driver alone without optimus. But now I'm interested in bumblebee/ironhide.
Can someone point me the difference?

---

### Post by beew on 2011-12-03
> **Ruffman said:**
> as far as I understand "Nvidia Optimus"  is an option, not a requirement. But thanks for that hint, I'll investigate it further...
if I want to install bumblebee it points me to ironhide... which is the right one, and can someone find a working solution if I have already installed nvidia drivers?

It is only optional if your BIOS has an option to turn it off. I don't know for sure but I sort of remember reading that you have to remove Nviidia's driver for bumblebee to work (it will install the Nvidia driver as a dependencies). You should check with the bumblebee project.

In general though, --without Optimus, that is, --you can install the latest Nvidia driver by adding xorg-edgers ppa to your sources list.
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") 

I am having problems with the latest 290.10 (gnome-screenshot doesn't shut down after taking screenshots and uses 100% cpu) so I have reverted back to 285.05.

---

### Post by darmok47 on 2012-01-13
Hi,
I have a problem that maybe can be solved with nvidia drivers.
I have installed ubuntu 11.10 on my new asus n55sf, blacklisted nouveau driver in order to use acpi on, here my problme: sometimes when screensaver start, my display do something strange, starting from a blank screen and going in some way that seems to be related to an hardware problem to black screen, then the pc freeze and the screen remain black despite any operation tha i can do, but the OS appearto still work.

I dont think is an hardware issue because on Win7 these problems never appeared.

Anyone can help me?

thanks

Darmok47

---

### Post by Pilot6 on 2012-01-13
Your problem will be fixed by unity 5.0. Nvidia divers even beta 295 do not help.

---

### Post by darmok47 on 2012-01-13
I dont use unity, i have installed gnome3, despite i hate it.
So my problem manifest itself in gnome3

---

### Post by darmok47 on 2012-01-14
update: when display switch off like after the usual screensaver time and i do something everything return to normal
any ideas?

---

