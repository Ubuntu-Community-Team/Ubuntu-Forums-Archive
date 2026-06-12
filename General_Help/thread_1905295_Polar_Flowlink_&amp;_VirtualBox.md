---
title: "Polar Flowlink &amp; VirtualBox"
date: 2012-01-06
forum: General Help
---

### Post by Macrotus on 2012-01-06
Hi

I know that Polar Flowlink doesn't suppor any Linux, but I was a little shocked when I realized that it doesn't even show it! I can see it with lsusb command. 

I was wondering, how I can let VirtualBox use it? I have installed XP in VirtualBox, and I would like to use the Flowlink with it.

---

### Post by fschlagel on 2012-12-12
I was succesful by installing** XP SP3** in **VirtualBox 4.2.4** on Ubuntu 12.04 64bit.  Make sure you also install **VirtualBox 4.2.4 Oracle VM VirtualBox Extension Pack. **This will allow passthrough of USB devices (ie Polar FlowLink).  Install latest version of WebSync 2.7.0 on XP.  That should do it.  I can sync my FT60.  Data transfer to polarpersonaltrainer.com works fine.  I do however get an error at the end of the transmission, so I must manually login to polar website, but all data has been successfully synced.

---

