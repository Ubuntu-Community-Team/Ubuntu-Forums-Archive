---
title: "Install 6111 nvidia driver on hoary"
date: 2005-02-13
forum: General Help
---

### Post by mediumcool on 2005-02-13
Hi there,

I have an mx4000 card which doesn't work with the latest nvidia driver. 

I have installed the patched 6111 driver to work with kernel 6.2.10 [patched driver](http://ngc891.blogdns.net/kernel/patches/NVIDIA-Linux-x86-1.0-6111-jp3.run).

After doing an /etc/init.d/gdm start imediately after installing the module, everything works as expected.

After restarting x or rebooting, i get an xorg error - Failed to initialize the NVIDIA kernel module!

I have tried adding nvidia to /etc/modules, but this leaves me with a blank screen and no access to other terminals.

Just out of curiosity, I installed fedora 3 on another partition and followed the instructions for installing the nvidia driver (kernel 6.2.10 same patched driver) and it worked fine.

The fedora instructions included the following step - 

cp -a /dev/nvidia* /etc/udev/devices
chown root.root /ect/udev/devices/nvidia*

This doesn't work with ubuntu

Any help greatly apreciated - I am pulling hair out over this!!!

Cya
Sean

---

### Post by Xian on 2005-02-14
Does this entry in the starter guide help: [Install Nvidia Driver](http://ubuntuguide.org/#installnvidiadriver)?

Do you have a file named "nvidia-kernel-nkc" located in /etc/modprobe.d/ that contains something like this:
```
alias char-major-195* nvidia
```

Is there a file named "nvidia-kernel-nkc" located in /etc/modutils/ that contains this entry:
```
alias char-major-195 nvidia
```

Is an entry similar to this listed in your /etc/modules.conf:
```
### update-modules: start processing /etc/modutils/nvidia-kernel-nkc
alias char-major-195 nvidia
```

And does your /etc/modules file have contents similar to this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a "#", and everything on the line after them are ignored.

sd_mod
psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp
nvidia
```

---

### Post by mediumcool on 2005-02-14
Hi Xian,


Thankyou very much for your suggestions.

The tut would have worked with warty, I took those steps when I had warty installed. The driver has been updated in hoary and the new one doesn't work with my card (nvidia splash screen stays on).

I had none of the listed files and entrys you suggested, so I made them myself. Unfortunately, I still get a blank screen   ](*,) 

I will keep trying (there has to be others in my situation that don't want to use warty's kernel).

Cya
Sean

---

### Post by fuflo on 2005-02-20
i have gf4mx and the same prob with 6629 nvidia.

so here's what i have done on archlinux:

after successfully instaling 6111 copy nvidia.ko from kernel modules to somewhere else. lets say /nvidia.ko
then [ in archlinux theres /etc/rc.d/rc.local, but i havent really found anything similar on ubuntu so..] you need to make/edit some bootscript and put some lines like these: 

rm /lib/modules/<your kernel version>/kernel/video/nvidia.ko
cp /nvidia.ko /lib/modules/<your kernel version>/kernel/video/

on archlinux this way works nicely. currently im trying to do the same on ubuntu.. will report when succesfull.. ;)

but i just wonder.. for 6111 you need kernel sources... how did you get them? from kernel.org? or maybe a ubuntu specific way.. plz tell me...

---

### Post by mediumcool on 2005-02-21
Hi fuflo,

I just got the kernel headers via apt-get:

sudo apt-get install linux-headers-`uname -r`

This gave me what I needed to build the nvidia module.

Look forward to reading about your results.

Cya,
Sean

---

### Post by fuflo on 2005-02-22
hm.. all i can find is 2.6.8 kernel headers.. installed it and nvidia still wants kernel source.. whateva.. im thinking to going back to archlinux ;) ubuntu is too much bloated i guess.. but you can still try to do this thing my way. when freshly compiled nvidia copy nvidia.ko from /lib/modules/...../ and put it somewhere else. then edit one boot script and put the lines i mentioned above..

btw if you dont really need 2.6.10, then you can use 2.6.8 with nvidia 6111 perfectly. currently im on that kind of setup here ;) when on 2.6.8, just force the version of nvidia to 6111 on synaptic and thats all..

---

### Post by mediumcool on 2005-02-23
Hi fuflo,

sudo apt-get install linux-headers-`uname -r` should give you the headers for whatever kernel you are using (ubuntu).  Doing this on my box allows me to build the patched module.

I am trying to work out why deleting and installing the module each boot helps; permissions?

Anyway, I came from arch, I wouldn't say ubuntu is bloated, but it is definately layed out differently to arch or slack.

Cya
Sean

---

### Post by fuflo on 2005-02-23
[QUOTE=mediumcool]Hi fuflo,

sudo apt-get install linux-headers-`uname -r` should give you the headers for whatever kernel you are using (ubuntu).  Doing this on my box allows me to build the patched module.

I am trying to work out why deleting and installing the module each boot helps; permissions?

Anyway, I came from arch, I wouldn't say ubuntu is bloated, but it is definately layed out differently to arch or slack.

Cya
Sean[/QUOTE]
 well i dunno.. it gave me 2,6,8 headers and i couldnt compile nvidia.. 

about the "I am trying to work out why deleting and installing the module each boot helps; permissions?"

hm.. all i thought when doing this was that nvidia.ko gets corrupted somehow.. i really dunno..

---

### Post by fuflo on 2005-02-25
hm.. well i forgot one line... here's my current rc.local in archlinux:

rmmod nvidia
cp /nvidia.ko /lib/modules/2.6.10-ARCH/kernel/drivers/video/
modprobe nvidia

i just need to do some tests with gdm and etc.. bacause im not sure if rc.local is executed before gdm starts.

---

### Post by mediumcool on 2005-02-25
Hi fuflo,

I installed arch on another drive and you've definately got it with your rc.local! I pulled out kdm from the deamens array and started kdm by hand (/etc/rc.d/kdm start) so rc.local loaded before kdm.

I just found this in google groups:

There is no "absence of rc.local" -- you just have to make it yourself. 
 
Just do the following: 
 
cd /etc/init.d 
 vi local 
 chmod +x local 
 update-rc.d local defaults 

will check it out and report back

Saen

---

### Post by mediumcool on 2005-02-26
well,

I created the local script and added fuflo's rc.local commands to it.  and it still doesn't work!!! 

Might have to join you in arch land for a bit fuflo, will keep ubuntu partition and keep at this though

Sean

---

### Post by mediumcool on 2005-03-18
All good now - new nvidia drivers work with old cards :-o

---

### Post by fuflo on 2005-03-19
yep.. they are.. maybe some day i ll install ubuntu again :)

---

