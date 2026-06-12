---
title: "Root permission issues with Zenmap &amp; NMAP"
date: 2011-09-05
forum: General Help
---

### Post by Mick_EE on 2011-09-05
I can't remember how I set my userID up to run root temporarily for Wireshark and Zenmap (GUI for NMAP)
Anybody give me a reasonable secure solution?

THX

---

### Post by Mick_EE on 2011-09-05
Also - Interfaces not showing up in Wireshark. I had this problem before and it had to do with an update that allowed the NICs to be run in promiscuous mode? Any ideas... ?

---

### Post by haqking on 2011-09-05
> **Mick_EE said:**
> I can't remember how I set my userID up to run root temporarily for Wireshark and Zenmap (GUI for NMAP)
Anybody give me a reasonable secure solution?

THX

not sure i understand what you mean.

You can launch it from terminal using gksudo

---

### Post by Mick_EE on 2011-09-05
> **haqking said:**
> not sure i understand what you mean.

You can launch it from terminal using sudo

I want to use the GUI Zenmap as well for Wireshark. no problem launching CL from the terminal session.
THx

THe interfaces in Wireshark are not showing up as well. I had this happen before - it was an update to allow the NIC to run in Promiscuous mode. So, don't know as I have the latest 10.10 updates. THis shpould have included the root update to allow running as root?

---

### Post by haqking on 2011-09-05
> **Mick_EE said:**
> I want to use the GUI Zenmap as well for Wireshark. no problem launching CL from the terminal session.
THx

THe interfaces in Wireshark are not showing up as well. I had this happen before - it was an update to allow the NIC to run in Promiscuous mode. So, don't know as I have the latest 10.10 updates. THis shpould have included the root update to allow running as root?

yeah i understand that so *gksudo zenmap* and *gksudo wireshark* launches them as GUI.

---

### Post by Mick_EE on 2011-09-05
> **Mick_EE said:**
> I want to use the GUI Zenmap as well for Wireshark. no problem launching CL from the terminal session.
THx

THe interfaces in Wireshark are not showing up as well. I had this happen before - it was an update to allow the NIC to run in Promiscuous mode. So, don't know as I have the latest 10.10 updates. THis shpould have included the root update to allow running as root?

OK - today the terminal session worked as it should. Yesterday it was only starting the app in CL mode??
Strange!! THank you for prompting me to try again. Problem Solved?

THank you

---

### Post by haqking on 2011-09-05
> **Mick_EE said:**
> OK - today the terminal session worked as it should. Yesterday it was only starting the app in CL mode??
Strange!! THank you for prompting me to try again. Problem Solved?

THank you

ok cool.  Well make sure you use gksudo and not sudo to launch a gui.

glad you got it sorted.

mark the thread as solved using thread tools.

cheers

---

### Post by Dangertux on 2011-09-05
If you are trying to create a launcher that runs it as root without opening a terminal window the command for the launcher would be

```

gksudo zenmap %F

```

same thing for wireshark.

---

