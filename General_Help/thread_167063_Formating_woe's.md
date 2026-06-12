---
title: "Formating woe's"
date: 2006-04-27
forum: General Help
---

### Post by RotoGrip on 2006-04-27
Hi all,

 I recently installed Kubuntu to try it out and then realized that it just wasnt working. So back to Ubuntu it was. I have an 160 hd in my box but Ubuntu is only reading 130. After the formatting process Ubuntu does it thing and then displays that it has detected another OS on the system and wants to install grub for dual-boot. How can i totally wipe this drive so i have just Ubuntu back.

Thanks,

---

### Post by Jagot on 2006-04-27
You did ask Ubuntu to wipe and use the whole disk during the partitioning stage I take it?

---

### Post by RotoGrip on 2006-04-27
[QUOTE=Jagot]You did ask Ubuntu to wipe and use the whole disk during the partitioning stage I take it?[/QUOTE]


Yes sir, the whole thing

---

### Post by Qrk on 2006-04-27
What OS did it detect? 

Ubuntu will install GRUB whether or not there is another OS on the drive.

---

### Post by RotoGrip on 2006-04-27
[QUOTE=Qrk]What OS did it detect? 

Ubuntu will install GRUB whether or not there is another OS on the drive.[/QUOTE]


 It shows at least 4-5 diffrent types of Ubuntu, Wich im guessin some of those are Kubuntu as well?

---

### Post by Qrk on 2006-04-27
hmm. That is interesting. I'd go through the installation, but select "manually edit the partition tables" and see how many partitions there are. You can delete the partitions manually to reformat instead of using the automatic feature. 

And for the record, you don't need to uninstall Ubuntu to install kubuntu. They aren't really different, you can get kubunut by doing *sudo apt-get install kubuntu-desktop* from Ubuntu. Not that it helps now.

---

