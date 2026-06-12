---
title: "Linux Distro/Recognize Ubuntu?"
date: 2009-07-16
forum: General Help
---

### Post by CaseSensative on 2009-07-16
Hello, I have used Ubuntu since 7.04 and I am a basic user. I feel comfortable with Ubuntu and I was wondering which distros would be good to dual boot with Ubuntu, and can recognize Ubuntu. Any help or feedback would be appreciated, thank you in advanced.

---

### Post by darolu on 2009-07-16
You can try one of the other main "branches", like RedHat-branch; try Fedora, it is similar to use than Ubuntu (both use GNOME as default desktop environment) but its packages are rather different, its package manager is also different, you may like it, is a very complete distro.

Then you can try OpenSuSE (it used to be my favourite distro), it is descendant from Slackware branch but nowadays works very different, it also has GNOME but if you download the DVD (recommended!) you can try KDE, OpenSuSE is a very "customized" distro, its installer is unique and is in my opinion the best one (at least graphically), its custom menu is also nice and has a very complete settings manager called Yast that makes administrative tasks very easy.

I also recommend Slackware, the oldest (and still alive) distro, is very efficient and makes your hardware work great and is not too complicated, it uses XFCE or KDE (among others like fluxbox); it has no GNOME though (not as default desktop), its packages work a bit different, is not as simple to install programs like in Ubuntu or OpenSuSE but is not hard either; it uses Lilo instead of GRUB so read some documentation about lilo so you can learn how to configure your dual-booting the way you like it.

If you want something like Ubuntu but witha  twist, then try LinuxMint it is based on Ubuntu.

If you are brave and feel experienced enough, you can try Arch or Gentoo (installing with minimal CD) for a fully custom isntallation compiling every piece of the OS.

---

### Post by CaseSensative on 2009-07-16
I tried dual booting with Fedora. Fedora did not recognize Ubuntu. I will try OpenSuse. Does openSuse have a Add/Remove repository? Does OpenSuse recognize Ubuntu during partitioning? Sorry if I ask alot of questions.

---

### Post by Legace on 2009-07-16
> **CaseSensative said:**
> I tried dual booting with Fedora. Fedora did not recognize Ubuntu. I will try OpenSuse. Does openSuse have a Add/Remove repository? Does OpenSuse recognize Ubuntu during partitioning? Sorry if I ask alot of questions.

Suse does not use the same repo as Ubuntu, but you should find everything you need on it, too. No, they won't "recognize" Ubuntu. No distro will. You just need to install SuSE/Fedora onto a seprate partition..

---

### Post by Zack McCool on 2009-07-16
I'm not sure what you mean by "recognize" Ubuntu.

If you mean that you want it to recognize it during an install and make all of the necessary changes to your filesystems without deleting anything, then no.  You'll need to do that manually.  You'll need to manually partition during the install, resize partitions if necessary, create the partition(s) for the new distro, and you may need to edit Grub once everything is done.

If you're just trying to try out different distros to see if you like the look and feel better, might I suggest installing VMWare server or VirtualBox and trying them out as VM's?  This will not interrupt your current partitions, and it will allow you to run them at the same time.

---

### Post by TeamJ on 2009-07-16
you could try other ubuntus, linux mint, slackware, fedora

---

### Post by andrew.46 on 2009-07-17
Hi CaseSensative,

> **CaseSensative said:**
> Hello, I have used Ubuntu since 7.04 and I am a basic user. I feel comfortable with Ubuntu and I was wondering which distros would be good to dual boot with Ubuntu, and can recognize Ubuntu. 

If you are considering trying a few distros an excellent alternative to dual booting is to use a Virtual Machine such as Virtualbox. These forums have a section devoted to the subject:

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

All the best,

Andrew

---

### Post by akshay.sulakhe on 2009-07-17
Believe me..no one other than Ubuntu identifies other distros...install whatever u want and then run grub-install hd0 in ubuntu and the find uuid of ur other linux partitions and dont forget to copy their kernel names and all...add manually...it may sound cumbersome right now..but its easy...

---

### Post by wolfdale on 2009-07-19
I was distro hopping while using Ubuntu Jaunty as my main OS. I noticed that when I tried some KDE distros (Mandriva, Fedora), their GRUB install would find my Jaunty and (I believe) added it via chainloading. I then played around with their GRUB setting and accidentally lost my Jaunty login. I've tried manually adding my Jaunty login credential into /boot/grub/grub.conf (menu.lst) several times using numerous methods but none worked. I ended up reinstalling GRUB from my live CD in order to get Jaunty back, but again lost my KDE logins. I noticed that the GRUB command "find /sbin/init" or "find /boot/grub/stage1" doesn't seem to work (locate multiple stages and paths) across KDE/Gnome distros and vise-versa even though both distros uses GRUB. Anyone come across this? Is this just a Gnome and KDE 4.x thing?

---

### Post by CaseSensative on 2009-07-19
Hello, thank all of you for your help. I chose to go with openSuse and I am pretty satisfied. OpenSuse is a little different then Ubuntu but It seems pretty user friendly. I am looking forward to dabbling around with different distros.

---

