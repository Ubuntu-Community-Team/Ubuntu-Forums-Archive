---
title: "Is the laptop too hot?"
date: 2010-12-08
forum: General Help
---

### Post by na5h on 2010-12-08
Hi! My friend has a Fujitsu Siemens Amilo Pa 3553 notebook running Ubuntu Maverick. Specifications: 2GHz AMD Turion X2 processor, 4GB RAM and ATI Mobility Radeon HD 3400-series graphics card. Proprietary FGLRX-drivers are in use, and desktop effects are enabled.  

This is the output I get from the "sensors" command at the moment. Computer has been on for a while and I'm doing some normal surfing with Firefox: 

acpitz-virtual-0
Adapter: Virtual device
temp1:       +56.0°C  (crit = +100.0°C)                  
temp2:       +56.0°C  (crit = +100.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +58.9°C  (high = +70.0°C)  

I tried to do some multi-tasking in order to make the computer work a little bit more (opened a few applications and played around with them all):
The temp1 at the bottom of the list (+58,9) got as high as +79.5 at some point. I just tried doing the same multi-tasking things over again, but all the temperatures seem to have been stabilized and stay around +56 degrees (fortunately).

Anyway, is this laptop too hot? I'm especially concerned about the PCI "adapter temp1" that went far over +70 at some point! :confused:

---

### Post by Hari5g900 on 2012-06-12
Well, What did you feel when you touched it? I mean, do you think it is too hot???

---

### Post by Hari5g900 on 2012-06-12
When I did this, I got this-

acpitz-virtual-0
Adapter: Virtual device
temp1:       +60.0°C  (crit = +256.0°C)                  
temp2:       +61.0°C  (crit = +108.0°C)                  
temp3:       +50.0°C  (crit = +105.0°C)                  
temp4:       +33.4°C  (crit = +108.0°C)                  
temp5:       +80.0°C  (crit = +110.0°C)                  

I am running ubuntu 10.04
My laptop is an HP Compaq 6710s

---

### Post by whatthefunk on 2012-06-12
According to the site below, critical temp for that processor is 100 C.  79.5 is getting a bit high, but since the temperature went down it means that the laptop is working correctly.

---

### Post by Hari5g900 on 2012-06-15
> **whatthefunk said:**
> According to the site below, critical temp for that processor is 100 C.  79.5 is getting a bit high, but since the temperature went down it means that the laptop is working correctly.
whatthefunk, you said according to the site below. WHAT SITE BELOW?????

---

### Post by whatthefunk on 2012-06-15
> **Hari5g900 said:**
> whatthefunk, you said according to the site below. WHAT SITE BELOW?????

Good question!  There was a link there before!

EDIT:  Think it was this one:
[http://www.cpu-world.com/CPUs/K8/AMD-Turion%20X2%20Ultra%20ZM-84%20-%20TMZM84DAM23GG.html](http://www.cpu-world.com/CPUs/K8/AMD-Turion%20X2%20Ultra%20ZM-84%20-%20TMZM84DAM23GG.html)

---

### Post by Hari5g900 on 2012-06-26
whatthefunk, it says maximum operating temperature. It does not mean that the temperature of the laptop has reached it's limit,does it? It means the temperature of the place where you operate it, don't you think?

---

### Post by bencouve on 2012-06-26
I have had toptops getting hot in the past. In fact my last laptop used to get too hot to the touch. I used to put a plate under it with ice in the plate, it worked ;) for a while, until the laptop decided to stop working.

I have found with my current tap top that it was starting to get hot with windows 7, so I installed Ubuntu 12.04. Now the temp is ok.

I check to see if it is hot to the touch and if too hot then I switch off.  You can buy external fans for this.

---

### Post by youknowme on 2012-06-26
> **na5h said:**
> Hi! My friend has a Fujitsu Siemens Amilo Pa 3553 notebook running Ubuntu Maverick. Specifications: 2GHz AMD Turion X2 processor, 4GB RAM and ATI Mobility Radeon HD 3400-series graphics card. Proprietary FGLRX-drivers are in use, and desktop effects are enabled.  

This is the output I get from the "sensors" command at the moment. Computer has been on for a while and I'm doing some normal surfing with Firefox: 

acpitz-virtual-0
Adapter: Virtual device
temp1:       +56.0°C  (crit = +100.0°C)                  
temp2:       +56.0°C  (crit = +100.0°C)                  

k10temp-pci-00c3https://wiki.ubuntu.com/DebuggingACPI
Adapter: PCI adapter
temp1:       +58.9°C  (high = +70.0°C)  

I tried to do some multi-tasking in order to make the computer work a little bit more (opened a few applications and played around with them all):
The temp1 at the bottom of the list (+58,9) got as high as +79.5 at some point. I just tried doing the same multi-tasking things over again, but all the temperatures seem to have been stabilized and stay around +56 degrees (fortunately).

Anyway, is this laptop too hot? I'm especially concerned about the PCI "adapter temp1" that went far over +70 at some point! :confused:

hummm - do you hear the fan working??
see [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

---

### Post by Elfy on 2012-06-26
Closed - please do not wake up old and unamswered threads with requests for support.

---

