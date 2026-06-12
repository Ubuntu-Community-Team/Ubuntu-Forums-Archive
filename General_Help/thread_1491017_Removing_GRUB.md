---
title: "Removing GRUB?"
date: 2010-05-23
forum: General Help
---

### Post by Shadow of Chaos on 2010-05-23
First, to say, while I like Ubuntu, I dislike grub, and prefer to use a live USB for the portability.

That said, I want to remove GRUB on my main laptop (Running Windows 7) from my WUBI installs. 

Doing some searched, I found that I should run something like fdisk /mbr or the like to get rid of it (Or at least mask it) in a command prompt, however, these instructions seem based more on the idea that Windows in inaccessible, which isn't the case for me.

So, basically, will /mbr work in my case, and is it safe? I can just ignore it, but it is somewhat annoying...

---

### Post by BoneKracker on 2010-05-23
I think Windows has a utility on the install media to "repair MBR" or something like that.

---

### Post by wilee-nilee on 2010-05-23
l

---

### Post by Jakiejake on 2010-05-23
You can't uninstall the GRUB since it manages the OS
But you can try "Startup Manager"

---

### Post by wilee-nilee on 2010-05-23
missed the wubi part.

---

### Post by Jakiejake on 2010-05-23
> **wilee-nilee said:**
> missed the wubi part.

Who? Me?

---

### Post by wilee-nilee on 2010-05-23
> **Jakiejake said:**
> Who? Me?
 
No me I quoted myself when I was trying to remove the commands for reinstalling W7 to the MBR, I read to quickly and thought the OP was wanting to remove a real dual boot and just run Windows, sorry about that. ;)

---

### Post by Jakiejake on 2010-05-24
> **wilee-nilee said:**
> No me I quoted myself when I was trying to remove the commands for reinstalling W7 to the MBR, I read to quickly and thought the OP was wanting to remove a real dual boot and just run Windows, sorry about that. ;)

LOL Thats Ok

---

