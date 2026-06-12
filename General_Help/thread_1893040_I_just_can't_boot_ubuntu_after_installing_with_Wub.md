---
title: "I just can't boot ubuntu after installing with Wubi."
date: 2011-12-09
forum: General Help
---

### Post by Krunch007 on 2011-12-09
Hello.

I would firstly like to thank you for reading the incoming wall of text.

A while ago I installed Kubuntu when I already had a dual boot with Windows XP and Windows 7, which kinda made it a trio boot or something. Because of doing so, a lot of stuff happened in the following days that either rendered Windows 7 unusable, or Windows XP, or all of them. Fortunately, I've been able to recover my installation of Windows 7, then use EasyBCD to make all the OS's bootable once more. However, I have recently been forced to reformat the partition that Windows XP and Kubuntu was on, erasing them both. I've tried installing Ubuntu with Wubi now, the same method I have used the last time.

Unfortunately, the Ubuntu install didn't show at boot menu, so naturally, after I booted Windows 7(now labeled "recovered") I tried to fix the boot with EasyBCD(I picked "Wubi" under the Linux/BCD tab in Add Item). That did work, since I can now see "Ubuntu" at boot menu, but when I select it, some command line is displayed and it's something like this:

grub>

I've tried pressing TAB to see the commands, then tried using command "boot", but it didn't work, saying something about kernel needing to be loaded before booting...

Anyway, I'd be very grateful if you could help me boot into Ubuntu. Thanks in advance.

---

### Post by Rubi1200 on 2011-12-09
Hi and welcome to the forums :)

Please post the results of the boot info script; there is a link at the bottom of my post with instructions.

Thanks.

---

### Post by Krunch007 on 2011-12-09
Thank you for replying. I think there might be a problem though. To use boot info script it says I have to boot into any Linux based OS. That's the problem. I can't boot. Do you think I could access that file through that GRUB command line?

---

### Post by Rubi1200 on 2011-12-09
It also says you can perform the required commands from a live environment.

This means you need to get hold of or create a LiveCD/USB and boot the computer with it, choosing to try not install.

Regardless of the fact that you have a Wubi install, a LiveCD is always useful as a means of booting a computer that requires some kind of repair or diagnostic work to be done.

This link shows you how to create a LiveCD:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by Krunch007 on 2011-12-13
Well, after a few tries I decided to give up and reinstall. Since I reinstalled Ubuntu around 6 times, I chose to install Xubuntu instead. Surprise! The MBR record(I checked it before I restarted) was looking fine, and after the restart it worked! In fact, I'm writing this post using Firefox in Xubuntu. Thank you again for all your help.

---

