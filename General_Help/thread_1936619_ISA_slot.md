---
title: "ISA slot"
date: 2012-03-06
forum: General Help
---

### Post by GS maran on 2012-03-06
Dear all
            
            I have installed Ubuntu in my computer and dos emu for free dos
    as i want use cam software  this cam software has hardware board which  is inserted in ISA slot
and  hardware dongle in the printer port..

i have worked this cam software in free dos it was working fine  only issue was the using flash drive.
so i planed  to use Ubuntu.
  
  now the issue  with the Ubuntu  is i cant  detected   software board   in the ISA slot.
 
i hope i can get solution 

thanks in advance
:)

---

### Post by maniandram on 2012-03-06
You can try running DOS in a virtual machine to run your camera program.

---

### Post by GS maran on 2012-03-08
After installing virtual machine  an error message is displayed
(could not detect a default hypervisor )
any suggestion which version of virtual machine is best.

my actual problem is to run CNC machine software  (cam)   which inserted in ISA slot 
in Ubuntu i cant use ISA slot. 

with regards
Maran

---

### Post by dcstar on 2012-03-08
> **GS maran said:**
> Dear all
            
I have installed Ubuntu in my computer and dos emu for free dos as i want use cam software  this cam software has hardware board which  is inserted in ISA slot and  hardware dongle in the printer port..

i have worked this cam software in free dos it was working fine only issue was the using flash drive.
so i planed  to use Ubuntu.
.........

DOS is DOS, it accesses the (ancient ISA) hardware directly. Ubuntu is **not** DOS and any emulator has no guarantee that it will access hardware resources like this.

---

### Post by maniandram on 2012-03-09
> **GS maran said:**
> After installing virtual machine  an error message is displayed
(could not detect a default hypervisor )
any suggestion which version of virtual machine is best.

my actual problem is to run CNC machine software  (cam)   which inserted in ISA slot 
in Ubuntu i cant use ISA slot. 

with regards
Maran

Try virtualbox(virtualbox.org).
Its has a nice GUI and it is free,and open-source.
It is available in the Ubuntu reprositeries.

---

