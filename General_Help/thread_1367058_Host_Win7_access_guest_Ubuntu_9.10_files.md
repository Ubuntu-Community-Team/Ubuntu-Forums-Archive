---
title: "Host Win7 access guest Ubuntu 9.10 files"
date: 2009-12-29
forum: General Help
---

### Post by escaleraroyal on 2009-12-29
Host Win7, guest Ubuntu 9.10
Will like to know how to access folders in Ubuntu from Win7. Any tutorial will be greatly appreciated.

---

### Post by Vaphell on 2009-12-29
granted, i had reverse situation (ubuntu host, xp guest) but it was quite easy to make these two see each other via network in my case.
Go to the network part of virtual machine properties and set the guest to be connected to host interface (default is NAT i think), check if the ip address is assigned by the router to the guest machine (or set it manually), ping that ip from the host to see if the host sees the guest.
The last step would be to set up samba shares or to use ssh.

---

### Post by escaleraroyal on 2009-12-29
Let me try that later on today and I let you know the results. Hopefully, your case applies to mine too.

---

### Post by escaleraroyal on 2009-12-30
> **Vaphell said:**
> granted, i had reverse situation (ubuntu host, xp guest) but it was quite easy to make these two see each other via network in my case.
Go to the network part of virtual machine properties and set the guest to be connected to host interface (default is NAT i think), check if the ip address is assigned by the router to the guest machine (or set it manually), ping that ip from the host to see if the host sees the guest.
The last step would be to set up samba shares or to use ssh.


Did you do this on Virtualbox? I'm using Virtuabox.

---

### Post by escaleraroyal on 2009-12-31
I finally was able to access my shared folder in Ubuntu guest from Win7 host. I only had to enable a 2nd network adapter in vbox.

---

