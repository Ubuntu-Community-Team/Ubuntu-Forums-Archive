---
title: "parallel port enable? or test"
date: 2012-09-09
forum: General Help
---

### Post by brobob on 2012-09-09
I have a clean new install of Ubuntu 10.x that has been set up to run EMC2. My cnc driver board uses the parallel port but no where can I find away to check the port address on the Intel DG41AN mini board running a core 2 duo chip. There is no setup or address assignment in Cmos. 
I can't find such in Ubuntu but I am new to Linux.
Any help?


Brobob

---

### Post by dandnsmith on 2012-09-09
There is a section on parallel port printers [here](https://wiki.ubuntu.com/DebuggingPrintingProblems) which shows the device entries etc to look for.
I didn't understand EMC2, cnc driver, and don't know that motherboard.
I take the reference to CMOS to be what the BIOS display would show - is this a standard BIOS package (Award, AmiBios ...)?

---

### Post by brobob on 2012-09-09
Derek

Thanks for the reference I'll use it and get back to you soon. As for EMC2 it is a cnc machine tool control program, the 'controller' I mentioned is a driver board controlled by EMC2 via the parallel port controling stepper motors doing the actual work. . 

Brobob

---

### Post by Wim Sturkenboom on 2012-09-09
From the old days ;) Not sure if you're looking for this.

378 - 37F for LPT1
278 - 27F for LPT2

Best bet would be LPT1; 378 is the base address. All values hexadecimal.

---

