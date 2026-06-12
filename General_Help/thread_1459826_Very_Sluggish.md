---
title: "Very Sluggish"
date: 2010-04-22
forum: General Help
---

### Post by mpn_1990 on 2010-04-22
Specs:
Dell Dimension 2100 
Intel Pentium III Coppermine 1.1Ghz
512MB RAM
Integrated 82810 Intel graphics
40GB HDD
Ubuntu 9.10

I know this system is rather old, but I never expected Ubuntu to run this sluggish. The load average is consistently above 1 and things like opening a menu take about five seconds to complete. Even something as simple as opening a new webpage will cause the load average to skyrocket up to 2.0-3.5. XFCE and even barebones twm do not improve performance. Flash is unusable in Chrome as even one flash ad will bog down the entire system. Htop shows nothing that would be taking up all the CPU cycles. I don't know why this is running so slow and inefficient, I just know something isn't quite right here because it does not take the power of two to three processors to open a web page.

I've disabled a bunch of startup services, that didn't help much. I thought SMP was the culprit, but the "nosmp" boot option has no effect on the kernel. 

I'm thinking that maybe just the video is not up to par. The 82810 was a terrible graphics controller even in its day...my system ram shows 16MB missing, ostensibly to the video controller. Is there a driver or something I can load that would perhaps improve performance on my system? Would throwing in an old PCI video card help it a bit? Are there any other tips you would recommend?

---

### Post by Falc7 on 2010-04-22
Use lubuntu
[http://lubuntu.net/](http://lubuntu.net/)

Meant to be really quick and light

---

### Post by intrader on 2010-04-25
I am sorry you are having this problems with slowness. I have also reported such problem, but by long post is not getting any responses: [http://ubuntuforums.org/showthread.php?p=9155862#post9155862](http://ubuntuforums.org/showthread.php?p=9155862#post9155862)

I am planning to go back to 9.04 which had very responsive and fast system on a Dell Inpiron 8200 (an old laptop).

Good luck.

---

### Post by mike555 on 2010-04-25
you might want to run "memtest" ..... I had an old pc and it sped up when I changed the RAM memory ...

---

### Post by intrader on 2010-04-25
Thanks for your reply. I tried memtest. 'command not found'

Besides, 9.04 ran just fine on the machine
:confused:

---

### Post by The Real Dave on 2010-04-25
To run a Memtest, you need to select Memtest86 in Grub at boot (hold down shift as it boots if the Grub menu is not normally displayed). This is best run overnight, so it can scan your memory repeatedly for errors. Memory can cause sluggishness, but it's likely that the standard Gnome desktop is just too heavy for your system. Personally, I'd recommend you to try something Openbox based,  like [Crunchbang]("http://crunchbanglinux.org/") or [Archbang]("http://archbang.org/"). Crunchbang is now being built on Debian, Archbang on Arch Linux. Both use Openbox WM and are considerably lighter and quicker than the Ubuntu with Gnome. 

You can also install Openbox on Ubuntu itself, as I normally do. There's a nice guide on setting up a low memory desktop, [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems").

Either way, the Gnome desktop is quite a weight to pull. Openbox is much easier and quicker to configure, and much lighter. You can also add a panel like Tint2 to make things simpler. 

IceWM and Fluxbox are other WM options, both of which are nice and light also.

EDIT: A screenshot of my Openbox desktop

[[IMG]http://linuxexpresso.files.wordpress.com/2010/03/16-mar-2010-1.png?w=200h=120[/IMG]]("http://linuxexpresso.files.wordpress.com/2010/03/16-mar-2010-1.png")

---

### Post by intrader on 2010-04-25
I really appreciate your detailed answer. 

I had ubuntu 9.04 running with Gnome WM with no problems. My box is a Dell Inspiron 8200 and I have found it quite capable until I installed 9.10. 

I installed 9.10 because I inadvertently deleted some mono files used by tomboy and the Package Manager could not restore it. On recommendation by the tomboy irc, I installed 9.10. I am waiting for resolution. My post is
[http://ubuntuforums.org/showthread.php?p=9155862#post9155862](http://ubuntuforums.org/showthread.php?p=9155862#post9155862). It is very long and perhaps because of this it has not gotten any response.

Again, thanks for your answer. I will keep it mind.

---

