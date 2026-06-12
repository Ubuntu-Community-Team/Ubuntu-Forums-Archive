---
title: "Read EXT3 drives from Windows XP/Vista/7 - How?"
date: 2009-10-02
forum: General Help
---

### Post by Roasted on 2009-10-02
I downloaded EXT2 IFS For Windows, which I found in a search here. But when I installed it, I mapped my EXT3 Linux Drive to "Local Disk - X"

When I double click X, it says it is not formatted, would you like to format it now?

How do I go about doing this without formatting anything?

---

### Post by aktiwers on 2009-10-02
I have had this problem too. Strange thing is it worked before I rebooted first time.
I never found a solution though :(

---

### Post by cbraxton on 2009-10-02
> **Roasted said:**
> I downloaded EXT2 IFS For Windows, which I found in a search here. But when I installed it, I mapped my EXT3 Linux Drive to "Local Disk - X"

When I double click X, it says it is not formatted, would you like to format it now?

How do I go about doing this without formatting anything?

The problem is your inode size. Somewhere along the way, the default inode size changed from 128 bytes to 256 bytes. Ext2 IFS only works with 128-byte inodes.

To format a partition to be compatible, you would need to use the mkfs "-I 128" command-line option.

---

### Post by Roasted on 2009-10-03
It'd be convenient to have read/write access from Windows, but to be frank, I'm not going to format my entire install just to have Windows play nicely with it.

Anybody know of another app that might work?

---

### Post by sisco311 on 2009-10-03
[ext2fsd]("http://www.ext2fsd.com/") supports large inode size.

---

### Post by jward3010 on 2009-10-03
This has always been the problem with EXT2 IFS, and why I never bothered using it. The only option you have really is to format your Ubuntu partition with the command above, reinstall Ubuntu on the new inode sized partition and hope it plays ball when you get back into Windows. It's not worth the hassle really - create a single large NTFS drive and store your data there. The ahem..person that made the fuse driver never made it open source hence we had to rely on his development which hasn't been that forthcoming. And there's a real possiblilty for good development of such a piece of software as so many new Linux users want to still run Windows for backup and need cross access as they do the stuff they want to do.

---

