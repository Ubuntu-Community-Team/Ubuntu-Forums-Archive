---
title: "VirtualBox - USB Doesn't Work."
date: 2009-07-24
forum: General Help
---

### Post by Roasted on 2009-07-24
Yes - I have the latest version of VirtualBox from the web site.
Yes - My user is in the vboxusers group.
Yes - My user has "Use VirtualBox" priviledges.
Yes - I have guest additions installed.

I had USB working before. But now it doesn't work...

---

### Post by brodeur235 on 2009-07-24
I don't want to be that guy, but I had this same problem, posted for help with it on several forums, and never got it resolved. I eventually resorted to buying a floppy drive and using that. Actually I was trying to boot my OS from USB... Maybe you'll have more luck in finding a solution. I hope you do,

Brodeur235

---

### Post by andrew.46 on 2009-07-25
hi Roasted,

> **Roasted said:**
> Yes - I have the latest version of VirtualBox from the web site.
Yes - My user is in the vboxusers group.
Yes - My user has "Use VirtualBox" priviledges.
Yes - I have guest additions installed.

I had USB working before. But now it doesn't work...

And I guess you have the PUEL version not the OSE version? My own experience unfortunately is with the OSE version so i will be of little help to you :confused:.

Andrew

---

### Post by keplerspeed on 2009-07-25
Well Roasted has said the version from the website, so I would assume it is the PUEL version.

I have always had to add lines to fstab to enable proc bus. See here [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

---

### Post by Roasted on 2009-07-25
> **keplerspeed said:**
> Well Roasted has said the version from the website, so I would assume it is the PUEL version.

I have always had to add lines to fstab to enable proc bus. See here [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

I didn't have to. The only thing was if my Ubuntu system currently had the device mounted it couldn't be activated in Windows. Before I would just unmount it in Ubuntu and it would be recognized in Windows.

---

