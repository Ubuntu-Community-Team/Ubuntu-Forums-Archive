---
title: "Installing windows XP on Ubuntu with Vmplayer"
date: 2006-03-27
forum: General Help
---

### Post by Dearhell on 2006-03-27
I have installed properly vmplayer on my Ubuntu and then I have created a .iso from my Windows XP cdrom. Now, how can I install that windows XP iso with the vmplayer?

When I use the vmplayer command on the console it asks me for *.vmx file

I tried searching through the forum but it seems there is nothing about this.

---

### Post by justleen on 2006-03-27
im not sure bout this, but i think you need VMware for that, not the player..

---

### Post by Dearhell on 2006-03-27
It can be made with the free vmplayer because I did it a time ago, but I can't remember how.

---

### Post by silent82 on 2006-03-27
You could use VMware server (free download), or, if you like the Player (smaller), you could try to look at 

[http://blog.lorenzoferrara.net/pivot/entry.php?id=73](http://blog.lorenzoferrara.net/pivot/entry.php?id=73)

---

### Post by Dearhell on 2006-03-27
I have fixed the problem with the [VM Builder](http://www.consolevision.com/members/dcgrendel/vmxform.html), it generates a *.vmx file config.

But now when it starts the installation of windows XP it shows a error that says that I have not any HD disk available.

---

### Post by az_human on 2006-03-27
Here's the [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=84275&highlight=install+windows+vmware+player") from this forum.

---

### Post by Dearhell on 2006-03-27
But I can't install the [Qemu Windows version](http://free.oszoo.org/ftp/qemu/win32/release/QemuInstall-0.7.2.exe) that it's said in that how-to with my wine.

There is another way to format a space to install Windows XP with Vmplayer without Qemu?

---

### Post by justleen on 2006-03-27
you could just create freespace with fdisk  or parted (=delete the partition you want to use).. the windows setup should see this free space, and in the setup you can frmat it as fat32/ntfs

---

### Post by Dearhell on 2006-03-27
My laptop HD only has a 80 Gb partition with Ubuntu.

And don't know how to catch the free space with the fdisk command.

---

### Post by az_human on 2006-03-27
[QUOTE=Dearhell]But I can't install the [Qemu Windows version](http://free.oszoo.org/ftp/qemu/win32/release/QemuInstall-0.7.2.exe) that it's said in that how-to with my wine.

There is another way to format a space to install Windows XP with Vmplayer without Qemu?[/QUOTE]

Why can't you install Qemu?  Is there a problem?  What prevents the installation from succeeding?

---

### Post by Dearhell on 2006-03-28
I cannot install the windows version through wine that it's said in that how-to post.

However I tried to install de Ubuntu Qemu version and try then to install windows through it, but it freezes after installing the windows files (in the screens that says the wonderful that it's Windows)

---

### Post by M@dMerC on 2006-06-22
to make the HDD for windows to install to simply type this into a terminal:
" qemu-img create -f vmdk windowsxp.vmdk 5G Formating 'windowsxp.vmdk' , fmt=vmdk "
if that doesnt work try doing:
" sudo apt-get install qemu " first  
you can also change windowsxp.vmdk (in the first command) to whatever you want and also 5G can be changed to whatever size you want the drive to be eg. 10G=10 Gig HDD
hope this helps.

---

