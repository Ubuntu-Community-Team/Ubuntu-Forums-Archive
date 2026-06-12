---
title: "Just to Share. My 9.1O ToDo List"
date: 2009-12-29
forum: General Help
---

### Post by samrat1985 on 2009-12-29
[SIZE="3"][FONT="Courier New"]Hi,

I am using Ubuntu since 2006.

Just to share. Here are few thing I need to do to match 
Ubuntu 9.1O up to my Windows install (dual boot ~ games!!).

My ubuntu 9.1O ToDo List


[COLOR="RoyalBlue"]# mplayer && purevideo [VDPAU]	#[/COLOR]

I had compiled it under 9.O4. Now it is broken :( 9.1O
Mplayer was not using processor even 5% playing HD! Completely working with smplayer & all. cool!!
See [wait. Link in linux partition. How do i access that through windows in 9.1O?]


[COLOR="RoyalBlue"]# DISABLE python startup & ubuntuONE	#[/COLOR]

This is easy. No need ubuntuONE.
"sysv-rc-conf" is the best app there is for these dirty jobs.


[COLOR="RoyalBlue"]# REMOVE all icons @ gnome-panel	#[/COLOR]

This doesn't work! [http://ubuntuforums.org/showthread.php?p=8211343](http://ubuntuforums.org/showthread.php?p=8211343)


[COLOR="RoyalBlue"]# linux_phc (acpi_inside_kernel_since_9.O4)	#[/COLOR]

My C2D E75OO is very hot ~ 75C @ 3.3GHz (did all I could to cool it physically except expensive cooler).
Using RMClock in Windows to reduce voltage. Previously used 1.288 core voltage @ Cpu-Z. 
Now it uses 1.152. Heat is reduced to 54C @ full usage (even in LinX v6).

Same can be achieved in linux using linux PHC patch for acpi module. 
See [http://www.linux-phc.org/forum/viewtopic.php?f=6&t=67](http://www.linux-phc.org/forum/viewtopic.php?f=6&t=67)


[COLOR="RoyalBlue"]# nvidia official driver & "custom_kernel" && dkms	#[/COLOR]

Says it all. New kernel for linux_phc req. since acpi module is no longer a module!
It is inside the kernel now (Why did they do it?) :(

Official Nvidia drivers would require my custom kernel source & 
so would any future graphic driver update. (remeber to keep the source).


[COLOR="RoyalBlue"]# `visudo` error @ gnome apps like mount thru nautilus.	#[/COLOR]

Previously I used to do visudo and add NOPASSWD in sudoers file to stop asking 
me for password to do super-user task. This give errors in 9.1O. Example mount internal partitions.
Going to look into this.

[COLOR="RoyalBlue"]# application filtering firewall   #[/COLOR]
A firewall like Zonealarm or Comodo to block all outgoing connection and ask for my permission before allowing outgoing connections. Firestarter had it but was buggy which made me dump it ( didn't start or something I don't remember, used it in 8.1O. Was a workaround for it too. Starting it before network or something).


PS- screenshots won't hurt! A bit OLD.[/FONT][/SIZE]

---

