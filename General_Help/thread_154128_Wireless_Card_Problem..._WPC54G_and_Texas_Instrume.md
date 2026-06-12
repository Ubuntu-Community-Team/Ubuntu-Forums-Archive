---
title: "Wireless Card Problem... WPC54G and Texas Instruments ACX100/111 Chipsets"
date: 2006-04-02
forum: General Help
---

### Post by lemix on 2006-04-02
I have a integrated wireless Texas instruments ACX111 chipset and i also have the Linksys WPC54G wireless card in an alienware laptop running ubuntu.

DSMEG requests that you go to this page,  [http://acx100.sf.net](http://acx100.sf.net), for firmware/driver installation instructions for this chipset.

I have followed these instructions and produce the following errors.

## When testing and inserting into kernal step i remove the old drivers...
acx                   128648  0
firmware_class          9472  1 acx
usbcore               104188  5 acx,usbhid,ehci_hcd,ohci_hcd
> sudo modprobe -r acx


##Then i run
 > sudo insmod ./acx.ko

which produces the following error....
insmod: error inserting './acx.ko': -1 Unknown symbol in module

since this is only the testing stage i continue and find that my '*wlan0*' Device is not listed in iwconfig. in the end nothing works.

](*,) 
I have also tryed to use ndiswrapper and ndisgtk from the repos to manually install the linksys lsbcmnds.inf driver to get that card up and running. That produces a *Hardware Present: No* Error.

Anyone know the solution to my problem?

---

