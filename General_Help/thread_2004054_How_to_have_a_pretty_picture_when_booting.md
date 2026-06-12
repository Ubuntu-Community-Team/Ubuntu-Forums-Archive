---
title: "How to have a pretty picture when booting?"
date: 2012-06-15
forum: General Help
---

### Post by amanchesterman on 2012-06-15
I have Xubuntu 12.04 which runs perfectly on my laptop. Boot time is about 35 seconds. But during that time, before the Xubuntu login appears, the screen is plain black -- and it would be nice to have a picture to look at, or at least a different colour.

I have followed the instructions here [https://help.ubuntu.com/community/Grub2/Displays#Installing_Splash_Images  ]("https://help.ubuntu.com/community/Grub2/Displays#Installing_Splash_Images")- I followed the section for Grub 1.99 (the version on my machine) and used the splashimages for Grub2 downloaded via Synaptic. I have updated grub, and my grub.cfg file correctly identifies the image, which is located in the /boot/grub/ folder.

In other words I think I have done exactly what is needed in order to display an image for the Grub menu ... but still, when I start my laptop, no image appears. So I'm wondering if that is simply because the Grub menu itself doesn't appear? (I only have Xubuntu, and the default for a single OS is that the boot menu doesn't show.) Is there any way to show the image in Grub without having to show the menu? Or am I looking down the wrong road altogether in trying to do this with Grub?

Any helpful advice will be received gratefully!

Thanks

John
[]("https://help.ubuntu.com/community/Grub2/Displays#Installing_Splash_Images")

---

### Post by brainwash on 2012-06-15
Plymouth should provide a graphical boot screen while booting. More information here:

[https://wiki.ubuntu.com/Plymouth](https://wiki.ubuntu.com/Plymouth)

There could be a delay before the plymouth process starts or before it is able to display the boot screen. Forcing the use of the framebuffer might help in the second case:

[http://askubuntu.com/questions/79953/why-does-plymouth-start-so-late](http://askubuntu.com/questions/79953/why-does-plymouth-start-so-late)


Furthermore, please attach the output of following command:
```
cat /proc/cmdline
```

---

### Post by Jose Catre-Vandis on 2012-06-15
Open thunar as root
Browse to /usr/share/xfce4/backdrops (or something like that - sorry on W7 at work at the moment)
Find the "left" or "right" background image and copy it to /boot/grub/ (or pick whichever image you want)
Restart

You should have pretty picture......

Alternatively, install grub-customiser (see tutorials and tips) and do much the same via a GUI

---

### Post by amanchesterman on 2012-06-15
Thanks to you both for your replies. 

Jose, I copied the file like you said (and then updated grub) but it made no difference. It  replaced the reference to the grub splash image in the grub.cfg file with a new reference to the xfce4 image, but still no picture displays. As I said in my original post, I **think** that's because  the grub menu itself does not display when only one OS is installed.

Brainwash, I will look into using plymouth, from the information page it looks as if it might do the job. The output from cat /proc/cmdline is as follows:

```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-25-generic root=UUID=196697c0-0297-49e3-ab06-ffec7a8720ec ro quiet splash vt.handoff=7
```Thanks again

John

---

### Post by amanchesterman on 2012-06-15
A quick follow-up: I have just rebooted the machine, and this time I forced the grub menu to appear -- and yes, the image is there.

So the fact that it doesn't show for me 'normally' is simply because the grub menu doesn't normally appear. 

I'll have a go at installing plymouth and will mark this thread as solved.

John

---

### Post by MG&amp;TL on 2012-06-15
> **amanchesterman said:**
> A quick follow-up: I have just rebooted the machine, and this time I forced the grub menu to appear -- and yes, the image is there.

So the fact that it doesn't show for me 'normally' is simply because the grub menu doesn't normally appear. 

I'll have a go at installing plymouth and will mark this thread as solved.

John

Plymouth is (or should be, AFAIK) installed already. But it's evidently broken somehow.

---

### Post by Jose Catre-Vandis on 2012-06-15
Just install grub-customiser you can then "easily" set the grub menu to appear.

Plymouth should be installed already - it can be a bit of a b****r on some hardware though e.g. it has not worked properly on my PC since it was introduced until 12.04 came along ;)

---

