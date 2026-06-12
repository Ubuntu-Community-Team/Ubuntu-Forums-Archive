---
title: "Help me build an experimental system"
date: 2006-04-10
forum: General Help
---

### Post by Basu on 2006-04-10
I've managed to get my hands on a slightly old systems with specs like: P4 2.8Ghz, 512 RAM and an 80GD hard disk and I intend to set it up as an experimental system where I can play around with various distros. here is my plan for carving up the hard drive:
hda1 : 10 GB Ubuntu
hda2 : 10 GB Arch
hda3 : 10 GB Some BSD
hda4 ,5 ,6: 10 GB each, experimentals
hda7 : 10 GB media parition
hda8 : 10 GB /home partition

Now, is it safe to have all the distros to share the same home directory? If it's not I'll just use hda8 to store the data and symlink to the home dirs. Since I'll be using the media and hda8 partitions more than the experimentals, would it be better to put them before the experimentals? And should the swap be at the end or right after Ubuntu and Arch? How do the rest of you have your experimental machines set up?
Thanks,
Basu

---

### Post by waster on 2006-04-10
not safe to reuse home as each distro will probably have different versions of software.

You won't be able to do hda1...8. You'll need extended partitions, but if possible you'd be better off using LVM.

---

### Post by justleen on 2006-04-10
[QUOTE=Basu]I've managed to get my hands on a slightly old systems with specs like: P4 2.8Ghz, 512 RAM and an 80GD hard disk
[/QUOTE]


Sorry.. but you call that slighty old?? considering half the world is still running win98, or are waiting for a 100$ laptop?

](*,)

---

### Post by Basu on 2006-04-11
Slightly old as in it was first bought about 3 years ago. 
How do I use LVM and what are the benefits over extended partitions?
thanks

---

### Post by IYY on 2006-04-11
> Slightly old as in it was first bought about 3 years ago. 

3 years ago, old? ... My computer was bought in 98 and I'm still happy with it.

---

### Post by Basu on 2006-04-11
Can we stop talking about the age of my computer?? Is there a way to find out what kernel modules my hardware actually needs? modprobe -l throws up a huge list of things including wifi and PCMCIA modules which I don't use.

---

