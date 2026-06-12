---
title: "Can I mount a Windows Desktop computer HDD to my Ubuntu machine?"
date: 2009-10-16
forum: General Help
---

### Post by Roasted on 2009-10-16
I have an Ubuntu desktop here, along with an infected Windows computer with the Conficker virus.

I have found out ClamAV with Ubuntu will remove the Conficker virus. It successfully removed the virus from my infected FAT32 flash drive.

I'm curious... can I plug in an ethernet cable between the two computers and somehow "mount" the HDD in the XP machine to my Ubuntu computer so I can scan that HDD from within Ubuntu?

---

### Post by DeMus on 2009-10-16
> **Roasted said:**
> I have an Ubuntu desktop here, along with an infected Windows computer with the Conficker virus.

I have found out ClamAV with Ubuntu will remove the Conficker virus. It successfully removed the virus from my infected FAT32 flash drive.

I'm curious... can I plug in an ethernet cable between the two computers and somehow "mount" the HDD in the XP machine to my Ubuntu computer so I can scan that HDD from within Ubuntu?

You want to erase a Windows virus on a Windows system with a Ubuntu program by connecting the two computers by cable?
Can't you just take the hard disk and connect it in your Ubuntu machine, as an extra disk? Saves you the trouble of having Samba installed.
Also, a Windows virus can't hurt a Linux system so you will be safe by doing that.

---

### Post by ottosykora on 2009-10-16
But I would in such situation simply bott the infected computer from live CD ubuntu, then install on that running system clamav. Yes this works, it is however installed just kind of temporary, in ram only, but it is here.

---

### Post by Roasted on 2009-10-16
> **DeMus said:**
> You want to erase a Windows virus on a Windows system with a Ubuntu program by connecting the two computers by cable?
Can't you just take the hard disk and connect it in your Ubuntu machine, as an extra disk? Saves you the trouble of having Samba installed.
Also, a Windows virus can't hurt a Linux system so you will be safe by doing that.

I already have Samba set up, so that's not an issue.

In this particular set up, I couldn't do that with plopping the hard drive in, because the particular computer I use at work with Ubuntu only has 2 SATA ports - CD Rom drive and HDD. The computer that's infected that I was going to play around with as a slave PC to my Ubuntu computer has an IDE connection.

In short - the computer I have Ubuntu on was designed for slim use and doesn't offer any expansion whatsoever, so I'm stuck in that department.

I got the idea from a Mac video I saw on CNET one time, because with Macs using Firewire you could boot another Mac laptop and "slave" it as an external hard drive.

AKA - two Mac laptops - can connect 1 to the other - and the secondary Mac shows up as an external drive on the primary Mac. Therefore, in Mac land, you could scan the "external" (secondary Mac) drive from there.

I was just curious if that kind of thing was available on Linux - but utilizing Windows as the secondary drive.

---

### Post by screaminfakah on 2009-10-16
I agree that booting the live cd is alot less trouble.

You could also just get a free conficker removal tool from Symantec or the likes and just run it from inside windows.

---

### Post by StuartN on 2009-10-16
> **screaminfakah said:**
> I agree that booting the live cd is alot less trouble.

Any self-respecting virus would have installed itself as a Windows service in any case, so you would be unable to delete it without halting Windows.

---

### Post by Roasted on 2009-10-17
> **screaminfakah said:**
> I agree that booting the live cd is alot less trouble.

You could also just get a free conficker removal tool from Symantec or the likes and just run it from inside windows.

That's what I did. I couldn't figure out why I kept getting re-infected, though.

Idiot me - I forgot to include my flash drive on the scan list. It would scan C drive, but before deleting, it would hit my flash drive and infect it... but I used my flash drive to transfer the program since I refused to plug this PC into the network for fear of the virus spreading more than it already is.

Now that I included my flash drive on the scan list, it zapped it on the computer + flash drive and according to every conficker scanner I've used - is gone. Woop!

---

### Post by dj-toonz on 2009-10-17
What I do in situations like this , pull the hard drive out & insert it in a USB enclosure and scan it with clamTK that way on the laptop, as using the live disc on the desktop,, I can't get the Ethernet or wifi working :-(

---

