---
title: "Ubuntu will not pass Nvidia screen during boot up"
date: 2011-04-17
forum: General Help
---

### Post by neba on 2011-04-17
One day I turn on my laptop and everything is starting up normal I get to the screen that shows Ubuntu loading then it changes to Nvidia Bata screen then back to Ubuntu loading then back to Nvidia. It wont get past that part.

     I have looked on Google and and tried many things like:
-dpkg-reconfigure xserver-xorg, and sever different varies of it. I read that I should get another screen to pop up. Non of that happens and still the same problem.

-I tried to boot with the live ISO and 
  mkdir /mnt
  mount /dev/sda5 /mnt
  chroot /mnt
  dpkg-reconfigure xserver-xorg
  reboot
that didn't work either.

-I went into recovery > failsafe and it kicked me out back to the recovery mode menu.

-I tired to remove nvidia drivers

-I tired to reinstall nvidia drivers

I have been doing this for a while now. and help would be nice thank you
neba

---

### Post by pqwoerituytrueiwoq on 2011-04-17
have you tried disabling the nvidia boot screen logo?
by adding this under device
may look something like this
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "NoLogo"        "true" 
EndSection
```/etc/X11/xorg.conf is the file to edit

---

### Post by neba on 2011-04-17
Thank you for your reply.
this is all I found

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Geforce 310M" 
EndSection

I wasn't able to find this? 
    Option         "NoLogo"        "true"

---

### Post by pqwoerituytrueiwoq on 2011-04-17
i was saying to add the no logo to it
if the nvidia screen cause it to freeze disabling it should bypass it

---

### Post by neba on 2011-04-17
Thank you for your quick reply. I added it to the command line. during the startup I still get stuck at the same place. I get to Ubuntu loading then the screen goes black then back to ubuntu loading then black again. Then command line you gave me worked by taking off the nvidia logo, but it wont start up. Thanks you

---

### Post by pqwoerituytrueiwoq on 2011-04-18
edit boot in grub to not use the fancy boot screen so you can see an error message

---

### Post by lithopsian on 2011-04-18
> edit boot in grub to not use the fancy boot screen so you can see an error message
"nosplash"

Also remove "quiet"

---

### Post by neba on 2011-04-23
Thank you for your reply. this is what I did. I chose recovery > then start up normally that takes me to tty1. 
cd /boot/grub/ nano grub.cfg I didn't find what you said to edit. Is that the right file to edit? I know I have grub2 its in Ubuntu 10.10

---

### Post by DennyF on 2011-04-23
Neba - had same problem when I went to 11.04 Beta 2. Problem did not show up till then. So I booted in recovery mode, switched to generic VGA driver, low res, and re-installed the experimental driver offered for Nvidia. That worked. Two days ago, however, they (Nvidia) released the final version. I installed that (should be offered in the software center - if not, check Nvidia website or the Softpedia Linux website) and now, everything works great. Hope this helps ... den

---

### Post by neba on 2011-04-23
Thank you Den. I think that will fix this issue. Do you know how I can do that through the terminal? I only can get into tty1-6

---

### Post by DennyF on 2011-04-23
I'm not much of a terminal guy, but the procedure is on [http://linux.softpedia.com/](http://linux.softpedia.com/) . It's the lead story and it shows you the terminal commands and you can copy and paste them.

---

### Post by neba on 2011-04-24
Thank you, I need to play around with this. It is hard to follow their direction because I can't get into my desktop only the tty1. thank you for the link. I don't know if it is possible but I think if I can find a way to disable the nvidia driver and use the Ubuntu default driver then I can install the correct driver that you suggested. 
Thanks Neba

---

### Post by neba on 2011-04-24
I have a question? When Ubuntu 11.04 comes out do you think that if I upgrade then would that fix the problem or would it just make things worse?

---

### Post by neba on 2011-04-27
bump

---

### Post by neba on 2011-04-30
bump

---

### Post by neba on 2011-05-07
ok I fixed it. I did a network upgrade in the tty to Ubuntu 11.04

---

