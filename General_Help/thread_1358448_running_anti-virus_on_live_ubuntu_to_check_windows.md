---
title: "running anti-virus on live ubuntu to check windows HDD"
date: 2009-12-18
forum: General Help
---

### Post by bootdoc on 2009-12-18
is it possible to run a live cd/usb ubuntu in order to clean a windows drive of viruses?  A friend is severely infected.  cannot access the native AVG.  My idea is to boot his box off a live edition and and run anti-virus scan on the native drive.

I've been using ubuntu since dapper but have never tried this before so I don't know if it is possible.  

Also, i have talked to this guy about switching to linux but he is set in his ways.  

Is there any other ideas besides system restore and complete reinstall?

---

### Post by xtjacob on 2009-12-18
I don't know about doing it with Ubuntu but you could try out the Trinity Rescue Kit it has four different virus scanners built in with it.

---

### Post by pluto4ps on 2009-12-18
Well I think to install Ubuntu in USB and then install Avast Linux Version and scan...

---

### Post by pbrane on 2009-12-18
What you suggest is entirely possible. the trick is to create a USB startup and then install the virus scanner. Going the USB route will be much easier than trying to create a live CD. I use f-prot for linux, it's free for home use. And it is one of the best scanner/disinfect programs around. However it is command line only, not GUI.

what pluto4ps said will work fine.

---

### Post by pricetech on 2009-12-18
pbrane:  I haven't used fprot in years.  Thanks for reminding me of its existence.

If the live CD or USB options don't work out, you can always put his hard drive in another computer and clean it that way as well.  This also makes it a lot easier to salvage your friends data in a worse case scenario.

---

### Post by pluto4ps on 2009-12-20
I do agree with "Pricetech" !dea is good...

---

### Post by SlugSlug on 2009-12-20
> **pluto4ps said:**
> Well I think to install Ubuntu in USB and then install Avast Linux Version and scan...


I've done this at work before - works a treat

---

### Post by dcstar on 2009-12-20
> **bootdoc said:**
> is it possible to run a live cd/usb ubuntu in order to clean a windows drive of viruses?  A friend is severely infected.  cannot access the native AVG.  My idea is to boot his box off a live edition and and run anti-virus scan on the native drive.

I've been using ubuntu since dapper but have never tried this before so I don't know if it is possible.  
........

Yes, just install an AV package (like ClamAV) via Synaptic, mount the Windows drive and run a scan.

This can be done off a Live CD (once you set the repositories) but is better done off a persistent USB setup.

---

