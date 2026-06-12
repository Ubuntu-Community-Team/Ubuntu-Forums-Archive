---
title: "how can i dual boot 64 bit vista and ubuntu 9.04"
date: 2009-09-20
forum: General Help
---

### Post by CarlC4 on 2009-09-20
Hi, I have just bought a toshiba with 64bit vista, and i very much would like Ubuntu, like i had on my old computer, but i have an ipod touch that i need itunes for, and there are some windows apps that i also need. So, what i'm asking is, how can i dual boot 64bit ubuntu 9.04, with an already installed 64bit vista premium?

---

### Post by Liolikas on 2009-09-20
Nothing special just install Ubuntu and be sure not to wipe all disk!!!
Just shrink main partition and use free space. Or decrease ntfs disk size in vista cp and then boot Ubuntu install and use unformatted space.
Ubuntu will detect vista and allow dual boot automatically. Maybe some /boot/grub/menu.lst configuration needed after Ubuntu install, but maybe default will be good for you.

---

### Post by 3rdalbum on 2009-09-20
Run the Ubuntu CD and double-click the Install program.

When you get to the screen that asks you whether you want to erase a partition, resize a partition, or manually specify a partition; you click on the Resize option.

**VERY IMPORTANT:** In the bar graph at the bottom of the installer window, there is a slider at the very right. You need to drag this towards the left in order to allocate disk space for Ubuntu. Allocate as much as you want. **Don't** leave it at the default setting, because this is not enough space for Ubuntu.

That's all there is to it.

---

### Post by pmeves on 2010-03-01
Yes, unless it tells you you haven't any OS installed and when Grub is built it won't add a Win entry, neither could I.

---

