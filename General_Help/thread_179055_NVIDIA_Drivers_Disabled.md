---
title: "NVIDIA Drivers Disabled"
date: 2006-05-18
forum: General Help
---

### Post by Dark Elitist on 2006-05-18
Hello Ubuntu Community!

My friend and I are totally new to Linux and so far love Ubuntu very much. Any help that we can get would be greatly appreciated!

Apparently, there is a bug with Breezy 5.10 and the NVIDIA drivers with memory leaking, according to the official Wiki for NVIDIA driver installation located at [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29") and it is easily fixable.

My friend has been playing ET and enjoying Ubuntu a ton but today, after one hour of gameplay, began to experience the memory leaking and had to close ET and reboot due to intense FPS drop and lag. The fix on the Wiki says to edit /etc/X11/xorg.conf and add to it: Option "RenderAccel" "false".

We did that, rebooted the computer, and the NVIDIA logo that displays to notify the user that the drivers are fully operational was no longer showing up. We tried reversing what we had just done, rebooted, and still... no NVIDIA logo. 

The NoLogo Option does not exist so apparently, the drivers are no longer functional.

We have totally reversed what we did but the logo still isn't coming back and we already know what will happen if we run Enemy Territory and the drivers aren't enabled - instant lockup.

Should we run sudo nvidia-glx-config enable again? Will that fix the problem?

Thank you Ubuntu community!

---

### Post by louis_nichols on 2006-05-19
Did you by any chance make a kernel upgrade too? Because that might have disabled the nvidia drivers if the kernel restricted modules package isn't out yet. This is the case right at this moment with dapper and kernel 2.6.15-23.

If this is indeed the case, the temporary solution is to boot an older kernel from the grub menu. Once the restricted modules package comes out, you just upgrade it aswell and will make this problem go away by itself. Then you can boot the new kernel again.

The modification in xorg.conf that you've made can't have caused all that trouble. It might be something else than what I wrote, but this is my initial guess.

---

### Post by Dark Elitist on 2006-05-19
Nope. All we did was added the above mentioned option to xorg and rebooted to find that the NVIDIA logo, which had been displayed up until this change, was gone. We then reverted our simple one line addition to xorg by totally removing it, rebooted, and the logo is still gone, even though we put things back just how they were. We have no automatic updates enabled, just notification.

[QUOTE=louis_nichols]Did you by any chance make a kernel upgrade too? Because that might have disabled the nvidia drivers if the kernel restricted modules package isn't out yet. This is the case right at this moment with dapper and kernel 2.6.15-23.

If this is indeed the case, the temporary solution is to boot an older kernel from the grub menu. Once the restricted modules package comes out, you just upgrade it aswell and will make this problem go away by itself. Then you can boot the new kernel again.

The modification in xorg.conf that you've made can't have caused all that trouble. It might be something else than what I wrote, but this is my initial guess.[/QUOTE]

---

### Post by dg_w on 2006-05-19
Yep that should do it 

Just to make sure :) 

From a console (logout of gnome , then CRTL+ALT+F2)

sudo apt-get update
sudo apt-get dist-upgrade

reboot, then back at console

sudo apt-get install -reinstall nvidia-glx nvidia-kernel-common

make sure that you are using the "nvidia" driver in /etc/X11/xorg.conf 
 
Rebbot and that should be it :)

---

### Post by Dark Elitist on 2006-05-19
A few questions below and thank you so much for your reply!

[QUOTE=dg_w]Yep that should do it 

Just to make sure :) 

From a console (logout of gnome , then CRTL+ALT+F2)

sudo apt-get update
sudo apt-get dist-upgrade[/QUOTE]

I know what sudo apt-get update does as we have everything updated and upgraded already but won't dist-upgrade send us to Dapper and cause lots of other problems? We are on 5.10 right now and upgrade has no findings. What would dist-upgrade do differently?

[QUOTE=dg_w]reboot, then back at console

sudo apt-get install -reinstall nvidia-glx nvidia-kernel-common

make sure that you are using the "nvidia" driver in /etc/X11/xorg.conf 
 
Rebbot and that should be it :)[/QUOTE]

What is nvidia-kernel-common? I don't remember ever installing that before or seeing it in the Wiki instructions for NVIDIA driver installation. Yes, it still says "nvidia" in /etc/X11/xorg.conf where it is supposed to.

Supposing this fixes everything, the question becomes how to the initial problem mentioned in my first post; how does one fix the severe memory leaking or is a new version of the driver due to be released soon?

Thank you Ubuntu community! If we can get this fixed, there is a good chance I will also migrate over from Windows. Ubuntu looks very promising. :-D

---

### Post by Dark Elitist on 2006-05-19
Bump! Help please you L337 peoples! ](*,)

---

### Post by Dark Elitist on 2006-05-19
Anybody at all? :confused:

---

### Post by tseliot on 2006-05-20
Try my script and see if anything changes (choose the one for Breezy if you're using Breezy):
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by Dark Elitist on 2006-05-20
[QUOTE=tseliot]Try my script and see if anything changes (choose the one for Breezy if you're using Breezy):
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")[/QUOTE]

Thank you very much.

When my friend comes around, we will try it but I have a question:

What are the chances that this will totally hose, break, and crash the system and how do we know that our kernel is compatible? We have ran apt-get upgrade and stuff so we may have a really new kernel off one of the repositories.

Also, has the memory leaking been fixed in 8756?

---

### Post by tseliot on 2006-05-20
[QUOTE=Dark Elitist]Thank you very much.

When my friend comes around, we will try it but I have a question:

What are the chances that this will totally hose, break, and crash the system and how do we know that our kernel is compatible? We have ran apt-get upgrade and stuff so we may have a really new kernel off one of the repositories.[/QUOTE]
Whatever version your kernel is, my script will install the nvidia driver using the installer from Nvidia's website (as long as your internet connection is working).

I don't know why it should totally break your system. If it doesn't work you can choose the "uninstall" function in my script.

Only a warning: it will remove the restricted modules and if you use a wireless card you won't be able to use it any more (unless you reinstall the restricted modules).

[QUOTE=Dark Elitist]Also, has the memory leaking been fixed in 8756?[/QUOTE]
I really don't know but I suppose it's worth trying

---

### Post by Dark Elitist on 2006-05-20
[QUOTE=tseliot]Whatever version your kernel is, my script will install the nvidia driver using the installer from Nvidia's website (as long as your internet connection is working).

I don't know why it should totally break your system. If it doesn't work you can choose the "uninstall" function in my script.

Only a warning: it will remove the restricted modules and if you use a wireless card you won't be able to use it any more (unless you reinstall the restricted modules).


I really don't know but I suppose it's worth trying[/QUOTE]

Alright. Thank you so much for your help so far.

He does use Wireless so we need the restricted modules. I don't suppose you could provide me instructions how to edit your script so that it doesn't touch the restricted modules?

Also, how will we know your script worked? Will a NVIDIA logo show up on boot?

Thank you so much!

---

