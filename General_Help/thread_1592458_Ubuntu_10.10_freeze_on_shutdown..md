---
title: "Ubuntu 10.10 freeze on shutdown."
date: 2010-10-10
forum: General Help
---

### Post by odror on 2010-10-10
After upgrading one of my computers to 10.10 I experience freeze on shutdown

I understand that there are multiple things that can do that. Is there a way to Isolate the issue. It freezes during the ubuntu dots screen. The dots are still changing endlessly. So it is not complete freeze. The only way to intervene is by issuing a CTRL-ALT-DEL then the computer restarts.

Thanks

---

### Post by JackNocturne on 2010-10-10
Try next time when you shutdown press "Esc" key , this will show text splash and will enable you to see whats happening

---

### Post by odror on 2010-10-11
The last command before it freezes is:

**init: dbus main process (1182) killed by TERM signal**

Is there a way to know what is the next process in the termination that is holding the shutdown.

---

### Post by noeyx on 2010-10-12
I also encounter this freeze sometimes. What I do to remedy this is by pressing any keys such as Enter and Spacebar.

---

### Post by ami7878 on 2010-10-12
This might be related but although I don't have any issue with shutdown (I also upgraded to 10.10 from 10.04) but when I try to suspend the pc freezes and the system is halted with the display remaining on and single (non-blinking) cursor at the top left corner.

Nothing I do changes and the only thing I can do is to force power off.

:confused:

---

### Post by Ymurti on 2010-10-14
I am also having the same problem in my netbook. I upgraded from 10.04 to 10.10. Before upgrade Ubuntu worked wonderfully. Please help!

---

### Post by Alpha Axl on 2010-10-15
Same problem here, and it seems to freeze on a purple/pink screen as it shuts down.

---

### Post by azedddine on 2010-10-16
hello,

i have the same probleme, ubuntu is great, wonderfull, but won't shutdown

---

### Post by mklinux on 2010-10-20
The same for me on my netbook running Ubuntu 10.10 UNR, is there a fix for this? I updated this morning already...and still it's not working. I can manually force it to shut off but, bah! Any help out there?

---

### Post by eksivus on 2010-10-22
Folks I'm new to Linux,
 
I just installed it and am having the same problem.
I've found that those of us that are freezing at the desktop background shut downs and restarts is being caused by a bug where your netbook(or laptop) is trying to acces a usb port that it is not supposed to. It is causing the computer to stop and wait for a response from said usb port.
 
In my case the problem is the RT2800usb. 
 
I am running a netbook: an HP mini 1050.
 
I'm trying to find solutions as we speak. I've seen some things about a "blacklist" in the "command prompt" so that ubuntu will stop trying to access it.
 
 I'll report back to you all if I find anything.

---

### Post by ki4jgt on 2010-10-22
My dad has a problem like that. I believe it's because he disabled apic though. He has to press the power button to turn his computer off.

---

### Post by eksivus on 2010-10-22
more information on my system:
 
PCI Slots- Intel Corp 82801
USB Ports- Intel N10/ICH7

---

### Post by mklinux on 2010-10-23
Found this on another forum, seems like a good work around :)

Thanks to hariseldon122, your solution solved this annoying problem on my EEE 1001HA!

RePost of solution:
The RT3090 wireless was the problem. To fix it, you can install the DKMS kernel module package containing ralink’s proprietary source drivers. I just downloaded the prebuilt DKMS package on that page, I didn’t build it myself. Then I blacklisted the OSS ralink modules:

Appending to /etc/modprobe.d/blacklist.conf

# blacklist other Ralink modules in favour of 3090 DKMS mod
blacklist rt2860sta
blacklist rt2870sta
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb"

---

### Post by mklinux on 2010-10-23
Update: The previous solution didn't work...ugh...

---

### Post by mklinux on 2010-10-23
> **mklinux said:**
> Update: The previous solution didn't work...ugh...

Actually, I'm an idiot. I tried it again and it worked. Just edit out the " on the end. So this does work :)!!! &#50500;&#49912;!

# blacklist other Ralink modules in favour of 3090 DKMS mod
blacklist rt2860sta
blacklist rt2870sta
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb

---

### Post by eksivus on 2010-10-25
Hey hey hey, Yeah I actually figured this out the morning of 10/23 after a bit of research. All that stress for nothing! Easy fix.

Folks I don't know if it's true in all cases, but in mine, using an HP mini 1050, the command code was 

sudo nano /etc/module.d/blacklist 

then I appended: 

blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb

cheers!!:guitar:

---

### Post by elbergalarga on 2010-11-10
I'm testing this solution and I'll post whenever I confirm it works or not...thank you!

---

### Post by elbergalarga on 2010-11-11
It works....

thank you very much

---

### Post by rahul.pache on 2010-12-22
> **eksivus said:**
> Hey hey hey, Yeah I actually figured this out the morning of 10/23 after a bit of research. All that stress for nothing! Easy fix.

Folks I don't know if it's true in all cases, but in mine, using an HP mini 1050, the command code was 

sudo nano /etc/module.d/blacklist 

then I appended: 

blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb

cheers!!:guitar:
@[eksivus]("http://ubuntuforums.org/member.php?u=1173101")
/etc/module.d does not exists in my ubuntu.
I edited /etc/modprobe.d/blacklist.conf instead.

My OS freezes randomly so I wont find out if it work or not so easily, I'll wait hoping it wont happen again.
I surely will reply back if problem exists.

---

### Post by JC Cheloven on 2011-01-05
> **eksivus said:**
> Hey hey hey, Yeah I actually figured this out the morning of 10/23 after a bit of research. All that stress for nothing! Easy fix.
Folks I don't know if it's true in all cases, but in mine, using an HP mini 1050, the command code was 
sudo nano /etc/module.d/blacklist 
then I appended: 
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
cheers!!:guitar:
For those that may be interested:
This seems to work fine fine for an Asus eee netbook, which also freezed at shutdown with maverick. 
The file where to add these lines was /etc/modprobe.d/blacklist.conf
Thanks!

---

### Post by diegoviola on 2011-04-23
Are you guys using laptop-mode-tools by chance? we are having this same  issue on other distros like Arch Linux and I have found that disabling  laptop-mode-tools "fixes" the problem.

This problem is apparently a kernel problem, and the laptop-mode-tools  maintainer stated that it's a kernel problem as well, I have submitted a  bug report here: [https://bugzilla.kernel.org/show_bug.cgi?id=33872](https://bugzilla.kernel.org/show_bug.cgi?id=33872)

---

