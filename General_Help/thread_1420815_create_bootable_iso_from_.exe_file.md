---
title: "create bootable iso from .exe file"
date: 2010-03-03
forum: General Help
---

### Post by dcody on 2010-03-03
Hello - I am running ubuntu 9.10 on my pc, trying to update the bios on a thinkpad a31. I'm trying to create a bootable iso disk from the downloaded file from ibm (spsuiv69.exe) it is currently sitting on my desktop. Be gentle with me - I'm new. Thanks tons.

To be clear - I am having trouble making the .exe file an iso. I read this is the best way to update bios on a linux machine, if there are better ideas - whatever works. Thanks again.

---

### Post by psusi on 2010-03-03
You need to follow the directions from the manufacturer.  If it is a windows executable, then you will need a windows install to use it.  If it is a dos executable, then you need to put it on a dos boot disk.

---

### Post by dcody on 2010-03-03
I found this but the link is dead and I am not sure how to modify it to make it work.
[http://www.bergek.com/2007/06/06/upgrade-thinkpad-bios-from-ubuntu/](http://www.bergek.com/2007/06/06/upgrade-thinkpad-bios-from-ubuntu/)

---

### Post by jocko on 2010-03-03
> **dcody said:**
> Hello - I am running ubuntu 9.10 on my pc, trying to update the bios on a thinkpad a31. I'm trying to create a bootable iso disk from the downloaded file from ibm (spsuiv69.exe) it is currently sitting on my desktop. Be gentle with me - I'm new. Thanks tons.

To be clear - I am having trouble making the .exe file an iso. I read this is the best way to update bios on a linux machine, if there are better ideas - whatever works. Thanks again.

You don't actually make an iso from an .exe, in this case the .exe file is really an archive file that already contains a boot cd image file. You just need to unpack the archive and burn the image to a cd (but for most cd burning programs it's easier to convert the .img file to a .iso file first...).
First make sure you have cabextract installed:```
sudo apt-get install cabextract
```
Then use cabextract to extract the contents of the file:```
cd ~/Desktop #if that's where the file is
cabextract spsuiv69.exe
```
And finally make an iso file from the extracted .img file:```
mkisofs -b IVUJ11US.IMG  -o biosboot.iso IVUJ11US.IMG
```

---

### Post by DenysT on 2010-03-03
> **dcody said:**
> Hello - I am running ubuntu 9.10 on my pc, trying to update the bios on a thinkpad a31. I'm trying to create a bootable iso disk from the downloaded file from ibm (spsuiv69.exe) it is currently sitting on my desktop. Be gentle with me - I'm new. Thanks tons.

To be clear - I am having trouble making the .exe file an iso. I read this is the best way to update bios on a linux machine, if there are better ideas - whatever works. Thanks again.

According to IBM the file spsuiv69.exe is a Windows executable. You have to be running a supported version of Windows to use this file. There is a floppy diskette version available. You'll still have to create a bootable DOS diskette with Windows though.

---

### Post by dcody on 2010-03-03
> **jocko said:**
> You don't actually make an iso from an .exe, in this case the .exe file is really an archive file that already contains a boot cd image file. You just need to unpack the archive and burn the image to a cd (but for most cd burning programs it's easier to convert the .img file to a .iso file first...).
First make sure you have cabextract installed:```
sudo apt-get install cabextract
```
Then use cabextract to extract the contents of the file:```
cd ~/Desktop #if that's where the file is
cabextract spsuiv69.exe
```
And finally make an iso file from the extracted .img file:```
mkisofs -b IVUJ11US.IMG  -o biosboot.iso IVUJ11US.IMG
```


made cabextract - getting an message "all done - errors while processing" when I run cabextract. I originally posted the wrong file - the correct one is - 1nuj10ud.exe. 
Thanks

---

### Post by jocko on 2010-03-03
> **DenysT said:**
> According to IBM the file spsuiv69.exe is a Windows executable. You have to be running a supported version of Windows to use this file. There is a floppy diskette version available. You'll still have to create a bootable DOS diskette with Windows though.
It's probably a windows executable archive, i.e it's like a self extracting .zip or .cab that unpacks itself and runs a script or program that writes the image file to a disc. In that case it is possible to unpack the archive and write the image to disk using linux programs instead of the windows program/script contained in the .exe file itself.

---

### Post by dcody on 2010-03-03
Thanks for your help. Is it simple to re-install xp next to ubuntu or do you think it might be possible to write an iso in virtual box on xp?

---

### Post by jocko on 2010-03-03
> **dcody said:**
> made cabextract - getting an message "all done - errors while processing" when I run cabextract. I originally posted the wrong file - the correct one is - 1nuj10ud.exe. 
Thanks

The file 1nuj10ud.exe that I can find on lenovo's download page is a dos executable, and not a windows executable archive, so the instructions you are trying to use will not work.
They actually link to a linux file, but that bios is dated 2003...

---

### Post by jocko on 2010-03-03
> **dcody said:**
> Thanks for your help. Is it simple to re-install xp next to ubuntu or do you think it might be possible to write an iso in virtual box on xp?
I tried to run the dos executable in dosemu (a dos emulator for linux) and it seems to work, but it just asks for the floppy drive letter and does not seem to take any switches that would allow extraction to something else than a floppy.
But if dosemu or a virtualized xp install could get physical access to a floppy drive (or perhaps even a floppy disc image) I don't see why it would not work...

---

### Post by psusi on 2010-03-03
If the executable just creates a bootable floppy disk, then yes, you could run it under dosemu to get the boot floppy you need to flash the bios.  If you don't actually have an actual floppy you could have dosemu use a floppy disk image file and burn THAT to a bootable cd.

---

### Post by dcody on 2010-03-03
> **jocko said:**
> 
They actually link to a linux file, but that bios is dated 2003...

Yeah, I saw that - just wouldn't be an upgrade for me. 

Whats a simple way to put xp back on my system next to ubuntu, without me making a mess of things.

---

### Post by psusi on 2010-03-03
> **dcody said:**
> Yeah, I saw that - just wouldn't be an upgrade for me. 

Whats a simple way to put xp back on my system next to ubuntu, without me making a mess of things.

Boot from the livecd, use gparted to shrink your existing partition to free up some space, then install windows to the free space.

---

