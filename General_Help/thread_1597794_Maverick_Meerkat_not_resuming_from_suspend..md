---
title: "Maverick Meerkat not resuming from suspend."
date: 2010-10-15
forum: General Help
---

### Post by Mr. Rozell on 2010-10-15
I have an Acer Extensa 4420 laptop with Maverick Meerkat AMD 64 installed. When I suspend the laptop via closing the lid or from the Indicator Applet, it suspends after about a couple of minutes. When I resume my session and type in my password, the prompt box turns blank and nothing happens. The Cap Lock light works when I press the Cap Lock key. The fan runs as normal. The mouse works and the screen dims if left idle. I can drop to console via Ctrl+Alt+F1 and issue the command "sudo restart gdm" and when GDM restarts I can log in and keep working. However this does not happen when I have the laptop plugged in. I would appreciate any help you folks can give me.

---

### Post by Mr. Rozell on 2010-12-13
Bumb

---

### Post by MollyWop on 2010-12-13
> **Mr. Rozell said:**
> Bumb
Happens to me using the suspend key on my keyboard. I'm using an acer aspire 8630 desktop.

---

### Post by Sweet Mercury on 2010-12-15
I have the same issue.

I'm using Ubuntu Netbook Remix 10.10 on a Dell Inspirion Mini 1018.

I can resume from hibernation, but not the "suspend" state. It looks as though the computer wakes back up (light stops blinking, hard disk can be heard activating) but the screen stays off and I have to hard reboot the system.

---

### Post by gobbles414 on 2010-12-15
I have the same issue, with slightly different symptoms. I'm running Ubuntu 10.10 (32-bit) on a Dell Inspiron E1505. It "wakes" from suspend about 50% of the time. The other 50% of the time, when it doesn't wake, the Bluetooth indicator light illuminates and the system itself seems to turn on, but the screen stays dark and the WiFi indicator light doesn't illuminate.

---

### Post by Sweet Mercury on 2010-12-16
I should add, I've tried the uswsusp fix I've seen on the forums, but that didn't work either.

---

### Post by gobbles414 on 2010-12-23
This issue has not occurred on my Ubuntu 10.10 laptop in several days... Perhaps the folks at Ubuntu issued an update to fix the problem? Has the problem gone away in Ubuntu 10.04?

---

### Post by gobbles414 on 2011-01-06
This issue returned this morning! :-(  I installed updates earlier this week, so maybe one of them undid the fix?

---

### Post by Mr. Rozell on 2011-01-06
It's times like these when I pine for the stability of Debian. Unfortunately Lenny is too old and Squeeze is not stable. So for the time being I have downgraded back to Lucid Lynx because this issue does not occur.

---

### Post by gobbles414 on 2011-01-07
I have proposed updates enabled on my Ubuntu 10.10 laptop. It would be interesting to see how often the bug would have appeared had I not enabled proposed updates.

---

### Post by Rowan_ on 2011-02-01
Same problem as described as several others: after suspend I try to power back up but the screen remains unlit.  The PC must have the power cycled to start back up.  

I tried a fix from Maverick Meerkat Release Notes, but to no avail.  Apparently it works for some. 
A detailed description of the fix can be found at 
[jr0cket.blogspot.com/2010/10/ubuntu-1010-hibernate-suspend-bug-fix.html]("jr0cket.blogspot.com/2010/10/ubuntu-1010-hibernate-suspend-bug-fix.html")

Acer Aspire one Netbook
Amd dual core c50 (1GHz)
memory: 1GB DDR3

---

### Post by Mr. Rozell on 2011-02-01
Thanks for the suggestion Rowan_, unfortunately that didn't work. Isn't it curious that for as long as Meerkat has been out, the solution continues to be elusive.

---

