---
title: "Krdc to Windows?"
date: 2006-06-02
forum: General Help
---

### Post by chadwick359 on 2006-06-02
While setting up my fresh install of Kubuntu on my laptop this morning, I decided that i would like to get Remote Desktop configured to talk at my windows machine here at work, I can see the Windows machine in Konq, and can access its shares with Samba, but when I try to use Kdrc to connect to the machine, I can't see any available connections. Is there any extra configuration I need to do on either box? (The RDC was working fine when I had windows on my laptop)

---

### Post by art2003 on 2006-06-02
your windows uses a cut down version of terminal server whereas I believe ubuntu's remote desktop client is a vnc client.

So the easiest solution would be to install vnc on your windows pc and to make sure you have the correct port open on your works firewall.

---

### Post by chadwick359 on 2006-06-02
Ah, I figured that may be it. Thanks much!

---

### Post by blimpyboy on 2006-06-04
If the windows computer has remote desktop enabled, you should be able to connect to it with krdc by using a url like "rdp:/windows_computer_name" .  Making it start with "rdp:/" is important.

---

