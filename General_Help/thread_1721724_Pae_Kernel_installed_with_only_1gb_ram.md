---
title: "Pae Kernel installed with only 1gb ram"
date: 2011-04-04
forum: General Help
---

### Post by rowbird on 2011-04-04
Hi, Does anyone know why my Ubuntu install always loads the Pae Kernel?

---

### Post by wojox on 2011-04-04
Are you building off the Server version?

---

### Post by rowbird on 2011-04-04
Sorry, I am using 10.04.

---

### Post by rowbird on 2011-04-04
Here is a screenshot of my system monitor.

---

### Post by wojox on 2011-04-04
I've seen the Sever Edition come with PAE Kernels but not desktop. You didn't install the server edition and add the desktop?

Is it laggy or anything?

---

### Post by rowbird on 2011-04-04
I will double check the md5sums and post the result shortly, unless there is a command to check the version?

---

### Post by rowbird on 2011-04-04
Actually, it is SuperOS 10.04 32 bit and they only make a desktop version.

---

### Post by wojox on 2011-04-05
> **rowbird said:**
> Actually, it is SuperOS 10.04 32 bit and they only make a desktop version.

Check in the repo's and see if you can find a generic kernel to install then remove the PAE.

---

### Post by rowbird on 2011-04-05
I have tried that, but X would only start in low graphics mode. I have an Nvidia card.

---

### Post by wojox on 2011-04-06
> **rowbird said:**
> I have tried that, but X would only start in low graphics mode. I have an Nvidia card.

Did you try to reconfigure it? Is the driver activated? Run:

```
sudo nvidia-xconfig
```

```
gksudo nvidia-settings
```

---

### Post by rowbird on 2011-04-06
Thanks for the tip, I will give it a try later on today and let you know how I make out.

---

### Post by lithopsian on 2011-04-06
So you installed SuperOS and not Ubuntu?  I don't know if anyone here will be familiar with exactly which kernel it gives you.

If you only have 1GB memory then you ideally don't want either the PAE kernel or the default Ubuntu non-PAE kernel.  Both are configured to address more than 1GB of memory and it has a noticeable performance hit, but the only way around it is to compile your own kernel or find one that has this feature turned off.  On the other hand the PAE kernel won't hurt you and should perform more or less identically to the default Ubuntu one.

---

### Post by rowbird on 2011-04-06
[Solved] I fixed it with all of your help. Somehow PAE kernels got installed, and my machine was using them, but I also noticed that I had all the regular generic kernels listed in the grub boot list, so I booted into one of those and I came to the low graphics notification again, so I logged in, renamed my /etc/X11/xorg.conf file, and checked in System-Administration-Hardware Drivers, and It said that the recommended Nvidia driver was not installed, so I installed it. I then used Ubuntu Tweak to remove all the PAE kernels graphically. Now I'm rockin',Thanks Guys!

---

