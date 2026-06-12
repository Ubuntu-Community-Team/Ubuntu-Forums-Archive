---
title: "5 into 1 ..."
date: 2006-03-23
forum: General Help
---

### Post by wannabelinuxconvert on 2006-03-23
Hi guys,

I have 5 (*possibly more*) 2.7gb hard drives ... is there any way, or any software I can install that will make Linux think it's just one big drive !?

All help or ideas will be appreciated.

Thanks

Mic

---

### Post by wannabelinuxconvert on 2006-03-23
I think I've found the solution using mdadm and raid-5 ... does anyone know of any decent tutorials on settin up raid through mdadm !?

Cheers

Mic

---

### Post by dcstar on 2006-03-23
[QUOTE=wannabelinuxconvert]Hi guys,

I have 5 (*possibly more*) 2.7gb hard drives ... is there any way, or any software I can install that will make Linux think it's just one big drive !?

All help or ideas will be appreciated.

Thanks

Mic[/QUOTE]
[http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)

---

### Post by wannabelinuxconvert on 2006-03-23
Not quite what I was looking for ... anyone else !?

Thanks

Mic

---

### Post by friendly_guy on 2006-03-23
This may not be what you are looking for but here goes:

Because of the the 'anything is a file' nature of unix/linux you can mount your hard drive to any directory (aka folder)  on your computer (eg one inside your home directory) & it will be treated as part of your computers filesystem.  The fact it is a separate drive will be not be apparant in everyday use.  

You could do this with as many drives as your machine will take.  If you want them mounted permanently edit your /etc/fstab file (backing it up first!).

---

### Post by az on 2006-03-23
[QUOTE=wannabelinuxconvert]Not quite what I was looking for ... anyone else !?

Thanks

Mic[/QUOTE]
But.... That's exactly what raid is.  You combine a number a physical drives into one logical volume.  You deal with that logical volume as if it were one big hard drive.

You even have tools to move data out of one physical drive to take it out of the raid array.

---

