---
title: "Virtual Machine Question"
date: 2010-08-02
forum: General Help
---

### Post by OxentroT on 2010-08-02
I am wanting to do some experimenting with some virtual machines as well as get to know some of the other distros out there.  
  
I was just wondering if I were to construct a VM on VirtualBox, and then sometime down the road uninstall it when finished. What would be the best way to go about uninstalling as far as completely restoring the space and partition that was being used back to my main partition? 

Does Virtualbox automatically do that for you?:-k

---

### Post by howefield on 2010-08-02
> **OxentroT said:**
> What would be the best way to go about uninstalling as far as completely restoring the space and partition that was being used back to my main partition? :-k

Your VM wouldn't be using a partition as such, it would be a file in your ~/.virtualbox directory. Delete that .vdi file and it is gone.. kaput.

Use Synaptic to completely remove the Virtualbox application and it would be gone also.

---

### Post by Maverick_Meerkat on 2010-08-02
Greetings,

Howefield is correct. Virtulbox creates a virtual disk not any real partition. When VBox is removed so is the virtual disk. All previously occupied disk space is returned.

---

### Post by OxentroT on 2010-08-02
Thank You both for your answers to my question. :p

---

### Post by P4man on 2010-08-02
I dont think uninstalling virtualbox through synaptic will remove the virtual harddisks. I would **hope** it doesnt, even if you select "completely remove". It should remove all program files and settings, but not the VMs. That like removing all your spreadsheets if you uninstall openoffice.

---

### Post by OxentroT on 2010-08-08
> P4man Re: Virtual Machine Question
I dont think uninstalling virtualbox through synaptic will remove the virtual harddisks. I would hope it doesnt, even if you select "completely remove". It should remove all program files and settings, but not the VMs. That like removing all your spreadsheets if you uninstall openoffice.

I found out by by chance as the first VBox I installed was an OSE version (wrong one) So I completely removed it and --purge then proceeded to d/l and install the Full Oracle vision and my .VDI were still there

---

### Post by bodhi.zazen on 2010-08-08
> **P4man said:**
> I dont think uninstalling virtualbox through synaptic will remove the virtual harddisks. I would **hope** it doesnt, even if you select "completely remove". It should remove all program files and settings, but not the VMs. That like removing all your spreadsheets if you uninstall openoffice.


That is correct. completely removing or purging packages removes configuration files from the system directories (typically /etc) but NOT your $HOME directory.

---

