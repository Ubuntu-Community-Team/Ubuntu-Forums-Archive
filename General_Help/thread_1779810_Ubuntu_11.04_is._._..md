---
title: "Ubuntu 11.04 is. . ."
date: 2011-06-11
forum: General Help
---

### Post by Dobly on 2011-06-11
.. broken!

I got 11.04 installed on my laptop a few weeks ago and all seemed well. 

I've only used this machine for general surfing and downloads (legal of course )

Anyway, last night it started to display some odd or should I say, show stopping issues. 

Issue 1. Clicking the Home Folder button at the top of the left launcher does nothing. Well when I say nothing is does dim the icon, the hard drive turns but no folder opens. OS function 101 failure. 

Issue 2. Inserting a USB stick (that just last week we working fine) does nothing. Again, when I say nothing, the harddrive light goes on, but the USB drive does not open. 

Issue 3. Unable to get my home folder open in the Ubuntu 11.04 Unity system I downloaded Sunflower, a file browser app. It runs fine from the command line, but when the I decided to make a shortcut to this on the desktop, I right clicked on the desktop in order to use the Create Launcher option. But guess what? The right click does not reveal any menu. Right clicking on the desktop does nothing. 

This is not good enough for what is suppose to be a mature stable OS!

<steps of soapbox>


Ok, I've vented enough. I really do not want to go to Fedora 15 or <shudder> Windows 7 so, how do I fix this broken system? Is there some system repair that reinstalls the OS or something? Is there a system repair that does not require me getting all the updates again?

---

### Post by linuxinstalledfromhdd on 2011-06-11
Have you run Disk Utility to check the Disk STATUS of your HDD? Is it good/bad? I had plenty of issues with 11.04, and I am a long time linux user.  Right now I am currently back running 10.10, and everything is perfect.  What I would suggest trying is this, before going to Fedora or something else entirely... 

Download 10.10. Install it to a USB Flash Drive. Boot from that Flash Drive. And test out the system. See how it performs.  If you notice that it runs smoother, better, etc.  Then install it.  Here is a guide to get everything up and running that you will want after you have that installed:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

With the guide it really should be a piece of cake after that.  :)

---

### Post by NetDoc on 2011-06-11
> **Dobly said:**
>  and all seemed well.  One would think, and I am one, that if the system worked alright in the beginning and opening the drive became deprecated that you may have an issue with the drive itself. While uncommonly rare in current drives, bad spots (sectors) were quite common on the hard drives of yesteryear. This seems more likely if loading from your USB drive produces the same lame results. Dobly had a great suggestion about using a 10.x install to check it, but be ready for a faulty drive.

---

### Post by Dobly on 2011-06-11
NetDoc

It was linuxinstalledfromhdd who suggested the USB test.. I got the meaning of that anyway thanks. 

The HD idea is quite possible. It's about 3 years old now. I'm very keen to test it out. 

Is it hard to install 10.10 to a USB stick? Never done that.  I suppose I could just download the ISO and book from a cd? That would be the same effect no? Would that let me see the internal HD? 

Is there some sort of HD test in 11.04? Something like what I would call scandisk or chkdisk in Windows? I'd like to run that first.

---

### Post by wildmanne39 on 2011-06-11
> **Dobly said:**
> NetDoc

It was linuxinstalledfromhdd who suggested the USB test.. I got the meaning of that anyway thanks. 

The HD idea is quite possible. It's about 3 years old now. I'm very keen to test it out. 

Is it hard to install 10.10 to a USB stick? Never done that.  I suppose I could just download the ISO and book from a cd? That would be the same effect no? Would that let me see the internal HD? 

Is there some sort of HD test in 11.04? Something like what I would call scandisk or chkdisk in Windows? I'd like to run that first.
Hi, yes you can use a livecd it needs to be the same version as the ubuntu you are using.
YOu put this command in a terminal to run a desk check.
```
sudo badblocks /dev/sda
```sda or  whatever your drive is named.

---

### Post by 3rdalbum on 2011-06-11
I think all three functions you're having trouble with are related to the Nautilus file manager.

What happens if you open a terminal and try to type "nautilus" into it? Do you get some error messages appearing in the terminal?

The last time Nautilus failed to start for me was when I played around with RGBA semitransparent windows, which Nautilus was not compatible with. Is this something you're experimenting with now?

If not, then does the Gnome failsafe mode work?

If it takes a while to get the Nautilus issue sorted out, then run Sunflower from the terminal as you have been doing, and then go to the Unity launcher on the left side of your screen and right-click the Sunflower icon and choose "Keep In Launcher". Then you'll be able to run the file browser easily.

---

### Post by Dobly on 2011-06-11
First up I ran 'sudo badblocks /dev/sda'

It ran (in typical annoying old school unix style) with no informative text output of what is is doing or what it is up to). It ran for about 20 minutes and just finished. Nothing reported to the screen. Should I assume there is no error or is the output of badblocks in some cryptic 'you gotta know' file somewhere on the hd?

As for nautilus: When I type that in a terminal I get this error.... 


"GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported"

WTF is this? Could this be my problem? What on earth is this error?

---

### Post by wildmanne39 on 2011-06-11
> **Dobly said:**
> First up I ran 'sudo badblocks /dev/sda'

It ran (in typical annoying old school unix style) with no informative text output of what is is doing or what it is up to). It ran for about 20 minutes and just finished. Nothing reported to the screen. Should I assume there is no error or is the output of badblocks in some cryptic 'you gotta know' file somewhere on the hd?

As for nautilus: When I type that in a terminal I get this error.... 


"GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported"

WTF is this? Could this be my problem? What on earth is this error?
Hi,GTK+3 is the it is going to replace GTK+2 but I do not think it is suppose to be available til the next release unless you have your system set to update the bleeding edge, or did you install gnome3? If it is an update I would go to synaptic and remove all instances of it, but if you installed gnome3 it has to have it and it should have gotten rid of GTK+2.

---

### Post by VOT Productions on 2011-06-11
Have you updated your system recently?

---

### Post by Dobly on 2011-06-11
I update the PC every time it asks. Is that correct or should I manually run the update process?

As for GTK+3 I DID try to install Gnome 3 in a moment of hating the new Unity launcher and only got part way into the Gnome 3 install (not sure exactly what I did). Then I discovered the classic view from the login screen and did didn't bother with Gnome 3. 

Assuming this installed GTK+3, what is the command to remove it? I looked in synaptic and filtering by 'GTK' and spotted 'gtk-3-examples' 'and gir1.2-gtk-3.0'. Are these the things to uninstall? And from the look of synaptic GTK-2 is gone. What would be the process to uninstall 3 and reinstalling 2? Would installing 2 write over the 3 install the same way that 3 wrote itself over 2? ie: do I just need to install GTK 2 to fix this issue?

---

### Post by linuxinstalledfromhdd on 2011-06-11
Yes, you should run update/upgrades manually from time to time.

sudo apt-get update
sudo apt-get upgrade

Use those frequently as you wish from your terminal...

As for your other attempt to fix your probelm with Unity, click on top left corner of Unity. Type in the search box for Login.  Unlock. And select from the dropdown menu Ubuntu Classic. And exit to  save. Reboot to make sure the changes have taken effect.

You know what would be perfect for a user in your situation? 

This:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Take your time with it. :)

And if you are going to mess with Gnome 3 again make sure to backup your data.

---

### Post by wildmanne39 on 2011-06-11
> **Dobly said:**
> I update the PC every time it asks. Is that correct or should I manually run the update process?

As for GTK+3 I DID try to install Gnome 3 in a moment of hating the new Unity launcher and only got part way into the Gnome 3 install (not sure exactly what I did). Then I discovered the classic view from the login screen and did didn't bother with Gnome 3. 

Assuming this installed GTK+3, what is the command to remove it? I looked in synaptic and filtering by 'GTK' and spotted 'gtk-3-examples' 'and gir1.2-gtk-3.0'. Are these the things to uninstall? And from the look of synaptic GTK-2 is gone. What would be the process to uninstall 3 and reinstalling 2? Would installing 2 write over the 3 install the same way that 3 wrote itself over 2? ie: do I just need to install GTK 2 to fix this issue?Hi, for the most part people say if you have tried gnome3 and you want to remove it you have to reinstall ubuntu. I have found one person that says he removed gnome3 and got unity working again with out a reinstall, I recommend a reinstall, but I will give the instructions he used just in case you want to try but beware it might not work. I could not find the instructions for removing gnome3,I only found the instructions for installing, you can do a search for uninstalling gnome3 in the forums and you might find it, but reinstall is still the best option,but with all the changes you have made I would back up files that you want to keep and do a clean install, do not keep anything that will have settings from this install.

---

### Post by Dobly on 2011-06-12
>>click on top left corner of Unity. Type in the search box for Login. Unlock.

Sounds good, but clicking the Unlock button does nothing. 

Perhaps a rebuild is in order.  All the time I have spent on this I'd have the reinstall done by now. This time I'll leave gnome 3 alone. 

Just one question before I do it. What is the difference between Ubuntu Classic in Unity, and Gnome 3? (in a nutshell)

---

### Post by Dobly on 2011-06-12
Full reinstal done and running happily now in Classic mode. 

Next step is to work though the stuff on the link posted by linuxinstalledfromhdd. 

Thanks all for your help

---

### Post by wildmanne39 on 2011-06-12
> **Dobly said:**
> >>click on top left corner of Unity. Type in the search box for Login. Unlock.

Sounds good, but clicking the Unlock button does nothing. 

Perhaps a rebuild is in order.  All the time I have spent on this I'd have the reinstall done by now. This time I'll leave gnome 3 alone. 

Just one question before I do it. What is the difference between Ubuntu Classic in Unity, and Gnome 3? (in a nutshell)
Hi, glad to hear you reinstalled I think that was the best solution. gnome3 is the new gnome it does not have all the bugs worked out of it yet.

---

