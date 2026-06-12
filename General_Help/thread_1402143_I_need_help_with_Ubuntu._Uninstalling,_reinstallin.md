---
title: "I need help with Ubuntu. Uninstalling, reinstalling, and removing the GRUB bootloader"
date: 2010-02-08
forum: General Help
---

### Post by trunkmonkeytoo on 2010-02-08
Hi! I just joined the forums, because I need to ask for help about a big problem I am having. I recently installed Ubuntu, using the Wubi installer to have it installed along with my new Windows 7. The problem is, I decided I wanted to uninstall Ubuntu temporarily, to make sure I could take it out. So I deleted the partition, and I thought that was it. But it turns out, when I turn on my computer, it still has the option to use the Ubuntu OS or the Windows 7 OS. I did some research and this turned out to be because of the GRUB bootloader that was installed into my computer when I installed Ubuntu. I would like to know how to completely wipe Ubuntu and the GRUB bootloader, along with anything else it may have done to my computer. If I can do this, then I will be reinstalling it, because I won't have to be worried like I am now that I may have permanently messed up my computer. If anyone can help me remove Ubuntu and the GRUB bootloader, I would really appreciate it. Thanks so much!

Oh, and if this works, then I have another question. When I tried to get Ubuntu on the internet, it simply did not recognize that I had a router running a wireless network at all, therefore I could not go online with it. I am currently running off of the Windows 7 partition on my computer. 

Thanks so much for your help!

---

### Post by cariboo on 2010-02-09
You need to run the Bootrec.exe tool, you must start the Windows repair utility. To do this, follow these steps:

[list=1]
[*]Put the Windows 7 DVD in the disc drive, and then start the computer.
[*]Press a key when you are prompted.
[*]Select a language, a time, a currency, a keyboard or an input method, and then click Next.
[*]Click Repair your computer.
[*]Click the operating system that you want to repair, and then click Next.
[*]In the System Recovery Options dialog box, click Command Prompt.
[*]Type Bootrec.exe, and then press ENTER
[/list]

---

### Post by trunkmonkeytoo on 2010-02-10
> **cariboo907 said:**
> You need to run the Bootrec.exe tool, you must start the Windows repair utility. To do this, follow these steps:

[LIST=1]
[*]Put the Windows 7 DVD in the disc drive, and then start the computer.
[*]Press a key when you are prompted.
[*]Select a language, a time, a currency, a keyboard or an input method, and then click Next.
[*]Click Repair your computer.
[*]Click the operating system that you want to repair, and then click Next.
[*]In the System Recovery Options dialog box, click Command Prompt.
[*]Type Bootrec.exe, and then press ENTER
[/LIST]


I've been doing all of that. But even the Ubuntu is completely removed from my computer, when I turn my computer on, it still gives me the option to boot from either windows or ubuntu. When I select Ubuntu, it says that the containing file is missing. How do I make my computer boot directly into Windows without giving me the option to boot into an Ubuntu program that isn't there?

---

