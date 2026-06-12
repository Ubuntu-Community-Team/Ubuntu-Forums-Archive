---
title: "VM Setup for Ubuntu 9.04"
date: 2009-09-09
forum: General Help
---

### Post by portalhometech on 2009-09-09
Hello all,

I am nearly a expert at windoze (Systems Engineer for 9yrs) however i am still growing in the Linux world which brings me to you. I choose Ubuntu as my new home desktop OS. I am stuck using Zune software for my Zune which makes me a slave to Windoze. I installed sun virtualbox and setup a windows XP VM. The VM will not see the real hardware graphics card so i cannot run games or the like. I did some research and the VM in Virtualbox will never see the real hardware. Am i using the correct software? Is there better? Does anyone else have a similar setup with a fully functional Win XP VM on Ubuntu? Any advice and help is much appreciated.

P4 3.06, 2GB RAM, Nvidia FX5600 with 256MB
host: Ubuntu 9.04 fully updated as last night (9/8) running Virtualbox
guest: Windowx XP SP3 32 bit

---

### Post by XCan on 2009-09-09
The newer VirtualBox should have some capabilities for hardware acceleration. But in general, I don't think VMs are designed to run games and stuff as a priority. I play games from time to time through Wine, which (am I lucky?) has worked really good so far. But then, the games I've played aren't the newest either.

Bottom line in all cases are, if you're a hardcore gamer, stick to Windows.

---

### Post by portalhometech on 2009-09-16
Thanks for the response.

A friend told me about a Virtualbox tools download similar to the tools you install for VMWARE. Is there any benefit of said tools?

---

### Post by XCan on 2009-09-16
What kind of tools are you referring to? I think Vbox can read from Vmware containers.

---

### Post by portalhometech on 2009-09-16
I was told they were possibly extra driver support, performance enhancing things, etc.

---

### Post by bodhi.zazen on 2009-09-16
You can install the VirtualBox Additions.

Although the Additions are better, probably not sufficient for gaming.

---

### Post by portalhometech on 2009-09-17
i couldnt find it at the virtualbox website. Is there a PPA for it or can i find it in Synaptic? ( i already added the PPA for virtualbox)

non related question. have yall used linux mint? thoughts?

---

### Post by bodhi.zazen on 2009-09-17
> **portalhometech said:**
> i couldnt find it at the virtualbox website. Is there a PPA for it or can i find it in Synaptic? ( i already added the PPA for virtualbox)

non related question. have yall used linux mint? thoughts?

[http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/](http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/)

---

### Post by portalhometech on 2009-09-18
Thank you. ill check it out when i get home and see if that helps me out with my problem.

---

