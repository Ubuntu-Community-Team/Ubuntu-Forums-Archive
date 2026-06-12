---
title: "Cairo-Dock (w/ OpenGL)"
date: 2009-10-25
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-10-25
I been googling around for a resolution w/ a problem w/ Cairo-Dock w/ OpenGL. There is a big ugly black background as if my composit manager is not running. I managed to find one solution (adding, Option "AccelMethod" "uxa") Works, but I read it is a bit unstable and found that is true, Lost complete desktop, system crashing etc, etc.(removed that option from xorg.conf. Was wondering if any1 else might be having this problem or had and resolved it? Also I did try "fake transparency" But only went from a black backgroung to the nautilus default background.

---

### Post by Feelin_froggy8877 on 2009-10-25
This problem is on a Dell Inspiron w/ intel graphics chip (not sure how to get graphics specs from within ubuntu)

---

### Post by macaholic on 2009-10-25
> **Feelin_froggy8877 said:**
> I been googling around for a resolution w/ a problem w/ Cairo-Dock w/ OpenGL. There is a big ugly black background as if my composit manager is not running.
This implies that you do indeed have a compositing manager running? Are you using the visual effects that come with ubuntu or some other means of compositing?

---

### Post by Feelin_froggy8877 on 2009-10-25
Yes I am running compiz. And no problems w/ any effects.

---

### Post by macaholic on 2009-10-25
What is your output of ```
sudo lshw -C display 
```?

---

### Post by Feelin_froggy8877 on 2009-10-25
*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

(on an off-note, how do u get that code in its own box there like that?

---

### Post by macaholic on 2009-10-25
From the looks of it, your driver isn't configured correctly, I believe there should be a "driver=..." in the configuration line.
You can try running ```
sudo apt-get update 
sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then restart X or log out and log back in.
To get the code wrapped in the "code" box, you hit the # button in an advanced reply.

---

### Post by Feelin_froggy8877 on 2009-10-25
I'll give it a try, Thanks for the interest.

---

### Post by Feelin_froggy8877 on 2009-10-25
```
k-dawg@ubuntu:~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
k-dawg@ubuntu:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20091025173839
k-dawg@ubuntu:~$ sudo lshw -C display
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
```

Went ahead w/ the dpkg-reconfigure, no changes it looks.

---

### Post by Feelin_froggy8877 on 2009-10-25
no other suggestions?

---

### Post by macaholic on 2009-10-26
You could try running the command with -o or -c, I am not entirely sure what these do as I am not familiar with cairo.
Another thing to try would be adding ```
Section "Extensions"
    Option "Composite" "Enable"
EndSection

```
to your /etc/X11/xorg.conf file.

---

### Post by fabounet on 2009-10-26
your card is maybe not yet fully supported by the drivers.
on a Dell Mini9 with an Intel GMA945 the dock (v2.1.1) works correctly with OpenGL.
you can report your problem to the Intel drivers team, it can benefit to their work.

---

### Post by Feelin_froggy8877 on 2009-10-26
How would I go about properly reporting the issue?

---

### Post by m4tic on 2009-10-26
if you want trsnsparency, I use a SiS chip so no desktop effects for me. 

gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true

---

### Post by m4tic on 2009-10-26
I don't know how it will affect compiz

---

### Post by Feelin_froggy8877 on 2009-10-30
Upgrading to (Karmic 9.10) resolved this issue.

---

