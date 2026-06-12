---
title: "Brightness adjustment in Dell inspiron 14R"
date: 2010-08-18
forum: General Help
---

### Post by shammi000 on 2010-08-18
Hi All,

I am not able to adjust the brightness in ubuntu.

I am using gnome and ubuntu 10.04.

I can see some folders DD01, DD02 in /proc/acpi/video/GFX0/  with value as given below.


cat /proc/acpi/video/GFX0/DD01/brightness 
<not supported>


I will appreciate any help.

Regards,
Shammi

---

### Post by psynaps3 on 2010-08-22
Same issue here, I'm unable to adjust the brightness on this model.

---

### Post by psynaps3 on 2010-08-22
Shammi, refer this [post]("http://georgia.ubuntuforums.org/showpost.php?p=9750643&postcount=12").

---

### Post by TCattitude on 2010-10-23
This PPA fix works for me:
[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)
Just add the sources for the update, run the update, restart system. Works ;)

Inspiron 14R.

---

### Post by murphyac on 2011-05-10
Worked for me too.  My brightness keys now work perfectly.  So glad Kamal Mostafa worked this out.
Angela C. Murphy, Dell Inspiron 14R(N4010).:)

---

### Post by ramkumarh on 2011-09-12
Brilliant, this is simple and works for me.
Using Dell Inspiron 14R (N4010).

---

