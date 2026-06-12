---
title: "ubuntu/kubuntu 10.10 Freezes on Averatec laptops"
date: 2011-03-31
forum: General Help
---

### Post by dmeehl on 2011-03-31
I'm trying to build a system out of some old laptops for some relatives. I have two Averatec laptops a 3100 series and a 3200 series. Neither Ubuntu nor Kubuntu will install or run from the live cd without locking up solid. 

Trying to install results in a complete freeze somewhere during the installation process. I've also tried the alternate cds to try and avoid a possible graphics driver problem. However, the problem doesn't seem to be X freezing. When I run the live cd instead of the install, the system freezes after a few minutes and is completely halted and must be hard rebooted. No keyboard combinations work including the alt+sysrq combinations.

I tried to get some output from the kernel log by running the live cd and then plugging in a flash drive. I then dump the contents into the flash drive (tail -f /var/log/kern.log > /media/USB\ DISK/kern.log). I got no error output, but maybe this is because it didn't have a chance to flush?  

I've also tried locking the processor at a slower speed with no luck. These laptops do not have a processor with Cool 'n Quiet. I looked for powernowd as I found a recommendation to turn that off, but I didn't find it in the system.

Does anyone have any ideas as to what could be causing this? It seems to be some kind of hardware incompatibility since it happens exactly the same on both laptops, but I am out of ideas.

---

### Post by cain071546 on 2011-03-31
try using a older version of Ubuntu like 9.10
it tends to work better in almost every aspect
i wont retire my 9.10 systems
10.04 is not bad but i HATE 10.10

try good old Debian or even Mint
you could probably get debian to install on a 
steam powered cheese grater 
if all else fails/which ive had happen to me on older hardware 
try puppy Linux's newest release Lucid Puppy built from Ubuntu Packages


or Fedora,Sabayon,Mandriva,Slax,Arch,Suse

---

### Post by dmeehl on 2011-03-31
I'm surprised that the only suggestion is to try a different distro. What is it that you hate about 10.10?

Are all of the other flavors you mentioned package compatible with Ubuntu? I supposed I could just look this up but since you are so familiar... :D

---

### Post by dmeehl on 2011-03-31
Meanwhile... does anyone else have ideas as to how I might gather information on what is causing the problem?

---

### Post by dmeehl on 2011-04-03
FYI, I tried Ubuntu 9.10 with exactly the same results.

---

### Post by dmeehl on 2011-04-04
I also just tried Linux Mint 10. Exactly the same problem. I believe this is something to do with the file system as it freezes in exactly the same spot every time and for every distro: formatting the disc. Could it be a problem with the auto mounter?

---

