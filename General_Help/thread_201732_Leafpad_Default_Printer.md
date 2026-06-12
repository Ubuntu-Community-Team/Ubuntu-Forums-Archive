---
title: "Leafpad Default Printer"
date: 2006-06-22
forum: General Help
---

### Post by OffHand on 2006-06-22
Hi
I just tried printing with Leafpad (my favorite simple text editor) but I have to fill in the default printer name each time I want to print. The default is set to use lp. If I change the name to match my printers name it prints fine. Does anyone know how I can make my printer default?

---

### Post by Rui Pais on 2006-06-22
hi, 
i think thats a known limitation of leafpad.

You may be interested in give mousepad a try. It's very similar, look and lightness, but made exactly to offer better print support:
[http://packages.ubuntulinux.org/dapper/editors/mousepad]("http://packages.ubuntulinux.org/dapper/editors/mousepad")

---

### Post by OffHand on 2006-06-22
[QUOTE=Rui Pais]hi, 
i think thats a known limitation of leafpad.

You may be interested in give mousepad a try. It's very similar, look and lightness, but made exactly to offer better print support:
[http://packages.ubuntulinux.org/dapper/editors/mousepad]("http://packages.ubuntulinux.org/dapper/editors/mousepad")[/QUOTE]
Thanks for your reply. I tried it but it is slower and didn't want to print. At least Leafpad can print when I type in my printers name. Can't I hack the code or something? I mean, if it chooses lp by default one would think it could also be my printers name :confused:

---

### Post by Rui Pais on 2006-06-22
[QUOTE=subsonic_shadow]Thanks for your reply. I tried it but it is slower and didn't want to print. At least Leafpad can print when I type in my printers name. Can't I hack the code or something? I mean, if it chooses lp by default one would think it could also be my printers name :confused:[/QUOTE]

uhmm, sorry, you are right... mousepad to print needs xfprint4 and a2ps.

About changing names... maybe adding another configuration to your printer and give the name lp works.

---

### Post by OffHand on 2006-06-22
[QUOTE=Rui Pais]uhmm, sorry, you are right... mousepad to print needs xfprint4 and a2ps.

About changing names... maybe adding another configuration to your printer and give the name lp works.[/QUOTE]
I created a printer named lp and Leafpad now prints  :D

---

