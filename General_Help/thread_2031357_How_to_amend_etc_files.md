---
title: "How to amend /etc files?"
date: 2012-07-21
forum: General Help
---

### Post by badaveil on 2012-07-21
The object here is to change "letter" to "A4" in /etc/papersize so that the default setting for papersize in LibreOffice is A4: 


Under user account, I am recognized as the Administrator but when I tried to amend /etc/papersize under Properties/Permissions, I found I am not the owner but that file is owned by root.

How do I become root so that I can amend that file?:confused:

---

### Post by CharlesA on 2012-07-21
sed ftw:

```
sudo sed -i 's/letter/A4/g' /etc/papersize
```

---

### Post by mamamia88 on 2012-07-22
sudo (your text editor here) /etc/papersize

---

### Post by CharlesA on 2012-07-22
> **mamamia88 said:**
> sudo (your text editor here) /etc/papersize
gksudo if using graphical apps. ;)

---

### Post by badaveil on 2012-07-22
> **CharlesA said:**
> sed ftw:

```
sudo sed -i 's/letter/A4/g' /etc/papersize
```

EXCELLENT!:D:D:D

A copy and paste onto the terminal then I activated and looked at my LibreOffice Word and LibreOffice Calc default page setting and both are A4.

EXCELLENT!:D:D:D

Thank you, Thank you Thank you. It pays to ask at Ubuntu Forum

---

