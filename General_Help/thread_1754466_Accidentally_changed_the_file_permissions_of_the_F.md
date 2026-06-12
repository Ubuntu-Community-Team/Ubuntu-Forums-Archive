---
title: "Accidentally changed the file permissions of the FS to 644"
date: 2011-05-10
forum: General Help
---

### Post by Parapan on 2011-05-10
Hello all, I've made a really critical and simple mistake and now im trying to recover my computer. I accidentally logged into root and was trying to change permissions for the current directory with "." but instead used a "/" which started changing permissions of everything from / recursively. I quickly realized the mistake I made after it started and aborted the process by pressing ctrl+C. However I know many things are still not right because, even though I tried to reboot and change the permissions back to 0755 from the recovery mode root console, I still get errors when gnome tries to start..Here is the exact error im getting .. "There is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256". I'm pretty sure because of the way I aborted or because of the time the filesystem was running with 644 permissions, some amount of damage was done..Does anyone know if there is a way to recover it to normal? Or is there a way to recover it from the Ubuntu CD? Thx

---

### Post by nothingspecial on 2011-05-10
> **Parapan said:**
> Hello all, I've made a really critical and simple mistake and now im trying to recover my computer. I accidentally logged into root and was trying to change permissions for the current directory with "." but instead used a "/" which started changing permissions of everything from / recursively. I quickly realized the mistake I made after it started and aborted the process by pressing ctrl+C. However I know many things are still not right because, even though I tried to reboot and change the permissions back to 0755 from the recovery mode root console, I still get errors when gnome tries to start..Here is the exact error im getting .. "There is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256". I'm pretty sure because of the way I aborted or because of the time the filesystem was running with 644 permissions, some amount of damage was done..Does anyone know if there is a way to recover it to normal? Or is there a way to recover it from the Ubuntu CD? Thx

Theoretically it's possible..........

First, you need to find out which files you have changed to 644, then you need to find out what they should be, then you need to change them back.

It would probably be much much easier and quicker to back up and reinstall.

---

### Post by coffeecat on 2011-05-10
This sort of question comes up occasionally and in all the threads I've been involved in, the OP eventually concludes that it's quicker and easier to re-install. Changing the permissions to 755 was just as problematic as changing them to 644, and it's not quite clear how much of the filesystem was chmodded. If /usr files are affected, it's a good bet that the whole of /etc is as well - which is just as serious.

If you have access to another permanent installation, run 'ls -Rl /etc' and 'ls -Rl /usr' to see what a bewildering medley of different permissions are present in system directories, and what a gargantuan task it would be to set everything to rights.

I agree with nothingspecial.

---

### Post by Parapan on 2011-05-10
Alright, thanks a lot guys, i guess thats just easier, will do. thanks anyways

---

