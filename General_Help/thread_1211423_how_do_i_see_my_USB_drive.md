---
title: "how do i see my USB drive??"
date: 2009-07-12
forum: General Help
---

### Post by carsonrose on 2009-07-12
lsusb shows it... but how do i get to it?

---

### Post by merlinus on 2009-07-12
Have you looked in nautilus?  Also, be sure appropriate boxes are ticked in System/Preferences/Removable Drives and Media.

---

### Post by carsonrose on 2009-07-12
> **merlinus said:**
> Have you looked in nautilus?  Also, be sure appropriate boxes are ticked in System/Preferences/Removable Drives and Media.

what is nautilus and how would I do that check box?? (totally new to Linux/Ubuntu) lsusb shows that i have a flash drive connected... but i dont know how to get to it.

---

### Post by itsjareds on 2009-07-12
Nautilus is the file manager. If you open it, do you see anything labeled "____GB Media"? Ubuntu usually names usb storage devices by how much hard disk space they hold.

If you don't see anything in Nautilus, do you see any icons on your desktop?

---

### Post by carsonrose on 2009-07-12
> **merlinus said:**
> Have you looked in nautilus?  Also, be sure appropriate boxes are ticked in System/Preferences/Removable Drives and Media.

There is no option for removable drives and media there....

---

### Post by carsonrose on 2009-07-12
> **itsjareds said:**
> Nautilus is the file manager. If you open it, do you see anything labeled "____GB Media"? Ubuntu usually names usb storage devices by how much hard disk space they hold.

If you don't see anything in Nautilus, do you see any icons on your desktop?

There is nothing on my desktop and by the file manager... is that what I see when i open "file system"?

---

### Post by brookie on 2009-07-12
Nautilus is like the file manager in windows. When you click on Places/Documents for instance, you are in the nautilus file manager.

What version of Ubuntu are you using? Because I don't have System/Preferences/Removable... option  on Ubuntu 8.10 Intrepid Ibex.

When I plug my usb flash drive into my system Intrepid just sees it, mounts it, and opens up a nautilus window showing my files. When I click on Places I now see my USB drive in the list shown as 'mounted' with an orange arrow looking thing nest to it.

If the arrow thing is not there, right click on your drive (if it's listed) and click on mount to access the files. Hope this helps. 
Cheers, 
brook

---

### Post by carsonrose on 2009-07-12
> **brookie said:**
> Nautilus is like the file manager in windows. When you click on Places/Documents for instance, you are in the nautilus file manager.

What version of Ubuntu are you using? Because I don't have System/Preferences/Removable... option  on Ubuntu 8.10 Intrepid Ibex.

When I plug my usb flash drive into my system Intrepid just sees it, mounts it, and opens up a nautilus window showing my files. When I click on Places I now see my USB drive in the list shown as 'mounted' with an orange arrow looking thing nest to it.

If the arrow thing is not there, right click on your drive (if it's listed) and click on mount to access the files. Hope this helps. 
Cheers, 
brook

I am runningn 9.04... and let me tell you... I cant get online and I cant view my USB drive... my first taste of linux isnt going well :(

---

### Post by itsjareds on 2009-07-12
Yep, opening "Filesystem" will get nautilus open. Alternatively, you can open a terminal and type "nautilus". When you have the file manager open, click the Computer icon at the top and see if any removable media is listed.

Can you post fdisk -l?

---

### Post by carsonrose on 2009-07-12
> **itsjareds said:**
> Yep, opening "Filesystem" will get nautilus open. Alternatively, you can open a terminal and type "nautilus". When you have the file manager open, click the Computer icon at the top and see if any removable media is listed.

Can you post fdisk -l?

I cant get my Ubuntu machine online, but I entered that command in the terminal with "sudo" infront... I have three lines..what should i type in here to tell you the info you are looking for?

no removable media is present

---

### Post by itsjareds on 2009-07-12
Oh. Alright then, nevermind.

I just booted into Ubuntu again and tried plugging in my USB flash drive, and I reached the same problem. Sometimes you just have to unplug/replug your drive to get Ubuntu to read it. Try unplugging and replugging your drive, then see if any window comes up (should be the file manager).

---

### Post by carsonrose on 2009-07-12
> **itsjareds said:**
> Oh. Alright then, nevermind.

I just booted into Ubuntu again and tried plugging in my USB flash drive, and I reached the same problem. Sometimes you just have to unplug/replug your drive to get Ubuntu to read it. Try unplugging and replugging your drive, then see if any window comes up (should be the file manager).


no change... i even tried a different USB port.. nadda...

---

