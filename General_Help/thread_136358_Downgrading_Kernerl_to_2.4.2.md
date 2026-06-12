---
title: "Downgrading Kernerl to 2.4.2"
date: 2006-02-25
forum: General Help
---

### Post by kuppas on 2006-02-25
Hello,
   After installing ubuntu 5.10, can I downgrade the kernel to 2.4.2 since my application needs kernel 2.4.2.  If possible, could you please write steps to follow.

Thanks,
-Kuppa

---

### Post by az on 2006-02-25
No, you can't.  Gnome and HAL use udev which is only available in 2.6 kernels.  Ubuntu will not work with older kernels.

What is it you need that only works with a five-year-old kernel?

---

### Post by Madman68 on 2006-02-25
Why would you **need** to downgrade? I don't see any reason to?

---

### Post by kuppas on 2006-02-25
I appreciate immediate reply.  Thanks very much.

I have a custom driver for one of the hardware device which works only with kernel 2.4.2.  

Is there any old ubuntu version which comes with kernel 2.4.2?

-Kuppa

---

### Post by az on 2006-02-25
[QUOTE=kuppas]
I have a custom driver for one of the hardware device which works only with kernel 2.4.2.  [/QUOTE]

Yes, but what driver?
[QUOTE=kuppas]
Is there any old ubuntu version which comes with kernel 2.4.2?

-Kuppa[/QUOTE]


No.  Debian Woody shipped with 2.4.18.  That was in 2001.  Warty (the first ubuntu release) shipped with 2.6.8.

---

### Post by kuppas on 2006-02-25
Thanks.  Video driver for old AMD Duron System.

---

### Post by sean.smithson on 2006-02-26
snip

---

### Post by az on 2006-02-26
[QUOTE=kuppas]Thanks.  Video driver for old AMD Duron System.[/QUOTE]
Please be more specific.  There very well may be a simple solution.

---

### Post by rold50 on 2006-08-10
I have similar problems too. I have PCMCIA video grabber card.

The drivers written for it works for the 2.4 kernels.

I tried installing the drivers for the current kernel version but I get errors. 

The problem lies in some of the function/member operator in the header files in 2.4 kernels is not in the latest kernel anymore.

For exxample in the pcmcia/ds.h There is a struct called dev_link_t, which had a member called release. In the current kernel, the release member has been omitted. :(

---

