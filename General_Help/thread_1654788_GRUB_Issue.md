---
title: "GRUB Issue"
date: 2010-12-28
forum: General Help
---

### Post by porkchop_001 on 2010-12-28
Hi Guys,

Attached below is a screenshot of my boot-screen. Is there a reason why I have so many options? Is there a way I can simply have a Ubuntu option and a Windows option instead of the array of choices I currently have? Thanks :)

[[IMG]http://img209.imageshack.us/img209/5541/img00172201012291233res.th.jpg[/IMG]](http://img209.imageshack.us/i/img00172201012291233res.jpg/)

---

### Post by mikewhatever on 2010-12-28
There wasn't a screenshot at the time of replying, but an educated guess tells me that you have too many Linux kernels.
Ubuntu Tweak is a third party application with a nice GUI that can remove them. You can also remove the older kernels using the Synaptic package manager. See the howto below for more info.
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by porkchop_001 on 2010-12-29
Hmm there should be a link.

See if this works: [http://img209.imageshack.us/i/img00172201012291233res.jpg/](http://img209.imageshack.us/i/img00172201012291233res.jpg/)

I downloaded and installed Ubuntu Tweaks and cleaned the kernels. They're still showing up through. Any ideas?

---

### Post by dcstar on 2010-12-29
> **porkchop_001 said:**
> Hi Guys,

Attached below is a screenshot of my boot-screen. Is there a reason why I have so many options? Is there a way I can simply have a Ubuntu option and a Windows option instead of the array of choices I currently have? Thanks :)


Install Burg and you can:

[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

---

### Post by Idefix82 on 2010-12-29
Just a small explanation: when Ubuntu installs a new kernel, it keeps the old ones for safety reasons. The new kernel might break something (it happens rarely, but it happens) to a point at which you wouldn't be able to boot into Ubuntu at all. Then, you can always boot up the old kernel and try repairing things or continue working with the old kernel and wait for the next kernel release. The recovery mode that comes with each kernel is also a safety feature.

I always keep one old kernel, just for safety reasons, but you can certainly go ahead and delete the third one in the list. You can also manipulate your /boot/grub/menu.lst to get rid of unwanted options, while keeping the kernels on the drive. For example, you can delete the recovery mode option for the old kernel that you keep from the menu (don't actually delete the text, just comment it out). You can also change the order of the menu options, to have the latest Linux kernel and Windows at the top and the rest below it.

---

### Post by porkchop_001 on 2010-12-29
> **dcstar said:**
> Install Burg and you can:

[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

I have Burg already installed - that screen shot is Burg. I don't see any such option that allows me to remove old kernels. Any ideas?

---

### Post by wilee-nilee on 2010-12-29
In a terminal
sudo update-burg

---

### Post by decrepit on 2010-12-29
> **Idefix82 said:**
> <<<<<<< You can also manipulate your /boot/grub/menu.lst >>>>>>> it.

I don't think 10.10 with grub2 has a menu.lst,I can't find it on my 10.4 anyway.

---

### Post by Idefix82 on 2010-12-29
You can always just uninstall the old kernels through synaptic. Just search for 2.6.35-22 and remove the kernel packages. They will then also be deleted from the menu.

---

### Post by porkchop_001 on 2010-12-29
> **wilee-nilee said:**
> In a terminal
sudo update-burg

Success! This makes perfect sense. I cleaned the kernels using Ubuntu Tweak, then they didn't show up in the synaptic list so this was the hidden key. Thanks heaps all! All I need to do now is hode my recovery option and I'm all set. Thanks :D

---

