---
title: "Kernel"
date: 2010-01-08
forum: General Help
---

### Post by endoglastic on 2010-01-08
How do i configure the kernel to be 1000hrtz? If you can, please tell me step by step.

---

### Post by iponeverything on 2010-01-08
The speed that you CPU runs at has nothing to do with the kernel.

Also 1000 hertz is only 1 kHz.

---

### Post by HiImTye on 2010-01-08
are you talking about overclocking, underclocking, or performance options?

and yes, this has nothing to do with the kernel

---

### Post by endoglastic on 2010-01-08
Uh, yes it does, in order to run my game at 1000fps i need to adjust to kernel rate to 1000hrz to compensate, otherwise it will not run at that.

---

### Post by HiImTye on 2010-01-08
to my knowledge you will need to rebuild the kernel to change the timeslice option (CONFIG_HZ)

also changing this option will give you less topside performance but reduce your latency slightly

this isn't changing your frequency (kHz) this is just changing the rate at which the kernel updates

---

### Post by tom.swartz07 on 2010-01-08
> **endoglastic said:**
> Uh, yes it does, in order to run my game at 1000fps i need to adjust to kernel rate to 1000hrz to compensate, otherwise it will not run at that.

Dear sir,  I have a hard time believing that younwould argue with seasoned Linux users about a kernel, when you beleieve that you could get a game running on a computer at 1000 frames per second. I would be hard pressed to see if Deep Blue, a supercomputer could process and output 1000 frames per second

your monitor only refreshes 60 to 120 times per second, also. 

So, I would say that you're looking in the wrong spot, and you are in no posistion to argue

---

### Post by endoglastic on 2010-01-08
> **HiImTye said:**
> to my knowledge you will need to rebuild the kernel to change the timeslice option (CONFIG_HZ)
 
This was what i was looking for.

---

