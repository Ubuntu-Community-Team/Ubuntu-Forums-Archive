---
title: "Upgrade Kernel w/ fglrx and suspend2"
date: 2006-06-08
forum: General Help
---

### Post by ehula on 2006-06-08
I am currently running Dapper on my Thinkpad T43p using the ubuntu fglrx restricted modules driver. Unfortunately suspend/sleep & resume don't work.

I would like to upgrade the kernel to 2.6.16, and include the suspend2 kernel module, and include the fglrx driver. Is there a way to do the above and use the ubuntu supplied fglrx driver so that my machine will automatically update when ubuntu updates this driver?

Could someone explain how to do this as simply as possible.

Thanks.

---

### Post by xXx 0wn3d xXx on 2006-06-08
[QUOTE=ehula]I am currently running Dapper on my Thinkpad T43p using the ubuntu fglrx restricted modules driver. Unfortunately suspend/sleep & resume don't work.

I would like to upgrade the kernel to 2.6.16, and include the suspend2 kernel module, and include the fglrx driver. Is there a way to do the above and use the ubuntu supplied fglrx driver so that my machine will automatically update when ubuntu updates this driver?

Could someone explain how to do this as simply as possible.

Thanks.[/QUOTE]
To get fglrx in your custom compilied kernel, after compiling and installing your custom kernel, install this package:
> sudo aptitude install fglrx-kernel-source
That will give you fglrx on your custom kernel.

---

### Post by ehula on 2006-06-08
[QUOTE=MasterChief1234]To get fglrx in your custom compilied kernel, after compiling and installing your custom kernel, install this package:

That will give you fglrx on your custom kernel.[/QUOTE]

Do I need to recompile the kernel, or is it loaded by naming it in my xorg.conf file?

---

### Post by xXx 0wn3d xXx on 2006-06-08
[QUOTE=ehula]Do I need to recompile the kernel, or is it loaded by naming it in my xorg.conf file?[/QUOTE]
No, if you have already compilied the kernel just run the command as I stated above. You do not need to recompile the kernel.

---

### Post by ehula on 2006-06-29
[QUOTE=xXx 0wn3d xXx]No, if you have already compilied the kernel just run the command as I stated above. You do not need to recompile the kernel.[/QUOTE]
Well, I have tried this, but it does not work. Can you think of anything else I could try?

---

