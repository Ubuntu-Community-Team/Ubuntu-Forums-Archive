---
title: "Help me to get Apache into startup"
date: 2010-03-03
forum: General Help
---

### Post by 13thSlayer on 2010-03-03
I want to get Apache to autostart on system boot. I compiled Apache from source, so it didn't install it's own script into /etc/init.d, so I have to write one. Can someone help me out here?

---

### Post by oj0kksn5 on 2010-03-03
> **13thSlayer said:**
> I want to get Apache to autostart on system boot. I compiled Apache from source, so it didn't install it's own script into /etc/init.d, so I have to write one. Can someone help me out here?

Why didnt you just ```
sudo apt-get install apache2
``` which would have just done all this for you

---

### Post by indytim on 2010-03-03
-OR-

> 
$sudo tasksel


Select the LAMP server and sit back and enjoy the bundled automatic installation...:D

-IndyTim

---

### Post by Tiler on 2010-03-17
> **sephedo said:**
> Why didnt you just ```
sudo apt-get install apache2
``` which would have just done all this for you

Even the auto-start?

---

### Post by lisati on 2010-03-17
Why not? I installed Apache as part of the installation of the server edition on my main desktop and it was added to auto-start automatically.

---

### Post by Konrad Ansehelm on 2010-10-03
You can use the standard apache init.d script for your custom compiled version. The init.d script checks which state the computer is in (if it is booting or halting) and starts/stops the apache daemon accordingly.

---

