---
title: "Need help uninstalling Ubuntu (vista dual boot)"
date: 2009-06-28
forum: General Help
---

### Post by atomsmasherr on 2009-06-28
I've been planning to remove Ubuntu from my desktop computer ever since I've got it on my laptop, but I never got around to it. Finally I have some time but I'm not sure how to go about it. This is the first time I am doing this so looking at other posts was a bit confusing. If you guys help me out I'd appreciate it.

Also I don't want to lose any of the files (in the vista partition) if possible.

---

### Post by atomsmasherr on 2009-06-28
bumpppp

---

### Post by DeMus on 2009-06-28
> **atomsmasherr said:**
> I've been planning to remove Ubuntu from my desktop computer ever since I've got it on my laptop, but I never got around to it. Finally I have some time but I'm not sure how to go about it. This is the first time I am doing this so looking at other posts was a bit confusing. If you guys help me out I'd appreciate it.

Also I don't want to lose any of the files (in the vista partition) if possible.

I don't know Vista but I am sure it has some kind of disc-management. Can't you use that to throw away the (for Windows) unknown partitions Ubuntu uses and make a new Windows partition from the empty space you created?
Why you want to delete Ubuntu? Don't like it, or don't know how to use it?

---

### Post by atomsmasherr on 2009-06-28
No I enjoy Ubuntu, although I'm very new to it. I installed it on my laptop, but I need vista on this desktop.

---

### Post by Vikhyath on 2009-06-28
If you still have the ubuntu installation cd, you can use it to boot in live cd mode and use gparted to format the ubuntu partition

---

### Post by atomsmasherr on 2009-06-28
No I don't have it.

---

### Post by Vikhyath on 2009-06-28
> **atomsmasherr said:**
> No I don't have it.
you can download the gprted ISO files from **"[this link"]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")**.
Burn them on to a cd and boot from the cd.

---

### Post by atomsmasherr on 2009-06-28
Okay, thanks. So once I boot from the CD where do I go from there? Is it for the most part self-explanatory?

---

### Post by Odemia on 2009-06-28
You need to restore the MBR using the vista install cd.  And remove the Ubuntu partition, this is most easily done using an Ubuntu live CD, if you don't have the live cd or a cd to burn to you can put it on a usb stick (backup any data you have on the usb before trying this) using the "Ubuntu Live USB Creator" on your laptop.

Sorry you had trouble finding instructions for this.  Google returned this [URL="http://%3Cbr%20/%3E%0Ahttp://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html"]
http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html[/URL] detailed instruction as the #1 result for me.

---

### Post by Vikhyath on 2009-06-28
make sure you retrieve any files you (might) have on the ubuntu partition then restart your computer and boot from the cd. Select the ubuntu partition and right click , select the option to format.
If my description above seems a little cloudy , try [http://www.brunolinux.com/01-First_Things_To_Know/Windows_Tools_-_Gparted.html](http://www.brunolinux.com/01-First_Things_To_Know/Windows_Tools_-_Gparted.html)

---

### Post by DeMus on 2009-06-28
Why so complicated? Why booting into a live CD, or a Grub CD, why not just use the Windows partition manager to delete the Ubuntu partition(s) and create a new Windows disk?
Yes, you have to use the Windows CD to restore MBR so Windows will start without the Grub menu. How to do that is just a Google away.

---

### Post by Vikhyath on 2009-06-28
> **DeMus said:**
> Why so complicated? Why booting into a live CD, or a Grub CD, why not just use the Windows partition manager to delete the Ubuntu partition(s) and create a new Windows disk?
Yes, you have to use the Windows CD to restore MBR so Windows will start without the Grub menu. How to do that is just a Google away.
I dont think the windows partition manager recognizes the ext type filesystems

---

### Post by DeMus on 2009-06-28
> **Vikhyath said:**
> I dont think the windows partition manager recognizes the ext type filesystems

It will see unknown partitions which can be deleted, atleast this was the case in XP. As said before I do not know Vista.

---

### Post by Vikhyath on 2009-06-28
@atomsmasherr 
in case you dont know where to find windows partition manager, right click my computer >manage> disk management.

---

