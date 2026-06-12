---
title: "Floppy doesn't"
date: 2006-02-16
forum: General Help
---

### Post by Denbeigh on 2006-02-16
Hi all,
I have had Ubuntu installed for two days and like what I see.
However I cannot access the floppy drive. All else is fine.
Some advice please, but take it step by step if possible.
Thanks in advance.

---

### Post by StefanoCole on 2006-02-17
Hello and Welcome to the Ubuntu forum. Maybe the following thread can help you: [http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy]("http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy")

Stefano

---

### Post by cotcot on 2006-02-17
Was the floppy working before ? If not you might have to enable the floppy in your BIOS.

---

### Post by Denbeigh on 2006-02-17
[QUOTE=StefanoCole]Hello and Welcome to the Ubuntu forum. Maybe the following thread can help you: [http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy]("http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy")

Stefano[/QUOTE]

Hi, thank you from New Zealand.
It works but I may have damaged something as I need to mount after every boot up.
However I can exist until Dapper arrives.
Thanks again.:)

---

### Post by arctic on 2006-02-17
I doubt that you broke anything. When the system shuts down, it will unmount all drives. CD, DVD, Floppy and harddisks for security reasons. For the same security reasons, only the needed harddisks mentioned in fstab will be mounted. Everything wlse will be mounted on demand, that is after remounting them by inserting CDs or double-clicking the floppy entry.

If something different happenes on your computer, please explain what happens exactly.

---

