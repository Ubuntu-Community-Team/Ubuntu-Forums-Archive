---
title: "Triple boot"
date: 2010-01-02
forum: General Help
---

### Post by linux_addict on 2010-01-02
I have an interesting problem, 2 years ago I became the owner of a Pentium 4, 3.0 ghz HT gaming tower, the tower had two internal hard drives, one with Linux Mint on it and the other with Windows XP.

When I came home from college, I brought it with me, however, before leaving college, I did a clean install of XP as the existing version was riddled with viruses and worms. 

Well, this apparently(I thought) wiped out the original GRUB loader, leaving me only with being able to boot into XP.

I took the computer apart when I got home and spent the next two years working on it off and on, fixing some problems that the original owner had left undone, or improperly done. I took out the 80 gig hard drive that had Linux Mint on it and in its place installed a 160 gig hard drive from an external hard drive that the enclosure had failed. I then split this into two partitions and installed Ubuntu 9.10 onto one of them, leaving the other free for Windows XP to use, along with its own 60 gig hard drive.

Today I decided to see if I could shoehorn the removed 80 gig hard drive that originally
 had Linux Mint on it into the case so I would have three hard drives. After some effort, and tinkering with the PATA settings, I succeeded in making it available to use on the Linux side(the windows install refuses to recognize it). 

I did see if I could get the computer to start up on it, but all I got was a BIOS error saying it had failed to load the operating system. However, after some more tinkering in the BIOS, it abruptly started up on it and showed me the original 
GRUB loader with the option of booting either XP or Linux Mint, however I lost the option to boot into my 80 gig Ubuntu partition. 

I can still access that drive partition, but it is not available as a boot option. 

Anybody have any idea how I can have an option to boot into any of the three operating systems? Its going to get old real fast if I have to rewire each time I want to be able to boot Ubuntu or Mint.

Thanks for any help,
linux_addict

---

