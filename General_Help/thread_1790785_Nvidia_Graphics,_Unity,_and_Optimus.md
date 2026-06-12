---
title: "Nvidia Graphics, Unity, and Optimus"
date: 2011-06-25
forum: General Help
---

### Post by [::AP::] on 2011-06-25
Hello all -

I just installed 11.04 on my new laptop. The Laptop is the Lenovo Ideapad y470. (085523U)

 * Intel i5-2410M (Sandy Bridge [2nd Gen])
 * Intel HD Graphics 3000 (Integrated)
 * Nvidia GT GeForce 550m (Graphics Card)

There is Nvidia Optimus technology.

Three questions
1. How to I get Ubuntu to use the Nvidia?
2. How to I get Unity to run (I probably won't like it, but I will give it a shot)?
3. How do I know if I installed Bumblebee correctly?
(Bumblebee = (in short) Optimus for Linux)

At first boot, it displays the message
"...this computer does not have the hardware to run Unity..."
(Something along those lines)
I am pretty sure I do :) Nice graphics card and processor. 

Therefore, I do not have Unity running. 
Second, I cannot seem to run any compiz effects. 

Here is a screen shot of System > Administration > Additional Drivers.
To the left is the latest Nvidia driver from their website.

[[IMG]http://img863.imageshack.us/img863/1139/screenshotty.png[/IMG]](http://img863.imageshack.us/i/screenshotty.png/)

Uploaded with [ImageShack.us](http://imageshack.us)
[http://img863.imageshack.us/img863/1139/screenshotty.png](http://img863.imageshack.us/img863/1139/screenshotty.png)

I have been using Ubuntu since 9.10 and up, but I am totally lost here. I would still consider myself a noob. Help me out here. 

Thanks, 

[::AP::]

---

### Post by [::AP::] on 2011-06-25
I think the problem is that it is "not currently in use"?

---

### Post by 11ghjones on 2011-06-25
Do you have nouveau blacklisted in any of the conf files in /etc/modprobe.d/ ?

---

### Post by grahammechanical on 2011-06-25
Ignore the message that says No proprietary drivers are in use on this system. Also ignore the message that says this driver is activated but not currently in use. A lot of us are of the opinion that these messages are incorrect.

I have the same messages but the Nvidia X Server Settings utility is telling me that I am using Nvidia driver version 270.41.06. This was installed through Additional Drivers.

If you intend to install that 275.09.07 driver then make sure that you deactivate the driver currently activated before you install the new one.

But before you do that try clicking on your user name at log in and on the bottom panel on the right will be a menu. If you have Ubuntu in the list, then select it and the desktop that will load will be the Ubuntu Unity desktop. If you do not like it, simply choose Ubuntu Classic from that list. Do not try to remove Unity once it is loaded. You will end up with a non-functional desktop.

To use compiz you need to install CompizConfigSettings Manager (CCSM) through the Software centre. It will be located in the System Settings. Tick the Ubuntu Unity Plugin to get access to a few adjustments to Unity. Be careful what compiz effects you activate. Some of them clash with Unity and you will lose the top panel. It gets hidden. The clickable areas are still there to click. You have to de-activate the enhanced effect and reboot to get the top panel back.

It will be welcome news if there is a Nvidia driver that allows the Optimus technology to be used with Linux.

Regards.

---

### Post by [::AP::] on 2011-06-25
> **11ghjones said:**
> Do you have nouveau blacklisted in any of the conf files in /etc/modprobe.d/ ?

Yes - under 
*/etc/modprobe.d/nvidia-graphics-drivers.conf*
The first line states
```
blacklist nouveau
```

I imagine this is fixed by removing this line? (as superuser)

---

### Post by mmsmc on 2011-06-25
nvidia with optimus does not currently work too well with ubuntu, especially that graphics card. there is a hybrid driver being worked on though

---

### Post by [::AP::] on 2011-06-25
> **mmsmc said:**
> nvidia with optimus does not currently work too well with ubuntu, especially that graphics card. there is a hybrid driver being worked on though

> **grahammechanical said:**
> 

But before you do that try clicking on your user name at log in and on the bottom panel on the right will be a menu. If you have Ubuntu in the list, then select it and the desktop that will load will be the Ubuntu Unity desktop. If you do not like it, simply choose Ubuntu Classic from that list. Do not try to remove Unity once it is loaded. You will end up with a non-functional desktop.

To use compiz you need to install CompizConfigSettings Manager (CCSM) through the Software centre. It will be located in the System Settings. Tick the Ubuntu Unity Plugin to get access to a few adjustments to Unity. Be careful what compiz effects you activate. Some of them clash with Unity and you will lose the top panel. It gets hidden. The clickable areas are still there to click. You have to de-activate the enhanced effect and reboot to get the top panel back.

It will be welcome news if there is a Nvidia driver that allows the Optimus technology to be used with Linux.

Regards.

Thank you for the response. *However,* I am not a **total noob** and knew this. ;) (I should have made that clearer.) Thank you though.

Optimus? Linux is getting close! Check out the Bumblebee project. 
[http://www.omgubuntu.co.uk/tag/bumblebee/](http://www.omgubuntu.co.uk/tag/bumblebee/)

---

### Post by [::AP::] on 2011-06-27
I have been travelling the past couple days - have not had a chance to address the problems. I may attempt a fix tomorrow, depending on internet access. 

Thanks, I will let you know. 

[::AP::]

---

### Post by Jack` on 2011-08-03
I am assuming you have installed the ppa, and run the commands to install and configure bumblebee.

To see if bumblebee is working, enter the following command into a terminal:
```
optirun glxgears
```
or
```
optirun glxspheres
```
That should display a few lines of text (or it might skip that part, but unlikely if you are not using unity), and then display either a set of gears or spheres in a new window, which when closed, will display a few more lines of text.
If it comes up with optirun not being a valid command, then bumblebee is not installed.
If it produces errors, typically lots of lines of text, then it is not configured.
Try running
```
sudo bumblebee-configuration
```
to see if it will fix the configuration file.
Also, even if it is configured, you might not be able to easily run unity. Luckily for me, my laptop already had scripts for automatic switching, without that, you need to start programs with optirun to use the nVidia card.
Personally, I think nVidia should be shot for their horrible work.

---

