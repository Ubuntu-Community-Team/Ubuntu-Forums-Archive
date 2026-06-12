---
title: "Can I make filesystem in RAM?"
date: 2011-10-09
forum: General Help
---

### Post by Pithikos on 2011-10-09
I have been having various issues with recordmydesktop in several days now with audio/video sync and dropping frames. Today I came up with the idea to change the working directory which is by default "/tmp", to the RAM directly. Is that possible? I have 4GB ram.

---

### Post by WasMeHere on 2011-10-09
This is done in [many] live systems, so the easy way would be to boot your system off a CD or USB drive.

---

### Post by Pithikos on 2011-10-09
> **Olle Wiklund said:**
> This is done in [many] live systems, so the easy way would be to boot your system off a CD or USB drive.

Thank you for the answer but that's not really answering my question. I am going to make tutorial videos quite often and rebooting every time into a Live CD and configuring the whole system will be painful :/

---

### Post by WasMeHere on 2011-10-09
> **Pithikos said:**
> Thank you for the answer but that's not really answering my question. I am going to make tutorial videos quite often and rebooting every time into a Live CD and configuring the whole system will be painful :/
... unless you keep it running live for long periods of time. Do you know of 'persistent' live systems? And there are fast usb sticks nowadays, that make booting quite fast.

---

### Post by WasMeHere on 2011-10-09
I found this thread: try if it works for you!
[[COLOR="RoyalBlue"]_http://www.linuxscrew.com/2010/03/24/fastest-way-to-create-ramdisk-in-ubuntulinux/_[/COLOR]]("http://www.linuxscrew.com/2010/03/24/fastest-way-to-create-ramdisk-in-ubuntulinux/")

---

### Post by Pithikos on 2011-10-09
> **Olle Wiklund said:**
> I found this thread: try if it works for you!
[[COLOR=RoyalBlue]_http://www.linuxscrew.com/2010/03/24/fastest-way-to-create-ramdisk-in-ubuntulinux/_[/COLOR]]("http://www.linuxscrew.com/2010/03/24/fastest-way-to-create-ramdisk-in-ubuntulinux/")

Thank you. That made it :D

---

### Post by fixerdave on 2011-10-09
There's also a "pre-cache" system out there... it basically loads all the normally used system files into the drive cache... which is pretty much the same as a RAM disk.  No funky folder copying and redirects, just run the program at boot.

---

### Post by Pithikos on 2011-10-09
> **fixerdave said:**
> There's also a "pre-cache" system out there... it basically loads all the normally used system files into the drive cache... which is pretty much the same as a RAM disk.  No funky folder copying and redirects, just run the program at boot.

But I don't want to load the system files. What I want is to record the screen directly to the RAM so I won't drop frames. Plus the drive cache is a few megabytes big so it definitely is too small for video.

---

### Post by SeijiSensei on 2011-10-09
Ubuntu creates a shared memory device called /dev/shm when it boots.  Use that.

---

### Post by WasMeHere on 2011-10-10
> **Pithikos said:**
> Thank you. That made it :D

Please mark the thread SOLVED
:-)
Olle

---

