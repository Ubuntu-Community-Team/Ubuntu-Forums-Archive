---
title: "How to install wine"
date: 2011-07-25
forum: General Help
---

### Post by Muhamad Nur Syuhada on 2011-07-25
Guys, I'm a new comer for Ubuntu OS. I have a question about how to install wine.
I've tried many times downloading wine and installing it, but still there's a comment in terminal:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What is exactly going on? would some one explain it to me please?
You can directly send me email at [email]shinisishiba@yahoo.com[/email].

Thx.

---

### Post by 2F4U on 2011-07-25
Can you explain how do you install wine? Did you forget to add sudo in front of the install command?

---

### Post by Elfy on 2011-07-25
> E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?You get this if you try to have more than one package management working.

Software centre/synaptic/apt-get in a terminal can only be done one at a time.

If you do only have one try rebooting.

---

### Post by Primefalcon on 2011-07-25
> **forestpiskie said:**
> You get this if you try to have more than one package management working.

Software centre/synaptic/apt-get in a terminal can only be done one at a time.

If you do only have one try rebooting.
Open your Ubuntu Software Center and search for wine in there

---

### Post by raja.genupula on 2011-07-25
man some times i am also getting that LOCK problem . but the only thing i did to solve that issue is restarting my system . ...the only reason i know is if you stopped any installation process in middle by ctrl+z , then you'll get that problem .so please wait for some time or restart your system .

---

### Post by dirghrabadia on 2011-07-25
> **forestpiskie said:**
> 
Software centre/synaptic/apt-get in a terminal can only be done one at a time.


Just curious, why it designed to act in a way as to allow one installation at at time?

---

### Post by raja.genupula on 2011-07-25
:lolflag:ha ha ha , honestly i too dont know man

---

### Post by nerdy_kid on 2011-07-25
rebooting Ubuntu is one way to fix that message.

---

