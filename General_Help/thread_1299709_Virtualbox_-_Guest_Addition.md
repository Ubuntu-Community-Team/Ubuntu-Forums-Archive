---
title: "Virtualbox - Guest Addition?"
date: 2009-10-24
forum: General Help
---

### Post by Quarkrad on 2009-10-24
I'm not sure what the/a Windows Guest Addition is re: Virtualbox.  Perhaps I need to start all over again...............  I have installed Virtualbox in my 9.04 installation.  I followed a web page(s) on how to install winxp but had no luck using an iso file so I installed xp, via Virtualbox, from the winxp installation CD.  All has gone fine and XP works find (appears to be faster than a native installation!!!!) I have audio as well.  I.e I can fire up Virtualbox, then xp, navigate to Youtube in Firefox and listen to a video - impressive.  I ask this question because when in Virtualbox I capture/start using the winxp screen by clicking the mouse after using the default Ctrl/righ key.  However, I cannot get out of the winxp screen and back to Virtualbox/Ubuntu - I have to close down winxp to get back to Virtualbox.  A number of sites mention this windows Guest Addition but I do not know what this is.

---

### Post by blueridgedog on 2009-10-24
Select your XP virtual box, then DVD/CDROM, then specify to mount an ISO image, then select the guest addon tools image.  When booted, the xp virtual will have a cd in the cdrom with software you can install to make it interact better with your host OS.

---

### Post by Quarkrad on 2009-10-24
Sorry -I need help with this.

**Select your XP virtual box**
I launch Virtualbox on my Ubuntu Desktop

[B]
 then DVD/CDROM, then specify to mount an ISO image[/B]

In the Virtualbox window I click on CD/DVD-ROM in the right hand pane.  This launches a new window asking me were to mount.  I click on the ISO Image File button
[B]
then select the guest addon tools image[/B]
Where is this image?  Do I download it from the web?  (Originally I made an ISO of the winxp installation CD but had no luck with this.  As said  I installed winxp, from within Vbox, using the installation CD, not an image.

 **When booted, the xp virtual will have a cd in the cdrom with software you can install to make it interact better with your host OS.**
This is confusing me - at the moment when Virtualbox launches it fires up winXP in its window and works fine - there is no CD in the cdrom drive.  Are you saying that after mounting the guest addon tools image a CD has to be in the cdrom drive?  What CD?

I have assumed Virtualbox works by loading winXP (or other OSs) into ones HD - as I have done.  Are you saying that it (Vbox) runs off a CD in the cdrom drive?

Sorry to be a bit stupid here.

(Ultimately I would like to see if I could run winxp/itunes in Vbox and update my ipod).

---

### Post by howefield on 2009-10-24
[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

Second video down, "Creating your first Guest Virtual Machine (Windows 7)" it might be easier watching it than following instructions.

---

### Post by xavierp94 on 2009-10-24
When you are running the Windows XP in Virtualbox, in the window, look for the menu Devices > Install Guest Additions.

---

### Post by Quarkrad on 2009-10-24
Thank you all very much - guest addition now installed.

---

### Post by ikisham on 2009-10-24
Protect your XP as you would in a normal installation (specially create a restricted user account to browse the web). It can get infected as usual. You can create a snapshot of the machine while in a healthy state so if it gets infected you have this backup.

---

### Post by shaggy999 on 2009-10-24
I'm surprised nobody has pointed out that you actually don't NEED the guest additions to get your mouse cursor context out of virtualbox. Assuming your "host key" is right-ctrl (the default) just tap that key and the mouse cursor will be unlocked from virtualbox and back to your host os. Virtualbox gives you a message stating this when you first click the mouse cursor inside the VM.

The guest additions add additional features, such as auto-unlocking of the mouse cursor when the cursor hits the edge of the guest os's desktop border, adding support for shared folders, and driver files specific for accelerating things in virtualbox (particularly graphics).

---

### Post by Quarkrad on 2009-10-24
Thanks all - solved.  However..............  I had a problem with usb ports and have now found out (I think) that I need Virtualbox puel - not what I installed, Virtualbox OSE.   Yet another web page shows me how to install vbox puel but when it comes to installing I get the following in terminal:

[B]W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures were invalid: BADSIG DCF9F87B6DFBCBAE Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>
W: You may want to run apt-get update to correct these problems[/B]

I entered the url into my sources list but there is obviously a problem with this signature.  Any idea how this is fixed?

---

### Post by howefield on 2009-10-24
What did you add to your sources.list and did you add the key ?

Instructions here

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

You can also simply download the package to your computer, and double click the file to start the install process. (Presumably you have already uninstalled the OSE version)

---

### Post by Quarkrad on 2009-10-27
Thanks to all - VBox now working inc USB ports.

---

