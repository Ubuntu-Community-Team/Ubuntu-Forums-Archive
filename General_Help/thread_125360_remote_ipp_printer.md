---
title: "remote ipp printer"
date: 2006-02-03
forum: General Help
---

### Post by edoardo on 2006-02-03
what does it take to get the KDE add printer wizard work for a remotely accessible CUPS printer?


I run ubuntu/kubuntu on 3 machines in a LAN
one has a usb printer HP840C (which works locally after having read about this fix [http://www.ubuntuforums.org/showthread.php?t=75286](http://www.ubuntuforums.org/showthread.php?t=75286).)

Of course I want the other machines to access the printer. If I share it with SAMBA (using for example the tools in the kde settings/kcontrol) then the others can access it (by entering its location manually in the kde add printer wizard). But I'd rather not rely on samba and 
wanted the other machines to access it as a remote cups server printer. The add printer wizard could not connect to the machine.

first, it took quite a bit to figure out that on the server machine i had to use the kde print server configuration to tell it to listen to any host and to add the printer itself in the security settings.

still, even though I used gnome-cups-add and entered the uri manually ad managed to print, the KDE wizard never sees the printer (there if it can't be selected you can't even enter the uri manually).

what is it necessary to configure in order to get to the remote cups printer through the kde wizard?

---

