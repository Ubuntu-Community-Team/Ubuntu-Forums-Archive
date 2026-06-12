---
title: "Screen Resolution Problems"
date: 2009-07-14
forum: General Help
---

### Post by iamjava on 2009-07-14
I downloaded the current version today for Ubuntu and loaded it onto a disk. I then went to the boot menu and ran Ubuntu off of the disk and selected "run without making any changes to your current configuration" to try out Ubuntu. The problem occurred when I got to the desk top. My monitor began displaing "resolution out of range, please try changing it to 1024x768", which is the highest resolution it has. I tried doing it, but it turns out that was the resolution it was at according to Ubuntu. Even worse, it wouldn't go any lower than that.

Anyone got a solution?

---

### Post by kogger on 2009-07-14
What resolution does your computer normally use?

---

### Post by iamjava on 2009-07-14
> **kogger said:**
> What resolution does your computer normally use?

1024x768

Edit: This is my first time ever using Ubuntu and it is running off the DVD I have. I did a disk check before I actually ran Ubuntu and it said there was only one error, if it helps.

---

### Post by kogger on 2009-07-14
Go to System->Administration->Hardware Drivers and see if your graphics driver is activated. If it's not, activate it; if it is, try re-installing it.

---

### Post by iamjava on 2009-07-14
> **kogger said:**
> Go to System->Administration->Hardware Drivers and see if your graphics driver is activated. If it's not, activate it; if it is, try re-installing it.

When I went to activate it, it gave me one loading-type screen, then a box with a red octagon in it. with no text. How do I reinstall a graphics card??

---

### Post by kogger on 2009-07-14
What kind do you have? ATI or Nvidia? (or something else?)

---

### Post by iamjava on 2009-07-14
> **kogger said:**
> What kind do you have? ATI or Nvidia? (or something else?)

Nvidia 2800 or something around there. (I know it's really old and crappy.)

---

### Post by iamjava on 2009-07-14
My friend who knows a little about Ubuntu told me to do ctrl+alt+f3, and it took me to a command prompt type screen. He says:

> [COLOR=#000000]from there you need to change the refresh rate, i have no idea how lol[/COLOR]

I sure as hell don't know how. >_>

---

### Post by kogger on 2009-07-14
Try this. Type this into a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

And then reboot. Not sure if it'll work, but it's worth a shot.

---

### Post by iamjava on 2009-07-14
> **kogger said:**
> Try this. Type this into a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```And then reboot. Not sure if it'll work, but it's worth a shot.

I did that, but it's now taking me through this whole configuration which I don't quite understand. I tell it to do it automatically and it still does it manually.. Also, how do I exit out of the configuration screen?

---

### Post by kogger on 2009-07-14
Honestly, I'm not entirely sure. And it's not the card you're trying to re-install, just the driver. You can also try purging it from your system (sudo apt-get remove --purge nvidia-*) and re-installing it, but I'm not sure how you would go about that off the top of my head.

---

### Post by iamjava on 2009-07-14
> **kogger said:**
> Honestly, I'm not entirely sure. And it's not the card you're trying to re-install, just the driver. You can also try purging it from your system (sudo apt-get remove --purge nvidia-*) and re-installing it, but I'm not sure how you would go about that off the top of my head.

I inserted a different hard drive with Vista on it and tried installing Ubuntu onto it, but I got an error. Might it just be a problem with the OS itself? 

Also, when I went to activate the driver or whatever, it said that it was not compatible or something.

---

### Post by kogger on 2009-07-14
You may have gotten a faulty disc, but besides that there shouldn't be any problem with the os itself.

---

