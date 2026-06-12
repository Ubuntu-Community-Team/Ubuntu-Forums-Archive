---
title: "How to copy printer configuration from ubuntu to kubuntu"
date: 2010-08-02
forum: General Help
---

### Post by tarekeldeeb on 2010-08-02
Hello all,

I have 2 PCs, 1 ubuntu and another kubuntu. Both are lucid 10.04.
I have a network printer. 

On ubuntu I cannot find my printer model listed, but ubuntu gives the option to search for drivers  online. This method succeeds.

On kubuntu there's no such option. I cannot install my printer driver.

Can I manually copy the printer driver/configuration to kubuntu?

Thanks in advance,

Tarek

---

### Post by bschelst on 2010-08-05
what kind of printer do you have?

---

### Post by tarekeldeeb on 2010-08-06
> **bschelst said:**
> what kind of printer do you have?

as I said, it's a network printer. Vendor NRG. Model: not  listed, but found when doing the ubuntu online search.

I don't think which printer I have is the problem. I am asking about which files to be copied to kubuntu.

Many thanks

---

### Post by gasparov on 2010-08-06
> **tarekeldeeb said:**
> 
I don't think which printer I have is the problem. I am asking about which files to be copied to kubuntu.

Many thanks

yes but if you find the driver for your printer you are done in kubuntu as well. 

If you use cups you can try by copying /etc/cups from ubuntu to kubuntu , in that directory you can find ppds and the printer definitions, make a backup of target directory before.

If one of the 2 computer acts as a printer server (lets say ubuntu) you can connect from kubuntu to the cups server.

---

### Post by apmcd47 on 2010-08-06
Just a thought: Can you share the printer from Ubuntu to Kubuntu and see if it copies the driver over? You could then try connecting directly to the printer and see if it uses the now existing driver. 

Never done this myself, it's just a stab in the dark.

Andrew

---

