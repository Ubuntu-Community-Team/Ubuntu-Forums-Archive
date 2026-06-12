---
title: "Slow Internet Speeds After 11.04 64bit Installed"
date: 2011-07-29
forum: General Help
---

### Post by spec36 on 2011-07-29
I have recently switched to Ubuntu 11.04 64bit from Windows 7. Since installing 11.07 I have experienced random disconnects, slow speeds and just overall poor performance from my ethernet card.

Looking into the issue further I noticed that the driver installed for my NIC is &quot;driver=r8169&quot;, but the actual NIC card is &quot;product: RTL8111/8168B PCI Express Gigabit Ethernet controller&quot; which I think pretty much says I should be running the 8168 driver.

When I run lsmod I only see &quot;r8169 &quot; installed.

How do I go about getting and installing the r8168 driver? I am pretty sure I just need to install this driver and then blacklist the r8169 in blacklist.conf. Any clarification would be great.

Any help would be greatly appreciated.

Thank You,

Spec36

---

### Post by spec36 on 2011-07-29
solved this by downloading the r8168 driver from the realtek website, removing the r8169 driver and installing the r8168 driver.

---

### Post by snowmanman on 2011-09-10
> **spec36 said:**
> solved this by downloading the r8168 driver from the realtek website, removing the r8169 driver and installing the r8168 driver.

Hey, where did you get this driver and how did you remove the old one? I'm having the exact same problem with this adapter.

---

### Post by snowmanman on 2011-09-10
Never mind, anyone else having this problem can go [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false") and download the Linux driver. The readme will guide the installation.

---

