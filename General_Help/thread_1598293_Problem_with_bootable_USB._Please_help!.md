---
title: "Problem with bootable USB. Please help!"
date: 2010-10-16
forum: General Help
---

### Post by cheesewake on 2010-10-16
Hi I am a beginner to Linux and I am having some trouble installing ubuntu with my usb drive. I used
 unetbootin to make the iso image to the usb. When I restart and run from the usb it opens ubuntu in a terminal form. How do I install using the proper commands. I do not receive a graphical interface. Just a low run level. Does this make sense?

Also, another reason I am swithching from Linux Mint to Ubuntu is so I can install my ATI radeon HD drivers. I cannot get them to work in Linux Mint. I hope it works. Unless there is another distro I can use that is compatible with the ATI Catalyst Drivers. 

Thanks,
Chris Hawkins
[www.gzmweb.com]("http://www.gzmweb.com")

---

### Post by tcpa41 on 2010-10-16
did you try?
sudo service gdm start

---

### Post by cheesewake on 2010-10-16
Nothin...

---

### Post by gnush on 2010-10-16
If anything goes wrong I think you often end up with a quite minimal bash terminal, I don't really remember what it's called.
Can you write exactly what it says?

Also, to start the graphical environment the following command might work.

> startx

---

### Post by cheesewake on 2010-10-16
It is a simple bash terminal they seem to be different commands. Somehow I need to execute the OS.  Normal termial commands do not work in bash . I tried startx also with no success...

---

### Post by inso_741 on 2010-10-16
is it a shell prompt or are u stuck at grub/syslinux prompt??

---

### Post by cheesewake on 2010-10-16
Its a shell prompt.

---

### Post by inso_741 on 2010-10-16
try creating live usb using the usb-creator that came inside the iso

---

### Post by cheesewake on 2010-10-16
Inside the ISO?

---

### Post by inso_741 on 2010-10-17
> **cheesewake said:**
> Inside the ISO?
yes mount the ISO(assuming you downloaded the iso from ubuntu.com)
there will be a tool call "usb creator" its for windows and works better than unetbootin(has the option for persistance)

---

