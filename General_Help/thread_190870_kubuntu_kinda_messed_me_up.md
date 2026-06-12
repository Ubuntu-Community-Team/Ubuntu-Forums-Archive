---
title: "kubuntu kinda messed me up"
date: 2006-06-06
forum: General Help
---

### Post by Fred Doolie on 2006-06-06
I installed kubuntu-desktop so I'd have KDE to play with ( I use Gnome 95% of the time). All works but now my startup and shutdown screens are blue "Kubuntu" instead of those pretty brown "Ubuntu"s and my Gnome splashscreen is kinda generic looking instead of the Ubunti one that was there before.

How can I get those nice brown ones back?

---

### Post by Nano Geek on 2006-06-06
Try uninstalling and reinstalling ubuntu-desktop.

---

### Post by Fred Doolie on 2006-06-06
Did this:
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop
rebooted

Nothing changed. :-(

---

### Post by Jucato on 2006-06-06
I'm not sure, but I think this has something to do with KDM/GDM. During the installation and setup of kubuntu-desktop, where you asked if you wanted to use KDM as the default (you can only use one *DM at a time). If you answered yes, that probably is the source of the problem. Don't worry, GDM is still installed. It just isn't the default anymore.

I think there's a file that contains which *DM is used as the default. I'm not entirely sure where it is or how to properly go about editing it.

---

### Post by Fred Doolie on 2006-06-06
I found it! After searching all over the forum I found this:
[http://ubuntuforums.org/showthread.php?t=185538&highlight=serengeti](http://ubuntuforums.org/showthread.php?t=185538&highlight=serengeti)

To put it simply this person had the same trouble and used "serengeti" instead. I tried it. The install gives you three options like "serengeti", "Kubuntu" and "default". hehe "Default" is the brown one! Hot dog! It rewrites the kernal and the brown screens come back!

---

### Post by jdong on 2006-06-06
To answer your original question:

sudo update-alternatives --configure usplash-artwork.so


Choose usplash-default.so for the brown Ubuntu splash.

Then, run sudo dpkg-reconfigure linux-image-`uname -r`

---

### Post by Fred Doolie on 2006-06-06
Oh, very good. Now I know how to change the image  to any usplash graphic and what the script was doing. Thank you. I learned something. So glad the orginal graphic wasn't lost. 

[Runs off to find some cool usplash images]

EDIT:

While googling for usplash artwork I found this:
[http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/](http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/)

And here's something else cool that will do it:
[http://ubuntu.wordpress.com/2006/02/12/galternatives-gui-alternatives/](http://ubuntu.wordpress.com/2006/02/12/galternatives-gui-alternatives/)

MORE EDIT:
And with the addition of gnome-splashscreen-manager we're back to normal.
Boy, is Linux different! I'm loving it more by the hour but is it DIFFERENT!

Different (adjective): The way a real OS is suppose to be and makes Winblows look like a child's toy.


... Darn it. I know what I want to do I'm just too uneducated to ask the right questions!

---

### Post by dstein on 2006-06-14
When running "sudo update-alternatives --config usplash-artwork.so", why is there a "+" next to the Kubuntu selection. Also, what does running "sudo dpkg-reconfigure linux-image-`uname -r`" do? Thanks.

---

### Post by jdong on 2006-06-14
[QUOTE=dstein]When running "sudo update-alternatives --config usplash-artwork.so", why is there a "+" next to the Kubuntu selection.
[/quote]
I believe that is the system default.

> 
 Also, what does running "sudo dpkg-reconfigure linux-image-`uname -r`" do? Thanks.

That regenerates the "initrd" for the currently running kernel. Typically, it's done after modifying initrd configuration files or new kernel modules for them to work at bootup. Also, bootsplashes are stored in the initrd, so that's why you have to run it after changing the bootsplash.

---

### Post by user1397 on 2006-06-16
[quote=jdong]To answer your original question:

sudo update-alternatives --configure usplash-artwork.so


Choose usplash-default.so for the brown Ubuntu splash.

Then, run sudo dpkg-reconfigure linux-image-`uname -r`[/quote]actually should be "--config" not "--configure" just a small detail thats all.

---

### Post by Cariboo1938 on 2006-08-26
Obsolete

---

