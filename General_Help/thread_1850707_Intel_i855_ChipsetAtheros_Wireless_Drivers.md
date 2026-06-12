---
title: "Intel i855 Chipset/Atheros Wireless Drivers"
date: 2011-09-27
forum: General Help
---

### Post by bestbets1 on 2011-09-27
Hi All,

Where could I find the drivers for the Intel i855 chipset for my 2003 laptop? I've tried searching Intel's website, but there are no download options. 

I was also looking for the drivers for Atheros wireless. I know I can use MadWiFi's offering, but I have absolutely no idea how to compile/install it.

Thanks in Advance

---

### Post by gandaran on 2011-09-27
> **bestbets1 said:**
> Hi All,

Where could I find the drivers for the Intel i855 chipset for my 2003 laptop? I've tried searching Intel's website, but there are no download options. 

I was also looking for the drivers for Atheros wireless. I know I can use MadWiFi's offering, but I have absolutely no idea how to compile/install it.

Thanks in Advance
Intel and atheros drivers are already built in on the linux kernel, you don't have to install any, wireless and video should just work without you doing anything but if you are experiencing any video or wireless problems please post the details and which ubuntu release you have plus atheros chipset model info.
```
lspci
```
paste the output here.

---

### Post by bestbets1 on 2011-09-27
Ok. The reason I needed the Intel drivers was because of some graphics/ACPI issues. Thats fixed, and seems to have fixed the Wireless communication issue also!!! 

For those who are having issue with either, update Linux via some other method, download the Linux drivers and if you have Atheros integrated wireless on your computer, then, it should work!!!

---

### Post by mörgæs on 2011-09-27
Good, then please mark the thread 'solved'.

---

