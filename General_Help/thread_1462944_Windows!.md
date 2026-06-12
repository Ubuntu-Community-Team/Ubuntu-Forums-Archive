---
title: "Windows!"
date: 2010-04-26
forum: General Help
---

### Post by Colo2 on 2010-04-26
Hello.

I currently have Ubuntu installed on my laptop.

I have it set up the way I like it. However, I want Windows on here too...

the thing is, I dont want to have to format if possible, I know that you need to install windows before Ubuntu. I have ubuntu all set up how I Like it and it would be a shame to have to wipe it... 

Is there any way at all I can install windows along side it without having to do a complete format?

thhanks

---

### Post by Ein2015 on 2010-04-26
> **Colo2 said:**
> Hello.

I currently have Ubuntu installed on my laptop.

I have it set up the way I like it. However, I want Windows on here too...

the thing is, I dont want to have to format if possible, I know that you need to install windows before Ubuntu. I have ubuntu all set up how I Like it and it would be a shame to have to wipe it... 

Is there any way at all I can install windows along side it without having to do a complete format?

thhanks

[https://help.ubuntu.com/community/WindowsDualBoot#Installing Windows After Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing Windows After Ubuntu)

Alternatively, use a virtual machine (check out virtualbox) if you don't need to do a lot of heavy lifting with Windows.

---

### Post by Megaptera on 2010-04-26
Useful guide here for dual-booting Windows/Linux with Linux installed first:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by lockalidiot on 2010-04-26
First, make sure you have an ubuntu live cd around.

Get gparted, resize your ubuntu partition. Format the new unallocated to be an NTFS file system. Then insert the windows cd, install windows on the ntfs partition. Once ready, insert ubuntu live-cd, go to "test without installing anything" thingy, mount your ubuntu partition and reinstall grub/grub2 depending on which you have.

---

