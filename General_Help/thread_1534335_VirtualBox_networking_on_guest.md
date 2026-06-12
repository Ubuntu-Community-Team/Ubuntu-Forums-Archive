---
title: "VirtualBox networking on guest"
date: 2010-07-19
forum: General Help
---

### Post by Ready2DropWin on 2010-07-19
Another VBox Question

I have a virtual machine of windows 7, but I can seem to get the network to show up on it. I have read a help article [http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html), and it says I should beable to use NAT to connect. I have tried both ethernet and wireless on my host, and I still can't get a connecting in the guest. Am I doing something wrong?

Thanks

---

### Post by _Mark_ on 2010-07-19
Depends wjhat you mean by connection if you just want the guest to access the internet then NAT should work, sharing folders should also work with NAT

If you want the guest and host to be able to connect you would need either Host Only or Bridged depending on you're requirements

Here is a [tutorial]("http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12") to setup simple file sharing with screenshots that may help to check you're config

---

### Post by Ready2DropWin on 2010-07-19
I noticed that the tutorial shows you managing your guest account vboxusers, however when I scrolled to look for that in my groups, its not there. Do I have to manually make that group?

---

### Post by _Mark_ on 2010-07-19
Not quite sure where you are seeing this

vboxusers group should be created during the install of VBox and you need to add you're username to that group, if that group doesn't exist it is possible the install may have gone wrong somewhere

---

### Post by Ready2DropWin on 2010-07-19
I saw it here [http://maketecheasier.com/how-to-install-windows-in-ubuntu-hardy-with-virtualbox/2008/07/02](http://maketecheasier.com/how-to-install-windows-in-ubuntu-hardy-with-virtualbox/2008/07/02) I am not sure if the installing is bad, since I am using it now, and all else is good, but the networking. I got vbox from the ubuntu software center. But one thing is true that group is not listed.

---

### Post by Ready2DropWin on 2010-07-19
I am still having no luck connecting to the Internet on the guest. I was wondering do I have to install my network drivers for the guest to get it to work?

---

### Post by _Mark_ on 2010-07-19
> **Ready2DropWin said:**
> I am still having no luck connecting to the Internet on the guest. I was wondering do I have to install my network drivers for the guest to get it to work?

You could go into device manager (or whatever the Win 7 version of this is) and check to see if the network card is working ok

Have you installed the guest additions?

---

### Post by Ready2DropWin on 2010-07-20
> **_Mark_ said:**
> You could go into device manager (or whatever the Win 7 version of this is) and check to see if the network card is working ok

Have you installed the guest additions?


No I have not installed the guest yet, I know this sounds dumb, but I didn't know if I could manually add the guest account for virtual box.

---

