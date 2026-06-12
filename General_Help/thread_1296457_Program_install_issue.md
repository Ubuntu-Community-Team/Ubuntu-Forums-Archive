---
title: "Program install issue"
date: 2009-10-20
forum: General Help
---

### Post by highvoltage82 on 2009-10-20
I am trying to install a program and when I click install in the package installer, it tells me only one software manager is allowed to run at one time. It has been installing things just fine and this started. How do I turn the others off or what do I do? I am knew to this and learning the best I can, lol.

---

### Post by mikewhatever on 2009-10-20
Close all open windows and try again. You must have Synaptic and Add/Remove open at the same time and they can't be used together at once.

---

### Post by highvoltage82 on 2009-10-20
I have tried that. The package installer is the only thing open. I have also tried rebooting and still does the same thing when I try to install the program.

---

### Post by mikewhatever on 2009-10-20
Hm... Make sure nothing is open of other desktop spaces or autostarts at boot. Check your running processes with 'ps aux'.

---

### Post by highvoltage82 on 2009-10-21
Ok. Now I cant install anything from add/remove or from the package installer. Add/remove says "the dpkg was interrupted, you must manually run sudo-dpkg-configure a to correct the problem. Or when I use the package installer it tells me I have more than one software manager running and I am sure I dont. Like I said I am real new to this, so I really dont know what to do or how to use the terminal well. Any help would be great and I would be very thankful.

---

### Post by highvoltage82 on 2009-10-21
Anyone?

---

### Post by oldos2er on 2009-10-21
Copy and paste **sudo dpkg --configure -a** into a terminal.

---

### Post by KeLa on 2009-10-21
I had same problem and it was that "update manager" was running on background.

---

### Post by MilesTails on 2009-10-21
Have you tried the magic reboot? 

If that dosent solve the problem id open your system monitor and check it again for a background process related to aptitude or dpkg

oops i see that you have tried rebooting my mistake, id sitll try double checking youre running processes though

---

