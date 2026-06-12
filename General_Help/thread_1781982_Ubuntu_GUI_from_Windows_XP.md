---
title: "Ubuntu GUI from Windows XP"
date: 2011-06-14
forum: General Help
---

### Post by Syndy on 2011-06-14
Hi,
I am new to Linux and and I'm having a problem trying to run Ubuntu GUI remotely on Windows XP and wonder if anyone can give me a pointer or two?
I have installed Ubuntu 10.04.2 LTS on a stand alone sever (HDD install). It works fine, it has a monitor, keyboard and mouse directly connected and 'startx' brings the GUI up OK. However, i want to rack mount the server without the monitor, mouse or keyboard so i have enabled SSH on Ubuntu to allow a remote secure connection. I can connect OK from windows XP using Putty via SSH. I get the Ubuntu login prompt and it accepts the user and password OK. However, 'startx' now fails. 
So, i have installed Cygwin/x on the Windows XP PC. I then use the SSH tunnel in Putty to connect and login to Ubuntu. I start Cygwin XWIN server on XP then use the 'xterm' command in Putty. A new pop up occurs which has the Ubuntu cmd prompt. I enter 'startx' and receive the following error;
 
*X.Org X Server 1.7.6*
*Release Date: 2010-03-17*
*X Protocol Version 11, Revision 0*
*Build Operating System: Linux 2.6.24-27-server i686 Ubuntu*
*Current Operating System: Linux bt 2.6.38 #1 SMP Thu Mar 17 20:52:18 EDT 2011 i686*
*Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38 *
*root=UUID=d6cceca3-35ea-41d9-bfde-068b4e07418c ro text splash nomodeset vga=791*
*Build Date: 08 March 2011 08:22:50AM*
*xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see *[*http://www.ubuntu.com/support*]("http://www.ubuntu.com/support")*) *
*Current version of pixman: 0.16.4*
*Before reporting problems, check *[*http://wiki.x.org*]("http://wiki.x.org")
*to make sure that you have the latest version.*
*Markers: (--) probed, (**) from config file, (==) default setting,*
*(++) from command line, (!!) notice, (II) informational,*
*(WW) warning, (EE) error, (NI) not implemented, (??) unknown.*
*(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 10 10:05:49 2011*
*(==) Using config directory: "/usr/lib/X11/xorg.conf.d"*
*error setting MTRR (base = 0xfd000000, size = 0x00800000, type = 1) Inappropriate ioctl for *
*device (25)*
*error setting MTRR (base = 0xfd000000, size = 0x00800000, type = 1) Inappropriate ioctl for *
*device (25)*
*error setting MTRR (base = 0xfd000000, size = 0x00800000, type = 1) Inappropriate ioctl for *
*device (25)*
*FATAL: Module mach64 not found.*
*(EE) [drm] drmOpen failed.*
*(EE) MACH64(0): [dri] DRIScreenInit Failed*
 
 
I have searched on the Internet and found information on the MTRR and Mach64 references. Do i have 2 different problems here or are they related? From what i have read do i need to install some patch for the MTRR error, if so how do i go about this? In terms of the MACH64 error, i believe this indicates some display problem? I have read about ATI graphics issues, the server does have ATI rage onboard graphics. Do i need to install new drivers? The Ubuntu displays fine on the connected monitor, so they seem to be working correctly. Is this more of a configuration issue?
 
Or am i going about this completely wrong?
 
I think i have read so much i am now confused regarding the problem i have and the fix. Any help would really be appreciated. Please keep in mind that i am new to this, so step by step would be great.
 
Many Thanks,
 
Syndy.

---

### Post by pqwoerituytrueiwoq on 2011-06-14
[http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/](http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/)
that may be what you want
windows will need any vnc client

---

### Post by Syndy on 2011-06-15
Thanks for the reply. I think you are right, VNC looks the way to go. I'll give VNC a go!
 
Cheers,
 
Syndy

---

