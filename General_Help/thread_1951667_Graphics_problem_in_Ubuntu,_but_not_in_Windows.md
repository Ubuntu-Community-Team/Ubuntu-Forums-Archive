---
title: "Graphics problem in Ubuntu, but not in Windows"
date: 2012-04-02
forum: General Help
---

### Post by 300235 on 2012-04-02
Hello, I installed Ubuntu 11.04 after having Windows 7 on my HP Pavilion DV9000 laptop.
Right away there were problems, at the login screen the background image had a bunch of horizontal lines going across, but the windows would pop up. It loaded up, and the default desktop background was doing the same thing, so i switched the background to a solid color and it was alright. However, I opened up Firefox and sure enough the same lines appeared in patches on it. I rebooted, and instead of booting into the login screen, the horizontal lines appeared everywhere and i couldn't access anything. This appears to only be a problem on Linux, for I reinstalled Windows and the graphics are fine. Can anyone identify the problem? Thanks a ton for your time. Also, installing the nVidia drivers didn't help at all(that is when i could get into Ubuntu to install them). 

I attached an example of what the screen looks like when I boot Ubuntu.

---

### Post by 300235 on 2012-04-03
Any ideas?

---

### Post by wildmanne39 on 2012-04-03
Hi, post the output of:
```
lspci | grep VGA
```
Which driver did you install and from where?
Thanks

---

### Post by 300235 on 2012-04-03
> **wildmanne39 said:**
> Hi, post the output of:
```
lspci | grep VGA
```Which driver did you install and from where?
Thanks
I'm running Ubuntu 10.04 in a VM in Windows, if it's any consolation. It seems to be a graphic card problem. Ubuntu runs in a lower resolution in VirtualBox, so there were no lines. Anyway, here's the code: ```
00.02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
```I installed the drivers from Hardware Drivers, it was the most up to date nVidia graphics driver.

---

### Post by wildmanne39 on 2012-04-03
Hi, if you are running virtualbox you do not install the nvidia driver, you just install guest additions and under settings select display and enable 3d support then start your ubuntu but if you installed nvidia driver then you will have to remove it.
Thanks

---

### Post by UltimateCat on 2012-04-03
I have been researching for about 3 months now the topic" graphics card" and why they crash and or if it is indeed hardware failure.

What I found is that digging deep into the details of a particular graphics card and determining what type of memory a particular card uses is really difficult.

I learned that a graphics card has it's own BIO's and if you make changes in those BIO's and your not well educated in the process you can accidentally crash your graphics. (Onboard or Card in designated slot)
The BIO"s that communicate to your graphics card is different from your regular system BIO's.
You can test the memory by going to memtest- (fee) memtest86.com

If you have Windows up and running and all is well it is not hardware failure.(at least that was in my case) The same thing happened to me and what I found was the proprietary use was causing conflict with my Ubuntu so I uninstalled it. Also; it was the emulator that was associated with Grand Theft Auto.  As long as I do not play that game on my Windows side my graphic don't crash-

There is still a lot for me to read and learn.  If I learn a way to solve your graphics issue I will post more information as I am determine to help others in this group who have similar issues.

As an Artist graphics are extremely important to me and this is my pursuit-

Learning from a brand new book writtten by Scott Mueller; " Upgrading And Repairing PC's"  Also reading and studying other Linux Bible's and trying to find answers to difficult graphic questions.

Best Regards;)

---

### Post by QIII on 2012-04-03
Perhaps a bit of explanation is in order so you understand what wildmanne39 is saying:

In VirtualBox, you are not using the hardware on your machine directly.   The virtual machine is sitting on top of a hardware abstraction layer inside the VirtualBox space.

That InnoTek graphics adapter is abstract.  Its driver is contained in VirtualBox and is used by the virtual machine.  Your VM is not using your physical graphics card directly.  VirtualBox is brokering the communication between your guest, using the InnoTek adapter, and your host, using your physical graphics card.

That's what is meant by "virtual".

---

### Post by 300235 on 2012-04-04
> **wildmanne39 said:**
> Hi, if you are running virtualbox you do not install the nvidia driver, you just install guest additions and under settings select display and enable 3d support then start your ubuntu but if you installed nvidia driver then you will have to remove it.
Thanks
I'm using VirtualBox so I can get into Ubuntu right now, I had originally installed Ubuntu by itself and that's what I intend to do. I didn't install those drivers in VirtualBox, but rather when i had booted Ubuntu by itself.

---

### Post by wildmanne39 on 2012-04-04
Hi, you can try this it should reset the driver back to default like it was before you installed it.

Boot into recovery mode with networking and make sure networking is working then run these commands.
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```
Thanks

---

### Post by 300235 on 2012-04-04
> **wildmanne39 said:**
> Hi, you can try this it should reset the driver back to default like it was before you installed it.

Boot into recovery mode with networking and make sure networking is working then run these commands.
```
sudo rm /etc/X11/xorg.conf
``````
sudo dpkg-reconfigure xserver-xorg
```Thanks
Hello, good afternoon, the problem however is that the lines appear with or without the drivers installed. I'm thinking the resolution is too high for my laptop. Is there anyway to lower the resolution? Much appreciated.

---

### Post by wildmanne39 on 2012-04-04
Hi, I am not sure from the terminal.

Did you at least try what I mentioned?

Also you can try these nomodeset options in this link.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by 300235 on 2012-04-04
It looks like it is a faulty hardware problem and is not Linuxes fault. It worked in Windows for a bit but now it seems to have bled everywhere. I appreciate all the responses. Thank you!

---

### Post by wildmanne39 on 2012-04-04
Hi, I am sorry to hear that it is a hardware failure.

---

