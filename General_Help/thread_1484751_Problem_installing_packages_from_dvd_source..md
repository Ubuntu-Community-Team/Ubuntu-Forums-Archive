---
title: "Problem installing packages from dvd source."
date: 2010-05-16
forum: General Help
---

### Post by roman -&gt; on 2010-05-16
OS: Ubuntu 10.04.
When I try to install some packages by **aptitude**, I see this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157112&stc=1&d=1273993442[/IMG]

Before it, I made it (**sudo apt-cdrom add**):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157114&stc=1&d=1273993571[/IMG]

And it (**sudo apt-get update**):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157113&stc=1&d=1273993571[/IMG]

My dvd-disk is not broken - md5 checksum is right. In **sources.list** I have only cdrom source, without any network repositories. 
When I install one package (for example pptp-linux) which don't use any depending, it work good, but when I have some group of packages - installed only first package from this group, you can see this in a first image, marked by yellow color and set to 16 percent.              
So, what's the matter?

P.S. Sorry for my englsih. 
[IMG]http://img199.imageshack.us/i/aptitude.png/[/IMG]

---

### Post by dino99 on 2010-05-16
try with synaptic: system admin synaptic

---

### Post by roman -&gt; on 2010-05-16
Try Synaptic:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157120&stc=1&d=1273996134[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157121&stc=1&d=1273996134[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157122&stc=1&d=1273996134[/IMG]

---

### Post by roman -&gt; on 2010-05-18
So nobody knows in [COLOR=#000000]what could be the  problem?[/COLOR]

---

### Post by oldos2er on 2010-05-18
Have you verified that /pool/main/v/vim_7.2.330-1ubuntu3_i386.deb exists on the DVD?

---

### Post by roman -&gt; on 2010-05-18
> **oldos2er said:**
> Have you verified that /pool/main/v/vim_7.2.330-1ubuntu3_i386.deb exists on the DVD?

Here:

[IMG]http://georgia.ubuntuforums.org/attachment.php?attachmentid=157418&stc=1&d=1274211667[/IMG]

---

### Post by oldos2er on 2010-05-18
If you double-click on the *deb file, are you able to install it?

---

### Post by roman -&gt; on 2010-05-20
> **oldos2er said:**
> If you double-click on the *deb file, are you able to install it?
Sorry, but I uninstall Ubuntu 10.04 from my main system and I can not try your solution. Now I decided try the Xubuntu 10.04 alternate installation edition, and install it in VirtualBox without **xorg** because I don't need all software which default installs with **gnome**. **Aptitude** don't work correctly there too - the same error: 'file not found' and install only one first package from a group of packages. I try **apt-cdrom add** - all the same way as in Ubuntu 10.04.
I can't find any solutions to solve this problem and it stop me to use Ubuntu as a main system, because I don't have a fast internet connection to load all basic software from internet repositories such as xorg, desktop environment and so on. :(

---

### Post by inso_741 on 2010-05-20
since you are using virtual box, have you tried installing guest additions?

---

### Post by roman -&gt; on 2010-05-22
> **inso_741 said:**
> since you are using virtual box, have you tried installing guest additions?
For what? I have this problem when I use Ubuntu 10.04 like host system too.

---

### Post by ednso on 2010-06-11
Hi,

Same here. Cannot install from Kubuntu DVD, although it is on source list.
Any one has solved this issue?

Bye.

---

### Post by ednso on 2010-06-11
Hi Guys,

Just have found a solution. First, umount your DVD with
sudo umount /dev/sr0
Then create a directory called /cdrom:
sudo mkdir /cdrom
and mount your DVD on in:
sudo mount /dev/sr0 /cdrom
and finally add it as repository:
sudo apt-cdrom add -d /cdrom

This worked here.

Bye.

---

### Post by SaintDanBert on 2010-06-14
I also have this problem.  All of the dialogs and messages say that it cannot find the cdrom-cdrw-dvd-dvdrw device or its media. I've tried to find where to configure the device details for synaptic use. NOTE -- "try" != "succeed".

I can tinker the media contents from a desktop file mangler or the shell so I know the content is present. I cannot make synaptic use the media content with any of the incantations that I know.  In a pinch I have dragged DEB file from the media onto my desktop and then used dpkg to install, but that is ugly.

~~~ 0;-Dan

PS/  From where I sit, it is knife wounds (much worse than "paper cuts") like this that continue to mark linux as a geek tinker toy. I'm not saying it is such a toy, but it is very VERY [highlight]VERY frustrating[/highlight] .

---

