---
title: "Wireless/VMware"
date: 2012-06-23
forum: General Help
---

### Post by dbyers59 on 2012-06-23
How do I get Ubuntu to recognize the wireless network at home using VMware?

---

### Post by holycow131415 on 2012-06-24
VMware is a virtual machine. Your host will connect to the wireless network, and the VM will have a virtual wired connection based off your host connection. So you wont and cant because VMs only use "wired' and set up virtual hardware for wired.

---

### Post by dbyers59 on 2012-06-24
Ok. So how do i get Ubuntu to connect to the Internet? Do I need to hard wire the computer?

---

### Post by nipunshakya on 2012-06-24
Yepp... there is a need of an ethernet cable mate...

---

### Post by wildmanne39 on 2012-06-24
Hi, if your host has internet your guest should have internet and in the host it can be a wireless setup but it will only be seen as a wired connection in the guest.

If you have internet to the host and not the guest then check your internet settings in the settings of vmware before you start your guest, mine looks like this but I use virtualbax.
Thanks

---

### Post by dbyers59 on 2012-06-26
Thanks to all replies. They were very informative. I opened the VM and clicked on the Ubuntu the other day and the Internet connection was active. Don't know what happened but I have full access now.

---

### Post by nipunshakya on 2012-06-26
Hmm... thats strange.. have u tried to find out what went wrong?

---

### Post by wildmanne39 on 2012-06-26
Hi, that is great just look at your settings in case they ever get changed you will know what they should look like with a working connection, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

