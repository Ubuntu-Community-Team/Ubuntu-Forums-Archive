---
title: "Network printing with Windows 7"
date: 2010-01-23
forum: General Help
---

### Post by killiekosmos on 2010-01-23
I've just started using ubuntu (9.10).  I istalled it on an old PC and connected it up to my home network (XP laptop, Vista laptop and Win7 desktop).  The Win7 PC has an HP C5280 attached as a shared printer and all Windows computers can print to it.

When I try to connect to it from ubuntu I keep getting asked for a password.  No matter what I use it says I'm wrong!  I even took all the passwords off the Win7 PC but I still get asked.

From the ubuntu box I can see the other devices on the network and explore the laptops but if I try to access the Win7 PC I get asked for a password again.

I suspect I've missed something simple so any suggestions welcome.

Thanks

---

### Post by nateperson on 2010-01-23
Try enabling "TCP Printing services" on your windows box.

---

### Post by nateperson on 2010-01-23
Sorry thats wrong, here's the steps you need to do so you can print to your PC...

On the Windows 7 PC

1. In Windows 7 Control Panel

2. Select "Programs and Features" pane

3. Click "Turn Windows Features on or off"

4. Click on the "LPD Print Service". Under "Print and Document Services"

5. Ensure printer(s) are shared

---

### Post by killiekosmos on 2010-01-23
Still no joy!  Ubuntu keeps asking me to log on to the Windows 7 machine but rejects all passwords

---

### Post by nateperson on 2010-01-24
I'm at a loss then, here's a thread with some other stuff to check...

[http://social.answers.microsoft.com/Forums/en-US/w7network/thread/49458c16-e99e-4af9-8cd9-40299af66f8e]("http://social.answers.microsoft.com/Forums/en-US/w7network/thread/49458c16-e99e-4af9-8cd9-40299af66f8e")

---

### Post by killiekosmos on 2010-02-08
Solved - deleted Windows Lice ID login assistant!

---

