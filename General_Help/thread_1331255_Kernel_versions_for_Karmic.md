---
title: "Kernel versions for Karmic"
date: 2009-11-19
forum: General Help
---

### Post by PeggySue on 2009-11-19
Hi,

I want to study Linux device drivers.  I have the appropriate text books but the examples are based around Kernel 2.6.10 and 2.6.24.  

Does anyone know of if Karmic 9.10 will work correctly with 2.6.10 or must it be 2.6.31 or higher?

Any suggestions about a good test set up working with 2.6.10 to .24 and Ubuntu would be appreciated.

---

### Post by regala on 2009-11-19
> **PeggySue said:**
> Hi,

I want to study Linux device drivers.  I have the appropriate text books but the examples are based around Kernel 2.6.10 and 2.6.24.  

Does anyone know of if Karmic 9.10 will work correctly with 2.6.10 or must it be 2.6.31 or higher?



there's a high chance you need at least 2.6.30 (if you have ext4, before 2.6.29, it's not supported as-is, and in 2.6.29, it's dangerous for important data)

anyway, you can forget 2.6.10, it's 3-4 years old. 2.6.24 was the Hardy kernel, so you can setup a machine with Hardy, which would be covered.

running the Karmic userland with Hardy kernel is another bet, it _should_ work, as upgrade between the 2 releases is supported.

However, my 2 cents, my experience with kernel development is that you should try and stick to the latest versions, not versions that old, the internal kernel APIs are constantly "moving", evolving in any case. Books are here to help you to get how the kernel works, but trying to learn from 2.6.24 source is useless. Use your books with 2.6.31 or 2.6.32-rcX, and shape what you read from them, with what you read from the source.

br,

---

### Post by PeggySue on 2009-11-19
br,

Thanks.  That's sound advice.  (I am using Ext4 in 9.10.)

I have to learn about drivers in general from the text books and also drivers in 9.10.  My plan A was to do this in two steps but I am persuaded by your arguments.  I still have a Hardy Heron partition which I can use to confirm that an error is my misunderstanding of the text books rather than a change in later kernels. 

Thanks again.

---

