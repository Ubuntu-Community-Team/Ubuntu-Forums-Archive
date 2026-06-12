---
title: "GRUB and Bootup Splash Screen"
date: 2012-03-31
forum: General Help
---

### Post by jbblack on 2012-03-31
Not sure what to call it other than the boot splash screen.

I am dual-booting Win7 and Ubuntu using GRUB 2.  At some point last night, I downloaded "kubuntu-desktop" and it downloaded a boat-load of stuff.  I didn't like it and removed it.  My problem is that the kubuntu splash screen shows up once I select Ubuntu from GRUB.  As far as I can tell, I've deleted all the Kubuntu information except this and I don't really like it.  Even the GRUB menu is blue.

Any ideas how I can fix that either via gedit or a graphical interface?

Thanks,
Joel

---

### Post by Bucky Ball on 2012-03-31
Make sure you haven't got 'kubuntu-default-settings' still installed.

Removing kubuntu-desktop alone will not remove the boat-load of stuff it dragged in, unfortunately.

You might also like to try Grub Customizer which allows you to manipulate the splash screen and a whole lot of other things grub ...

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer]("https://launchpad.net/%7Edanielrichter2007/+archive/grub-customizer")

Choose your release from the drop-down menu.

---

### Post by Scooby-2 on 2012-03-31
You might also like to try the Super Boot Manager, which I have used to get a professional, customised and modern boot screen.

http://www.omgubuntu.co.uk/2011/05/super-boot-manager-eases-burg-grub-plymouth-tweaking-pains/

Sorry I cannot make this a hyperlink. When I try to do this, this site abbreviates the text, which is OK.... but it also abbreviates the hyperlink, which results in a page not found. :confused:

---

### Post by raja.genupula on 2012-03-31
> **Bucky Ball said:**
> Make sure you haven't got 'kubuntu-default-settings' still installed.

Removing kubuntu-desktop alone will not remove the boat-load of stuff it dragged in, unfortunately.

You might also like to try Grub Customizer which allows you to manipulate the splash screen and a whole lot of other things grub ...

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer]("https://launchpad.net/%7Edanielrichter2007/+archive/grub-customizer")

Choose your release from the drop-down menu.

+1 

[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)

will explain you what you can do with that ,

---

### Post by jbblack on 2012-04-01
I never could get Super Boot Manager to install.  The dialog stated something about not being able to find the file.  I *did* get the grub customizer to install and just used it.  Hopefully I didn't break anything and this is solved.  If so, I'll mark it as solved.  :)

-Joel

---

### Post by electrojustin on 2012-04-01
First find a photo you want as your splash screen. Then drop it into /boot/grub. Finally run update-grub. There you are, you just changed your grub background. If you really like the purple background I'm sure that will be easy to find on the internet. Also, if there is a .tga in /boot/grub already, that might be whats causing the blue background.

---

### Post by Bucky Ball on 2012-04-01
> **electrojustin said:**
> First find a photo you want as your splash screen. Then drop it into /boot/grub. Finally run update-grub. There you are, you just changed your grub background. If you really like the purple background I'm sure that will be easy to find on the internet. Also, if there is a .tga in /boot/grub already, that might be whats causing the blue background.

Grub Customizer probably easier, friendlier and more versatile but nice tip ... ;)

---

