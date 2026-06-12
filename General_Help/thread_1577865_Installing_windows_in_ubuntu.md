---
title: "Installing windows in ubuntu"
date: 2010-09-19
forum: General Help
---

### Post by orphenlegato on 2010-09-19
I have a unique problem. I have a laptop with a busted screen and no way to boot directly to the external monitor with ubuntu installed and the thing is I want to install windows 7. Anybody know of anyway to do this without being able to see the screen before the os loads?

So far I have messed around with installing windows 7 in vm box and trying to turn the vdi file into a valid partition and also tried installing it with wine but it couldn't find the temp folder to copy the install files.

---

### Post by snowpine on 2010-09-19
Welcome to the forums! However, this is not really an Ubuntu question, perhaps you will get a better answer from the Microsoft forums.

What you need to do is figure out the key your BIOS uses to get a boot menu (usually Esc or one of the Fn keys) so that you can boot from your Windows install DVD. This takes place before the Ubuntu GRUB bootloader, so nothing in Ubuntu can control the process.

---

### Post by orphenlegato on 2010-09-19
Thanks for the response. The fn key method does not seem to work as it will not switch the monitor output and only thing that shows up on my monitor is Ubuntu. Any windows install I will make would have to be from within Ubuntu. If this is a question for a Windows forum I am sorry but I thought I could get the most help here.

---

### Post by snowpine on 2010-09-19
If your computer's BIOS will not allow you to boot the Windows installer, then I would recommend installing Windows in a virtual machine inside of Ubuntu.

---

### Post by ajhunt on 2010-09-19
If I'm reading your problem right, it sounds as though you're not getting to the boot selection menu quick enough - do you know for sure what the thay key is? If you do, then keep tapping the key (immediately from pressing the power button) until you get some beeping. If you're not sure then perhaps post back the brand/model.

As for the monitor output, I'm sure the fn key for monitor output is bios led rather than the os so concentrate first on getting to the boot menu first (even if you can't see it) because you won't get to cycle the monitor function quickly enough before the post screen passes.

---

### Post by orphenlegato on 2010-09-19
Thanks everyone but I figured it out. I installed windows in VM box then wrote down all keystrokes it used then used gparted to erase the partitions once I did that I was just down to installing only using what I wrote down as a guide.

---

