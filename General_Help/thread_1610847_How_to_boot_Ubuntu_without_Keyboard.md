---
title: "How to boot Ubuntu without Keyboard"
date: 2010-11-01
forum: General Help
---

### Post by RM777 on 2010-11-01
Hi

I have searched this forum before posting & can only see threads about problems of keyboards not being seen by Ubuntu.

My problem is different. I have a headless server running 9.10. it has no GUI & is CLI only. The annoying thing is that I cant boot it without a keyboard. I have seen other sites threads saying turn of 'apm' in BIOS? But I dont know if that will affect other things.

I use SSH only to manage this box either from home/work so again keyboard is not needed in any capacity.

Please help & thanks for reading this...

---

### Post by KeLa on 2010-11-01
So, if you can't start your pc without keyboard then you can do as i have done.
Take one keyboard and open it and there is a tiny board with some chips inside the
keyboard. Take that tiny board and the keyboards connection wire and use eg. duck tape
to pack it and then connect that blob to the pc and it will be satisfied because it sees a "keyboard" there.

---

### Post by philinux on 2010-11-01
> **RM777 said:**
> Hi

I have searched this forum before posting & can only see threads about problems of keyboards not being seen by Ubuntu.

My problem is different. I have a headless server running 9.10. it has no GUI & is CLI only. The annoying thing is that I cant boot it without a keyboard. I have seen other sites threads saying turn of 'apm' in BIOS? But I dont know if that will affect other things.

I use SSH only to manage this box either from home/work so again keyboard is not needed in any capacity.

Please help & thanks for reading this...

Check in the bios of the machine. Halt On or other setting.

---

### Post by RM777 on 2010-11-01
> **philinux said:**
> Check in the bios of the machine. Halt On or other setting.

So I assume I should change to 'Halt Off'???

Thx

---

### Post by mtinman on 2010-11-08
I'm having the same problem, only the bios on my "headless" server doesn't support "Halt On" settings - any suggestions besides attaching an old keyboard to the "headless" server?

Thanks in Advance...

---

