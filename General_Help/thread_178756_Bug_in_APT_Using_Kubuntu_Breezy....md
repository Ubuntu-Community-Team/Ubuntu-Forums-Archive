---
title: "Bug in APT? Using Kubuntu Breezy..."
date: 2006-05-18
forum: General Help
---

### Post by c0lea on 2006-05-18
Hello :) 

I have been using Kubuntu Breezy for a while, with a good experience overall... however, i ran into a strange glitch 2 times, wich i have no idea why its happening...

It went like this, the first time i installed synaptic instead of Adept for package management, and afterwards, i wanted to ditch synaptic and go back to Adept.  When i went to apt-get install adept, it prompted that it needed to install quite a lot of packages, and remove quite a few too. This seemed strange to me, as i just wanted to install a package manager, wich i didnt knew required so many package installation and removal... The strange part is that part of the packages requested for removal were the linux kernel images! Even APT displayed a message that i really shouldnt remove that package, cause it would cause inconsistency problems... so i told apt not to remove it, that caused the whole proccess to exit with an error, an after rebooting, my system was broken. I had to do a reinstall. :???: 

Then, after reinstalling everything, same thing happened , only this time it was because i wanted to install evolution... ](*,) 

Why would a package require the linux kernel image to be removed? Is this a bug on APT? or am i not understanding something here? :-k 

Thanks in advance for any help you can give.

Regards,
c0lea

---

### Post by infoburner on 2006-05-18
your not misunderstanding anything, evolution should not remove the kernel images.

it sounds to me like you might have a bad install cd. did you md5sum the image and the cd after it was burnt?

---

### Post by c0lea on 2006-05-18
... nope, didnt do so :???: 

So maybe it is a corrupted image huh?

Didnt knew that... Thanks! :D

---

### Post by infoburner on 2006-05-18
ive been bitten by getting lazy and not chksumming an install cd at least a billion times

---

