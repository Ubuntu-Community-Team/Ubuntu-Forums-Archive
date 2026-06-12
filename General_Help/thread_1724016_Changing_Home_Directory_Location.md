---
title: "Changing Home Directory Location"
date: 2011-04-07
forum: General Help
---

### Post by Dreigo42 on 2011-04-07
I have a dual-boot win7 and Ubuntu 10.10 and I want Ubuntu to use my windows user folder as home. I edited fstab to give me ownership and mount it to /mnt/Windows at startup but whenever I change the location of home in the Users and Groups it acts like it is changing it but it never does. I close the settings and when I re-open it, it is set back to /home/*me*.
Any ideas as to what is going on?

---

### Post by coffeecat on 2011-04-07
You can't use a NTFS filesystem for your home. There are various hidden files and folders that need specific Linux permissions which are not supported in NTFS. What you can do is to set up symlinks to the various folders in your Windows user folder. The folders in your Linux home will be symlinks to the Windows folders but you will be able to browse them, and read and write to them transparently. Your personal files can be on a NTFS filesystem, not the hidden home configuration files.

It's not a good idea to write to a Windows C: drive routinely from outside Windows. Windows can react badly to this. A better option would be to have a separate data partition formatted NTFS for your personal files. You would be able to set up symlinks in Ubuntu in the same way and shortcuts in Windows for convenience.

---

### Post by Dreigo42 on 2011-04-09
I like that Idea. I had never thought about an additional partition. The only downside is that I am not familiar with making symbolic links. is there a simple way to replace the current directories with sim-links?

---

### Post by coffeecat on 2011-04-09
You may need to delete certain folders in the home folder in order to set up links with the same name.

Setting up symlinks.

From the terminal - have a look at 'man ln'.

Easy way:

Create your partition. Mount the partition and in a file browser window, create a folder in the partition - for example, 'Movies'. Now right-click on the Movies folder and choose 'Make Link'. A symlink folder will appear called 'Link to Movies'. At the moment it simply links to the Movies folder in the same filesystem, but we haven't finished yet. Drag and drop the link folder to your home folder and a 'Link to Movies' will appear in your home folder. If you open it, you will be able to see the files and folders in it and read and write to them just as though you were using the original folder. You can now delete the original link folder - it has served its purpose. And you can rename the link folder in your home if you want. I usually remove the 'Link to' from the name because I can see that it is a symlink from the curved arrow on the folder icon.

This will only work reliably if you arrange to have your separate partition automounted on boot up. That requires a line in /etc/fstab. Someone can help you with this if you need when you have your partition set up.

---

### Post by Dreigo42 on 2011-04-10
Thanks Everything is working beautifully now. Ubuntu One even syncs properly. Thanks for all your help!

---

### Post by coffeecat on 2011-04-10
Excellent. Good luck!

---

