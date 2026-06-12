---
title: "How can I recover my install?"
date: 2010-09-13
forum: General Help
---

### Post by Dustybug on 2010-09-13
Hi folks

I have a laptop on which I dual boot Ubuntu and Vista - Vista is quite simply only there for access to iTunes.

I was using Grub2 and have my hard drive partitioned so there is a Vista partition, partitions for Grub2 and Ubuntu and a joint partition where I keep my documents, music, etc, so they can be accessed easily from both OSs if required.

I tried to boot the other day and was met with a black screen with a window in the middle telling me that my Nvidia drivers were missing and that Ubuntu would run in low resolution graphics mode. There was an Ok button but I couldn't move the mouse to select it and the enter key, space bar, etc didn't work. In fact no key presses did anything.

In a moment of madness I ran the Vista repair utility and gave Vista control of booting things again over Grub2. My theory was that I would simply re-install Ubuntu in a week or so when I had time but now that I've had time to think about it this is the second time this has happened to me. I'd only just got Ubuntu set up the way I wanted it with my selection of software installed and configured to my liking. So here's my question...

Using the Ubuntu Live CD, how can I get my existing Ubuntu install back?

I assume I have to mount the partition where Ubuntu is, tell Ubuntu to use default video drivers and then give Grub2 its position back over Vista. Only problem is I don't know how to do that.

Can someone tell me how?

---

### Post by mike555 on 2010-09-13
If Windows messed up grub , you will need to reinstall grub (Ubuntu needs it to boot) .

---

### Post by Dustybug on 2010-09-13
Windows didn't mess it up - I told Windows to take control of the OS selection again until I could reinstall/fix Ubuntu.

I can probably reinstall Grub myself if I sit down and have a go at it but that wouldn't fix the main problem - the Nvidia one - would it?

---

### Post by garvinrick4 on 2010-09-13
Put cd in tray and boot off of it and choose Try Ubuntu.
I like labels on my partitions so here go's.
Open package call gparted and right click on Ubuntu install, go to label and lets say you label it lucid. And it is in sda5. Use your own, what ever they are sda1, sda2 sda5 whatever your Ubuntu linux install is. I am just using these for showing you. Ok you labeled it lucid and hit green arrow to apply it.
```
sudo mkdir /media/lucid
```
```
sudo mount /dev/sda5 /media/lucid
```
```
sudo grub-install --recheck --root-directory=/media/lucid /dev/sda
```
```
sudo umount /media/lucid
```

Reboot and go into Ubuntu install from grub selection and:
```
sudo update-grub
```

---

### Post by garvinrick4 on 2010-09-13
Google your nvidia driver problem and see if you get an answer to help you. Or go to the proper forum here and post your nvidia problem. When you need it fixed quick Google, google and more googling.

---

### Post by philinux on 2010-09-13
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

This will restore grub from the livecd.

---

### Post by Dustybug on 2010-09-13
Thanks for your replies - I now have Grub back but when I boot I am back to the error screen which I can't get passed. The only thing I can do is hold the power button to switch the laptop off.

Error screen photographed on my iphone and photo attached to this post.

What should I do now?

---

### Post by philinux on 2010-09-13
> **Dustybug said:**
> Thanks for your replies - I now have Grub back but when I boot I am back to the error screen which I can't get passed. The only thing I can do is hold the power button to switch the laptop off.

Error screen photographed on my iphone and photo attached to this post.

What should I do now?

At the grub menu use the down arrow key to select recovery mode.

Once you get the recovery menu choose command prompt with networking.

Then.

sudo apt-get update

then

sudo apt-get install nvidia-current

then

sudo reboot

---

### Post by Dustybug on 2010-09-13
Thank you VERY much people! I'm back in Ubuntu now :D

I've noted down the instructions to fix it if it happens for a third time but is there anything I can do to stop this happening to me? I mean in terms of OS/software tweaks rather than hardware replacements ;)

---

