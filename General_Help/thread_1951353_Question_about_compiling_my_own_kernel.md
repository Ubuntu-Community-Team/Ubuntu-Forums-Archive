---
title: "Question about compiling my own kernel"
date: 2012-04-02
forum: General Help
---

### Post by Hungry Man on 2012-04-02
If I compile a kernel and replace the one currently on my machine will I still continue to get patches from Ubuntu's update manager?

What if I were to use something from this?
[http://kernelsec.cr0.org/](http://kernelsec.cr0.org/)

---

### Post by raja.genupula on 2012-04-02
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Hungry Man on 2012-04-02
Doesn't answer my question. It says I don't get support - that's vague.

---

### Post by Cheesemill on 2012-04-02
You will continue to get updates for all of the packages installed on your system, including updates for the stock Ubuntu kernels. These kernel updates will force an 'update-grub' which will add the new Ubuntu kernels to the top of your boot menu.

You can get around this by removing the Ubuntu kernels from your system and only having the custom one which *will not* receive any updates unless you manually compile a new version.

Looking at the website you linked to though, this doesn't involve you compiling your own kernel, it is simply a repo which you add to your system which allows for downloading and updating of the custom kernel with the normal package manager tools.

Bear in mind though that he states that the repo is only supported for Ubuntu version 8.04, so if you are using a later version of Ubuntu you will have to look somewhere else.

---

### Post by Hungry Man on 2012-04-02
I see, so if a patch were released I would have to recompile the kernel or could I just patch it myself?

Yeah, the site I linked is precompiled hardened kernels. 

Thanks - already learning something.

---

### Post by Cheesemill on 2012-04-02
> **Hungry Man said:**
> I see, so if a patch were released I would have to recompile the kernel or could I just patch it myself?

Yeah, the site I linked is precompiled hardened kernels. 

Thanks - already learning something.

Every time you apply a patch it is always referring to patching the source code.

So yes, you could patch the kernel yourself but you would only be patching the source code so you would need to recompile as well after applying the patch.

Your best and easiest route would probably be to find a current repository that contains patched kernels for whatever version of Ubuntu that you are currently using.

---

