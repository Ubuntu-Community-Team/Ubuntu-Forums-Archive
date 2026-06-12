---
title: "how to copy files from one ubuntu to other if permission denie"
date: 2011-12-26
forum: General Help
---

### Post by sonyofjapan on 2011-12-26
so i got this ubuntu 9.04. it suddenly crash one day
so then i made a ubuntu 9.04 live cd and pop it in another pc.
then i took the hdd of the crash ubuntu and connect to the other pc using live cd.
i connect it by using usb to sata/pata connector
then when i was copying files, it says permission denie, since the live cd pc dont own the files.
 
is there a way to get past that?

---

### Post by The Cog on 2011-12-26
Do it as root. Command-line, use 
> sudo cp -r source-folder destination-folder

for a gui use the command 
> gksu nautilus
to launch the file manager.

be careful with these extra rights - you have the right to trash the system.

P.S.
You may have to change the owner once the files are on the destination drive. 
> sudo -R chown username:username directorynamebut never be tempted to take ownership of system files like that or you'll be reinstalling soon afterwards because lots of odd things break.

---

### Post by sonyofjapan on 2011-12-27
ok, so i did the file manager but when i copy and paste it to a flash drive (from my crash ubuntu hdd), the file operation would froze. 
and when i click "send to" that also froze.

---

### Post by sonyofjapan on 2011-12-27
> **The Cog said:**
> Do it as root. Command-line, use 
 
 
for a gui use the command 
 
to launch the file manager.
 
be careful with these extra rights - you have the right to trash the system.
 
P.S.
You may have to change the owner once the files are on the destination drive. 
but never be tempted to take ownership of system files like that or you'll be reinstalling soon afterwards because lots of odd things break.
 
 
ummm...i got another problem now. try to copy the files but the operation would freeze. i use "send to" and it still freeze.

---

### Post by The Cog on 2011-12-27
If the GUI is freezing, I would then try the command-line. It might give a helpful error message. Be patient, it might take a while to complete. If there is an error message, post it here and people might know what it means.

---

### Post by sonyofjapan on 2011-12-31
> **The Cog said:**
> If the GUI is freezing, I would then try the command-line. It might give a helpful error message. Be patient, it might take a while to complete. If there is an error message, post it here and people might know what it means.
 
ok, i found out why it wasnt doing it. permission denie agian

---

