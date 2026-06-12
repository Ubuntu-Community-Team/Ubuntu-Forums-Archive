---
title: "Nvidia Bumblebee won't work"
date: 2012-07-10
forum: General Help
---

### Post by rI9^)wx! on 2012-07-10
Hello, I am experiencing a problem with my new Alienware M14x. I installed Ubuntu and Bumblebee, but when i run optirun glxspheres, it returns the error "[ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please". I don't want my Nvidia GPU to become an expensive paperweight, please help!
Specs:
Alienware M14x R2
Nvidia Geforce GT650M
12GB of RAM
Intel Core i7-3610QM

---

### Post by SavageCHRIS on 2012-07-10
What version of Ubuntu are you using ? and how did you install Bumblebee ?

---

### Post by rI9^)wx! on 2012-07-11
I'm using the latest version of Ubuntu (12.04) and I installed it by adding the Bumblebee PPA, then installing the correct packages (I just followed the instructions on the Ubuntu Wiki). Is there anything else you need to know?

---

### Post by rI9^)wx! on 2012-07-12
Can anyone please help? I _***really***_ want this to work!

---

### Post by defcronyke on 2012-08-01
Hey darkness3560,

I've worked out a recipe for getting the Optimus GT650M working with bumblebee and the NVidia proprietary driver, check it out here: [http://eternalvoid.net/tutorials/linux-optimus-gt650m/](http://eternalvoid.net/tutorials/linux-optimus-gt650m/)

I don't promise anything, but it worked for me, and I already have a report of it working for someone else.

The short of it is, until bumblebee 3.0.1 and nvidia-current 304.22b are in an Ubuntu repository, you'll probably have to follow a procedure similar to my recipe to get your GT650M working. The recipe explains how to install the NVidia drivers in a non-standard location, without removing all your original OpenGL stuff. It goes on to explain how to install a newer version of Bumblebee from git, and how to set it up to be able to find all the NVidia libraries, but also to use an Intel driver to access the framebuffer.

Full instructions are at the link I provided, I hope it works for you. There's no point in having an awesome discrete card if you can't even use it!

---

### Post by Liametc on 2012-09-17
**omg I love you so much**. Worked first time :D

Just for other people that may have run into this issue, where you have to do this
> sudo cp -a /emul/ia32-linux/usr/lib/* /usr/nvidia/lib32

if you cannot find **/emul/ia32-linux/usr/lib/**, copy **/usr/lib32** instead. Worked for me

---

### Post by Liametc on 2012-09-17
ARGH! I've managed to ruin it all! Tried to sort out some sound through the hdmi and followed [these instructions]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")

used "additional drivers" to install the new drivers and it all gone. No optimus, no cinnamon.

HELP![-o<

---

### Post by defcronyke on 2012-09-17
> **Liametc said:**
> ARGH! I've managed to ruin it all! Tried to sort out some sound through the hdmi and followed [these instructions]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")

used "additional drivers" to install the new drivers and it all gone. No optimus, no cinnamon.

HELP![-o<

It would be the first part of "Procedure Ae - (Make NVIDIA HDMI Audio work)" from that HDMI tutorial that broke your Optimus support. You'll probably have to start over with a fresh install of your operating system. After reinstalling the OS, get Optimus working using my tutorial first, then try the other tutorial, but skip over the first part of Procedure Ae (and start at the part that says: "Run in a Terminal window: aplay -l") since you will already have the Nvidia drivers installed (in a different way) after following my tutorial. I haven't tried the other tutorial, so I don't know if it will work for you or not, but good luck!

---

### Post by Liametc on 2012-09-18
Thanks for the speedy reply. I had come to the conclusion that I would need to do a fresh install, but now I definitely know. O well, so close.](*,)

---

