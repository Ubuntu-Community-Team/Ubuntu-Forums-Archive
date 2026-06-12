---
title: "No wireless for 11.04 Inspiron"
date: 2011-06-16
forum: General Help
---

### Post by dhodgson on 2011-06-16
Hi all like alot of people I have had trouble with the wireless (and to some degree the DSL connection) using 11.04. All I can say is DON'T DOWNLOAD THE LATEST UBUNTU STA DRIVERS for wireless. They simply do not work.  It is beyond me why they have them as a download (in updates) when they simply do not work. Get rid of them and download a generic driver which does work on Inspiron laptops (and others). And when you update unclick the ubuntu  STA drivers as if you don't your wireless will stop working again and you will have to re-install your generic drivers again. Next, after you have unintalled the unbuntu STA drivers from additional drivers AND you have downloaded and installed your generic STA drivers DO NOT forget to activate the driver in additional drivers. Also ensure through synaptic manager you have downloaded firmware b43 installer and b43fwcutter. Re-start your machine and bingo you will have wireless. Here are the links for 32bit and 64 bit machines for the generic STA drivers.

For 64 bit:   [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb)

For 32 bit:   [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)

Once I got my head around this it took me 3 mins to get it up and running and haven't had any problems. 
Derrick

---

