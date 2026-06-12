---
title: "Kernel type question (SMP?)"
date: 2006-03-02
forum: General Help
---

### Post by m.musashi on 2006-03-02
I'm struggling to get ubuntu installed and I came across this quote on another forum.

> The 2.6.11 x64_64 SMP kernel that shipped with the original Fedora Core 4 release will not boot with this board. Luckily the install also includes the non-SMP kernel, which works fine. After updating, the current 2.6.14 SMP kernel works great.

It referenced Fedora but mentioned the SMP kernel. What is that and does ubuntu use it? If so, can I use a non-SPM kernel and how would I do that?

Thanks.

---

### Post by carlosqueso on 2006-03-02
I don't believe that Ubuntu uses an SMP kernel...what problems are you having installing Ubuntu? Also, are you using the x86 or AMD64 version?

---

### Post by Ramses de Norre on 2006-03-02
Ubuntu installs the 2.6.9-386 kernel, so no smp.
You can however update to it if you want after the install.
I don't know which is the default 64bit kernel but it wont be smp neither.

---

### Post by m.musashi on 2006-03-02
I'm using the x86. I tried the 64 bit also.

I've posted the actual errors in [this](http://ubuntuforums.org/showthread.php?t=137831) thread but no real solution yet. After a bit of searching I discovered [this](http://quaggaspace.org/a8nvm/) page and it seems the BIOS on my board is the problem. There are work arounds but I'm too much of a newbie to be able to figure them out. I'm just hoping for a fixed BIOS before long but I might just try and exchange the board. My other hope is that Dapper would somehow address the issue but flight 4 won't work so I'm doubtful.

---

### Post by m.musashi on 2006-03-02
[QUOTE=Ramses de Norre]Ubuntu installs the 2.6.9-386 kernel, so no smp.
You can however update to it if you want after the install.
I don't know which is the default 64bit kernel but it wont be smp neither.[/QUOTE]
What about Dapper? I think it's the 2.6.15 kernel. Does that have SMP? Since it looks like SMP is the problem, can I install without it?

---

### Post by Ramses de Norre on 2006-03-02
I don't think any default installation kernel has smp, because all cpu's will run ok without it but some might not run with it. That's also the reason why the default kernel is 386.
I don't think smp will be the root of your problem..

---

### Post by m.musashi on 2006-03-02
[QUOTE=Ramses de Norre]I don't think any default installation kernel has smp, because all cpu's will run ok without it but some might not run with it. That's also the reason why the default kernel is 386.
I don't think smp will be the root of your problem..[/QUOTE]
Thanks. That is basically what I needed to know. I'm trying to troubleshoot my problem and I thought that might be an elelment of it. I guess not.

Thanks again.

---

