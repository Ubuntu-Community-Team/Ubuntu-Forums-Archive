---
title: "virtulabox guest additions"
date: 2009-12-28
forum: General Help
---

### Post by unix1adm on 2009-12-28
Hello, I am having some issues with the VB guest additions. Specifically the video driver. 

I found this thread but it does not work for me. 

[http://ubuntuforums.org/showthread.php?t=1122085](http://ubuntuforums.org/showthread.php?t=1122085)

I have some sw that needs the 3d and screen resolution to be changed. I get the following error:


The virtual machine window is optimized to work in 32 bit color mode but the virtual display is currently set to 16 bit.
Please open the display properties dialog of the guest OS and select a 32 bit color mode, if it is available, for best possible performance of the virtual video subsystem.
Note. Some operating systems, like OS/2, may actually work in 32 bit mode but report it as 24 bit (16 million colors). You may try to select a different color mode to see if this message disappears or you can simply disable the message now if you are sure the required color mode (32 bit) is not available in the guest OS.

When I install the guest addition in safe mode the XP system crashes when I try to run the full windows mode and part works but still cannot get my application to work. 

The vendor told me I needed these settings turned on. how can I do that?

"If you go to the run option on the computer and type dxdiag to run the directx diagnostic program, then go to the display tab, what does it say the status is for direct draw acceleration, direct 3d acceleration, and apg texture acceleration? These all have to be enabled for the software to work. If the video card does not support these functions the software can not work with it."

Thanx

---

### Post by unix1adm on 2009-12-28
The other thing i find strange is that I do not get a DNS entry for my interface. If I use iP to a site it works. If I hard code the DNS servers it works. I do get a DHCP address. 

Any thoughts why I am not picking up the host Ubuntu DNS settings?

if I use a wireless inter face it was working with DNS or a hard wired one. If I try my PCMCIA VZ modem it seems to work Or at least it did. Ill have to check it again. 

I am using a Droid tethered to the Host OS and it works fine . But for some reason the DNS is not picked up by the guest. I am using a /etc/resolv.conf for my Droid setting and a default one for the wireless/hard wired setting. 

I wonder if thats the reason but I would think as long as the resolv.conf worked in the host it should get picked up my the XP guest.

---

### Post by unix1adm on 2009-12-29
anyone have any ideas on this????

---

### Post by unix1adm on 2009-12-29
I dont understand what that link has to do with my problem....

That is some sort of blogger site for mp3 etc. not vbox

---

### Post by howefield on 2009-12-30
> **unix1adm said:**
> I dont understand what that link has to do with my problem....

That is some sort of blogger site for mp3 etc. not vbox

It is probably just someone spamming their blog, but the posting appears to have been deleted by an admin.

Although you, very kindly have reposted it ;) 

Is this a game you are trying to run, if so, what is it ?

---

### Post by unix1adm on 2010-01-02
> **howefield said:**
> It is probably just someone spamming their blog, but the posting appears to have been deleted by an admin.

Although you, very kindly have reposted it ;) 

Is this a game you are trying to run, if so, what is it ?

No game. I am trying to view my home security cameras using the q-see software...

Sorry about reposting  the other link. Thank you admins

---

