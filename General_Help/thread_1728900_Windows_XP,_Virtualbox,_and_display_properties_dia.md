---
title: "Windows XP, Virtualbox, and display properties dialog"
date: 2011-04-14
forum: General Help
---

### Post by haapsalu_sall on 2011-04-14
I have installed Virtualbox from their website. I was able to create an XP virtualbox. I have tried several times, though, to download the XP disc to the virtualbox and I keep getting an error message that says it needs 32 bits. I found the display properties box and changed it from 16 to 32, also restarted the computer. I am still getting a wrong machine message with this error message about 16 bit. What am I missing?

2007 Toshiba Satellite L-35
Ubuntu user since 4/11 running 10.10

---

### Post by Dngrsone on 2011-04-14
Windows XP is designed to run on a 32-bit processor.  The version of Virtualbox you are using is apparently hosting a 16-bit machine.

Which Virtualbox are you using?   I recommend going to the [Virtualbox](http://www.virtualbox.org/) site and downloading it from there instead of installing it from the Ubuntu software center.

---

### Post by haapsalu_sall on 2011-04-14
I'm using Virtualbox 4.0 from the website for Maverick. 

The error message I got said Wrong Machine go to display properties dialog and change to 32 bit. I went to diplay, changed the video memory to 32 bit, restarted the computer. Still getting the same error.

---

### Post by Slim Odds on 2011-04-14
You're confusing bits, bytes and color depth.

You need to install the VirtualBox Guest Additions to get 32 color depth on the display.

---

### Post by haapsalu_sall on 2011-04-14
Installed it, tried again, and I'm still getting the same error. Is there something in the Guest Additions that I have to change? How do I do it?

---

### Post by Slim Odds on 2011-04-14
> **haapsalu_sall said:**
> Installed it, tried again, and I'm still getting the same error. Is there something in the Guest Additions that I have to change? How do I do it?

Did you reboot the virtual machine? You need to after you install the Guest Additions.

---

### Post by haapsalu_sall on 2011-04-15
I rebooted the computer itself. Will this reboot the virtual machine? If not, how do I do that. A Google search doesn't tell me anything.

---

### Post by Slim Odds on 2011-04-16
> **haapsalu_sall said:**
> I rebooted the computer itself. Will this reboot the virtual machine? If not, how do I do that. A Google search doesn't tell me anything.

Just restart the OS in the virtual machine as you would if it was not in a virtual machine.

---

### Post by haapsalu_sall on 2011-04-18
Thank you for your help.

---

