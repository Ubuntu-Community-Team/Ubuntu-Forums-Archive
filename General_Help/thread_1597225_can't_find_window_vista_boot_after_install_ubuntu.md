---
title: "can't find window vista boot after install ubuntu"
date: 2010-10-15
forum: General Help
---

### Post by Plasticbottle on 2010-10-15
So I've install Ubuntu 10.04 onto my hard drive which had window vista installed first. After I've finished installing Ubuntu, i found out that there is only Ubuntu available on the GRUB and my Wiindow Vista is gone! What can I do to put or install back the Window Vista boot? :(

---

### Post by lisati on 2010-10-15
If you are able to run the following from the command line and post the output, it might be able to get us started with suggestions:
```
sudo fdisk -l
```

---

### Post by Plasticbottle on 2010-10-15
please have look!

---

### Post by lisati on 2010-10-15
The good news is that it looks like that Vista is still on your system.

I'd suggest running this command from the terminal, and seeing if Vista shows up when you reboot:
```
sudo update-grub
```

Other forum users might be able to offer further help.

---

### Post by Plasticbottle on 2010-10-15
OKay this is what I've got after typing it in.

---

### Post by Plasticbottle on 2010-10-15
> **lisati said:**
> The good news is that it looks like that Vista is still on your system.

I'd suggest running this command from the terminal, and seeing if Vista shows up when you reboot:
```
sudo update-grub
```

Other forum users might be able to offer further help.

I've done it but after restarting its still the same :O

---

### Post by Quackers on 2010-10-15
Please go to the link below and download the file to your desktop then run the command given on that site. This will produce a results.txt file on your desktop.
Please paste the contents of that file in your next post using CODE tags (New Reply and click on # symbol)

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Plasticbottle on 2010-10-16
Wow thanks for your help^^ but I've already solved it through another way. Great appreciation for your work^^

---

