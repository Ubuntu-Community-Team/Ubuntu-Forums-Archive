---
title: "Need help with Networking two computers together"
date: 2010-10-16
forum: General Help
---

### Post by speedy45 on 2010-10-16
[FONT=Arial]I would like to know how to network a HP P1005 Laser Printer that is connect to my desktop with Windows XP SP3 Home, & as well network files & folders to watch it on Ubuntu on my laptop?[/FONT]

---

### Post by rudy.b on 2010-10-16
Hi,

A good way to set up a network between Ubuntu and Windows is using Samba.  You may want to set up your Windows machine as the server (since it has the printer connected) and then use your Ubuntu laptop as a client.  You can find more detailed setup information here: [Samba Community Documentation]("https://help.ubuntu.com/community/Samba")

---

### Post by speedy45 on 2010-10-17
> **rudy.b said:**
> Hi,

A good way to set up a network between Ubuntu and Windows is using Samba.  You may want to set up your Windows machine as the server (since it has the printer connected) and then use your Ubuntu laptop as a client.  You can find more detailed setup information here: [Samba Community Documentation]("https://help.ubuntu.com/community/Samba")


ok I try to do what this link told but my Ubuntu 9.04 won't install my printer & view my files & folders which is setup on WINXP Home SP3, so why is this happening?

Also when go to the Printing part of Ubuntu to find my printer, & I do see my Desktop PC but it can't see my printer, & also I can't see my files & folders.

---

### Post by DeMus on 2010-10-17
> **speedy45 said:**
> ok I try to do what this link told but my Ubuntu 9.04 won't install my printer & view my files & folders which is setup on WINXP Home SP3, so why is this happening?

Also when go to the Printing part of Ubuntu to find my printer, & I do see my Desktop PC but it can't see my printer, & also I can't see my files & folders.

OK, so you can see your desktop PC already. That's good, but it's only step 1.
Step 2 is sharing: in Windows you have to share the folders you want to become visible in Ubuntu. Right-click the folder and choose share.
To be able to print you also have to share the printer. Give it a short share-name so it is easy to find in Ubuntu.

---

### Post by speedy45 on 2010-10-17
> **DeMus said:**
> OK, so you can see your desktop PC already. That's good, but it's only step 1.
Step 2 is sharing: in Windows you have to share the folders you want to become visible in Ubuntu. Right-click the folder and choose share.
To be able to print you also have to share the printer. Give it a short share-name so it is easy to find in Ubuntu.

I do have Microsoft Security Essentials(Anti Virus), PC Tools Firewall Plus on my Windows XP,   that might cause this to happen, also I am checking if there any firewall that I install that is blocking it from sharing so I can see my files & folders that is sharing turn on. Well I do fix the firewall problem by uninstall it on my Ubuntu but now I don't see my files & folders. Also I found out that in order to use my Laser Jet printer, I had to connect to by usb only because my printer doesn't have wireless support at all. My problem is only my files & folders trying to share it t my Ubuntu Laptop.

---

