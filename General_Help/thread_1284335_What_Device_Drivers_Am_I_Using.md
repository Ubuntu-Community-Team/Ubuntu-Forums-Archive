---
title: "What Device Drivers Am I Using?"
date: 2009-10-06
forum: General Help
---

### Post by Levy1234 on 2009-10-06
Is there a way to find information about what device drivers are being used in ubuntu jaunty?  Under system > hardware drivers they only list proprietary drivers.  I installed a program called "device manager" but it   only has hardware information and no driver info.  I did a search of  this forum and on google and did not come up with anything.  Help would be appreciated.  Levy

---

### Post by CatKiller on 2009-10-06
> **Levy1234 said:**
>  Under system > hardware drivers they only list proprietary drivers.

That's what that tool is for.

Free drivers are generally provided by the kernel and don't need to be worried about.

What was it that you wanted to know?

---

### Post by spiderbatdad on 2009-10-06
My understanding is for the most part, linux loads drivers into the kernel at boot time. These are called modules. So more commonly drivers are called modules in linux. to see what modules are loaded and in use on your system run the following command in your terminal
```
lsmod
```as in list modules.

---

### Post by karlson on 2009-10-06
> **Levy1234 said:**
> Is there a way to find information about what device drivers are being used in ubuntu jaunty?  Under system > hardware drivers they only list proprietary drivers.  I installed a program called "device manager" but it   only has hardware information and no driver info.  I did a search of  this forum and on google and did not come up with anything.  Help would be appreciated.  Levy

I think what you are looking for is

```

lspci -vv

```

this would give you all the devices and the drivers associated with them.

---

### Post by Levy1234 on 2009-10-06
Thanks for the information.  The reason I wanted to know about the drivers is that I suspected a screen resolution problem, that no one could help me with, was due to a faulty driver for my intel mobile 4 display adaptor.  It turned out I was right about that.  I found the xorg-edgers repository which includes drivers that have not yet been put on the main repository.  It updated my drivers nicely and solved the problem.  Hmm . . . from some of the responses to my original post, it sounds like Ubuntu users do not generally have to worry much about drivers, except proprietary ones.  Coming from windows, I am used to considering problems as possibly caused by faulty or outdated drivers and am used to seeking out and installing updates.  I guess in this case, widows thinking hellped solve an Ubuntu problem!  Thanks again for the responses.  I will take a look at the   codes suggested in them.  Levy

---

