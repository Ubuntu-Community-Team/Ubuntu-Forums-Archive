---
title: "Quickly transferring data off old machines."
date: 2009-11-21
forum: General Help
---

### Post by rcasey on 2009-11-21
Hey there,

I have a fairly simple task I believe Ubuntu would be great for. My organization accepts donated computers, which we process (format, Ubuntu), clean, and redistribute. One common request we get from people donating machines is a way for us to pull their data off before wiping the drive.

We tried booting into Windows (which we've seen anything between 98 and Vista), creating SMB shares, and transferring data off to be burned, emailed, or dropped on a thumb drive, depending how the donator wanted it. This process is very time consuming and we can never produce a sure fire repeatable method workable enough to train someone to do consistently.

So we started live booting Ubuntu off CD, mounting the donators drive, connecting to an Samba server we setup, and manually dragging and dropping files.

My question is about streamlining the process. Based on my research so far, I would like to customize a live CD of Ubuntu to automatically mount all available FAT32 and NTFS drives, then create a share of these drives over SMB, all automatically on boot. This way we can boot off the liveCD, and just connect to the machine over ethernet using SMB, and grab all the data we need. Doing it this way would allow one person to be simultaneously accessing shares on multiple computers. We also wouldn't have to connect the machine to a keyboard/mouse/video setup beyond changing the BIOS settings to boot off the CD, allowing us to "set, boot, and forget".

So based on this description are their any major roadblocks I'm going to run into attempting to produce this LiveCD?

Thanks in advance for any advice as well.

---

