---
title: "Maverick USB issue - system lags"
date: 2010-10-11
forum: General Help
---

### Post by makro on 2010-10-11
Fresh Maverick installation.

Maverick is fast until I plug/unplug the USB keyboard or mouse or any other USB device.
After plug Maverick becomes slow without abnormal processes in 'top'.
All become slow, USB Keyboard lags (about 1 or 2 seconds) typing a key especially in gnome-terminal, Javascript animations (trying jquery-ui effects page) in Firefox/Chrome become very slow, flash videos too.
System takes about a minute to shutdown/reboot and close GDM session.

Without plug any USB device maverick is very smooth.

[https://bugs.launchpad.net/bugs/658161]("https://bugs.launchpad.net/bugs/658161")

---

### Post by makro on 2010-10-11
After a day at work without plug/unplug any usb I didn't have slowdown at all.

As I plugged the USB keyboard before shutdown, system starts to lag again!

---

### Post by makro on 2010-10-21
SOLVED!!

I had to update my laptop's BIOS.
My PC's HP Compaq 6730s with intel GMA. 
Upgrading BIOS solved all the issues

---

### Post by ivanovnegro on 2010-10-21
> **makro said:**
> SOLVED!!

I had to update my laptop's BIOS.
My PC's HP Compaq 6730s with intel GMA. 
Upgrading BIOS solved all the issues

Its not related to your post, I found it accidentally.
I have the same notebook with Intel GMA.
Can you say me how you upgraded your BIOS and if it makes sence?
I upgraded my system also and saw in the terminal that I have to do a BIOS update but I cannot remember why it appeared while upgrading and what it means.

Thanks

---

### Post by makro on 2010-10-22
First of all check your BIOS version. Press F10 at boot and then look into infos. Mine was 68PZU (version F09)

If your is 68PZU or 68PZD click here [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3687778&prodNameId=3687786&swEnvOID=1093&swLang=13&mode=2&taskId=135&swItem=ob-74611-1]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3687778&prodNameId=3687786&swEnvOID=1093&swLang=13&mode=2&taskId=135&swItem=ob-74611-1")

Using a Windows XP/Vista open the downloaded file (it extracts some files into a folder). Click on the exe in the created folder (I clicked on the one which finish with "u") and plug an USB key or a blank CD and follow the instructions.

Hope it helps.

---

### Post by ivanovnegro on 2010-10-22
First of all thank you for your quick reply.
I have the same version like you only its F.07.
But my notebook is Windows free.:)
I think I have to make a more complicated procedure and am not sure if I will have changes.
I read that upgrading the BIOS is a sensible thing.
So, Im not sure.

---

### Post by makro on 2010-10-22
Hi! 
You've to do exactly what I wrote! My BIOS was F.07 before update!
You only have to use a WindowsXP/Vista PC to create the CD or USB Key.
It creates a bootable device! So you've only to boot your PC from the device you've created.

---

### Post by ivanovnegro on 2010-10-22
Ok, I understand.
I will use the notebook of my girlfriend, she has XP on it and then I will follow your steps.
Thank you again.

---

### Post by makro on 2010-10-22
You're welcome! 
Maverick is amazing now!

---

### Post by ivanovnegro on 2010-10-23
Hey Makro,

thank you very much for your instructions.
Now everything works perfectly.
Never knowed about upgrading the BIOS.

Regards

---

