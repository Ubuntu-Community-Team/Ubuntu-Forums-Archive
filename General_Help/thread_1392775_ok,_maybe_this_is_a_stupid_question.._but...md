---
title: "ok, maybe this is a stupid question.. but..?"
date: 2010-01-28
forum: General Help
---

### Post by somerefriedbeans on 2010-01-28
The desktop PC I'm using for some reason doesn't like Ubuntu 9.04+ nor any derivative of it. If I run a live cd it will freeze completely if i even click on the menu. It's very strange and really annoying.

8.04 can run fine on a live cd and I was thinking about installing it. I was just curious if the repositories in synaptic for hardy were still updated frequently - like having mostly newest versions of free software.. gimp, k3b, etc...

thx in advance

---

### Post by mk1w86 on 2010-01-28
Ubuntu 8.04 is a long term support release and will be supported on the desktop until 2011, just don't expect the latest versions of software. :D

See here for information on LTS releases:

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

You might also find this useful:

[http://www.ubuntu.com/products/ubuntu/release-cycle%20](http://www.ubuntu.com/products/ubuntu/release-cycle%20)

---

### Post by snowpine on 2010-01-28
8.04=April 2008, so all of the applications are almost 2 years old. (They do receive regular security patches and bug fixes though.)

Have you tried the current release, 9.10?

---

### Post by somerefriedbeans on 2010-01-28
Yes i have actually and it freezes just the same.. I don't quite understand it. And I've actually been able to successfully install it but it would still freeze after booting up.

Fedora won't work for me either. Mandriva works fine but it's not my cup of tea. So, I've been using openSUSE.. and it has been great, but I've had some trouble with a lot of dependency issues with certain software. 

I ran ubuntu 9.04 on my laptop (before it broke) and it worked fine.

any ideas?

oh btw, maybe this would be helpful?
```
linux-ttc4:/home/bean # lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
02:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

```

---

### Post by snowpine on 2010-01-28
I have the identical chipset. :) I solved the freezing-shortly-after-login problem by disabling Compiz desktop effects.

```
metacity --replace
```

If that indeed solves the problem, you can re-enable Compiz safely with: 

```
compiz --replace --indirect-rendering
```

(edit) Like you, I have the same problem with Fedora 12, Arch, etc... it is not strictly an Ubuntu bug.

---

### Post by somerefriedbeans on 2010-01-29
ok, i'll have to try that. thank you very much :)

---

### Post by Iowan on 2010-01-29
> **somerefriedbeans said:**
>  I was just curious if the repositories in synaptic for hardy were still updated frequently8.04.4 is recently "released?". This Hardy machine has had several updates lately.

---

### Post by somerefriedbeans on 2010-01-29
> **Iowan said:**
> 8.04.4 is recently "released?". This Hardy machine has had several updates lately.

i was wondering if all of the software that shows up in the synaptic package manager is up to date... like firefox, gimp, or any other application you'd like to install.

---

### Post by snowpine on 2010-01-29
> **somerefriedbeans said:**
> i was wondering if all of the software that shows up in the synaptic package manager is up to date... like firefox, gimp, or any other application you'd like to install.

8.04 = April 2008. All applications in Hardy are stable versions roughly 2 years old (though they do receive security patches and bug fixes as necessary).

---

### Post by somerefriedbeans on 2010-01-29
> **snowpine said:**
> 8.04 = April 2008. All applications in Hardy are stable versions roughly 2 years old (though they do receive security patches and bug fixes as necessary).

i already heard ya, i was just further explaining to that other guy. thx though ;)

---

### Post by somerefriedbeans on 2010-01-29
> **snowpine said:**
> I have the identical chipset. :) I solved the freezing-shortly-after-login problem by disabling Compiz desktop effects.

```
metacity --replace
```If that indeed solves the problem, you can re-enable Compiz safely with: 

```
compiz --replace --indirect-rendering
```(edit) Like you, I have the same problem with Fedora 12, Arch, etc... it is not strictly an Ubuntu bug.


When I try this, I get:

```
bean@bean-desktop:~$ compiz --replace --indirect-rendering
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```compiz is lags really bad.. any way to fix this?

---

### Post by somerefriedbeans on 2010-01-29
bump

---

### Post by tom.swartz07 on 2010-01-30
> **somerefriedbeans said:**
> bump

You could just turn off the desktop effects? 

Just run 
```
metacity --replace
```
and enjoy a non-crashy computer :D



Unfortunately, it looks like your computer is unable to handle the graphics processing for compiz at all, so youre going to have to just leave it off...

If you do manage to upgrade the computer, though, you will certainly be able to play with compiz! Until then though- tough luck. :(

---

### Post by snowpine on 2010-01-30
+1; Compiz crashes on my identical hardware with Ubuntu, Arch, Fedora, etc. so it is not an Ubuntu issue. The easiest, foolproof solution is:

```
metacity --replace
```

---

### Post by somerefriedbeans on 2010-01-30
That's pretty gay. Compiz works perfect with openSUSE.

---

### Post by somerefriedbeans on 2010-01-30
so, there's no possible fix for this in ubuntu on this hardware..? it worked great on my suse 11.1 and 11.2

i just don't understand. could it be a driver issue? or maybe there is some kinda of mesa problem?

---

