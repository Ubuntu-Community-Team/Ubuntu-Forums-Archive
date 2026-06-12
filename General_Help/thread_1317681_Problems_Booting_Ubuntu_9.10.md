---
title: "Problems Booting Ubuntu 9.10"
date: 2009-11-06
forum: General Help
---

### Post by Pernig on 2009-11-06
I installed Ubuntu 9.10 i386 edition tonight and got the following problem. I have got a workaround but thought I should still let the community know. I have used search to see if this bug exists but I can't seem to find it. Please excuse my ignorance if this is not the case.

I will quote what I posted on another forum earlier so you can get the gist of how I have gone about it:

[QUOTE="Pernig"]Basically I cannot get onto GRUB without first putting in a live CD then selecting 'boot first hard disk', or putting in a Windows disc. I actually had this same problem before, when the drive the operating systems are installed on was a single NTFS partition sporting XP alone. 

Also, when I get to logging in, I am presented with text-based login only which flashes many times a second as if it is trying to load X to give me a visual login screen but is instantly reverting to text. I combated this by reinstalling and getting it to automatically login (not a problem as I am the only user). My first question is; do you think this login problem is related, or a separate issue? The reason I ask is because the between now and the last time I used Linux on this machine, GRUB has been developed a fair bit and the version of GRUB they bundle with Ubuntu is in beta. 

Secondly, do you think dodgy booting suggests my hard drive is knackered, or could I solve the problem by simply wiping the drive and creating a new partition table? I will probably not bother doing this as although all my documents and personal files are all on a different physical drive, I play Garry's Mod and I have lots of addons installed via SVNs which I can't be arsed to put on again.[/QUOTE]

Since then I have actually reinstalled Ubuntu 9.10 amd64 edition as it seemed to slip my mind that my computer is 64 bit :lol:. Anyway, I have installed it so that it logs me straight on as I am the only user, therefore I do not know if this problem is specific to the 32-bit version. Also, as I'm sure you can understand, I am reluctant to change the login settings so that it doesn't log me in automatically in case I get locked out of the OS so to speak, as I am not a Linux expert!

In summary, I am not reporting the initial booting bug as I'm quite sure this is a problem with my hardware. What I am reporting is the login screen failure, but am also including details of the hardware problem in case this is related.

Thanks in advance for your help.

---

### Post by Pernig on 2009-11-06
OK, I can shed a little more light on the situation:

I can logout and log back in and everything is as it should be. I'm not feeling quite brave enough to change the settings and log in from startup right now! 

Could anyone tell me if I were to change the settings in Login Screen and the problem returns, would I be able to change them back again if I started in compatibility mode? If not I will be locked out of the system as it is impossible to type my password in because the flashing I mentioned seems to focus then unfocus the keyboard on the text based login.

Perhaps this bug is something to do with when I was first starting up, I was using the general video drivers. Now I have the Nvidia drivers installed for my card (GeForce 8500GT). Perhaps this has solved the problem. I will keep you all updated.

---

