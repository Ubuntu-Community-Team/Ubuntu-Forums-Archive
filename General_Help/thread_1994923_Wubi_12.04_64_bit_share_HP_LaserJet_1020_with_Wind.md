---
title: "Wubi 12.04 64 bit share HP LaserJet 1020 with Windows 7"
date: 2012-06-03
forum: General Help
---

### Post by erik1001 on 2012-06-03
Hello. Friend of mine get really interested when he saw my OS and asked me to install and configure it for him. I helped him and now he is owner of PC with Ubuntu Wubi 12.04 64bit but I'm stucked on printer sharing. Actually I think the problem may comes from Windows, but I'm former XP user and I don't know the stuff on Win7.
I installed and configured printer drivers and Samba on Wubi. The printer works fine when I'm printing something from Ubuntu, but when I try accessing it from MS Windows 7 PC, it shows me dialog message "Printer drivers not found" or something. "Click OK to install drivers" but there are not listed drivers for HP LaserJet 1020 printer. Does it mean that Windows 7 doesn't have proper drivers? If true, where can I find proper drivers to install? 
On the Ubuntu's PC there is Windows 7 too and the printer was successfully used by both MS Windows 7 PCs using Print spooler.

Sorry for my English and maybe stupid question and thanks in advance.

---

### Post by Paddy Landau on 2012-06-03
> **erik1001 said:**
> Sorry for my English and maybe stupid question and thanks in advance.
Your English is fine and there are no stupid questions. :)

When you talk about sharing your printer, are you saying that the printer is physically attached to the computer with Ubuntu, and you want to share it with another computer on the local network?

---

### Post by erik1001 on 2012-06-03
Yes, the printer is on the PC with Ubuntu. The connection Ubuntu=>printer works fine as well as Windows=>Ubuntu, but the Windows=>Ubuntu=>printer doesn't.

---

### Post by Paddy Landau on 2012-06-03
Hmm... I'm sorry, I don't know why it's not being found. I'm not much of a Windows expert.

---

### Post by erik1001 on 2012-06-03
[IMG]http://semradar.com.br/wp-content/uploads/2011/08/okay.gif[/IMG] Anyway - thank you for bumping up the thread.

The problem is still there - I see the printer from Windows, but I cannot make it work because of the message I described in first message. :confused:

---

### Post by Paddy Landau on 2012-06-03
Try installing the nearest thing you have to the HP Laserjet 1020 in Windows. See if that helps. Now that I'm writing about it, I remember that I've had similar problems with Windows before.

---

### Post by erik1001 on 2012-06-10
Finally I did it.
The solution was pretty simple.
Open "/etc/samba/smb.conf" with root permissions and then find "[printers]" and adding after it "use client driver = Yes" worked for me.
Thanks, the topic is closed. 8)

---

