---
title: "Connecting To The Internet"
date: 2010-09-16
forum: General Help
---

### Post by Father Of Many on 2010-09-16
I just got my computer online with Ubuntu 9.04, i am able to connect to the internet but only in what seems like a round about way.
To connect i have to click System > Preferences > Network Connection > DSL > Highlight DSLEXTREME > Edit > Uncheck "Connect Automatically > Apply > Edit > Check "Connect Automatically" > Apply > Close.
What am i doing wrong? Is there an easier way to connect or set it up to connect automatically when the computer is restarted.
Normally i wouldn't restart the computer unless it's necessary, but the baby finds it amusing to turn the computer off.

---

### Post by ubunterooster on 2010-09-16
Go to system>preferences>startup applications. Is network manager listed as an auto starting program?

---

### Post by Father Of Many on 2010-09-16
How do i know if it is?

---

### Post by efflandt on 2010-09-16
Do you have **Available to all users** checked?  If that and **Connect automatically** are checked I believe it should try to connect automatically for any network activity even before you log into the computer (or if you boot to text console).  Although, I have not done PPPoE from Ubuntu, just wired, wireless, and mobile data (my DSL modem/router handles PPPoE login and is set to remain connected).

---

### Post by Father Of Many on 2010-09-16
Excellent, it connected as soon as it restarted.
Thanks for the help efflandt and ubunterooster. Ubuntu just keeps getting easier to work with.

---

### Post by ubunterooster on 2010-09-16
You are welcome.

---

